# Installeer op Fedora Linux

Er zijn QOwnNotes-repositories voor **Fedora 28 and higher**.

## A config-manager dnf beépülő modullal rendelkező rendszereken

Futtassa a következő shell parancsokat rootként a lerakat hozzáadásához.

```bash
dnf config-manager --add-repo http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Fedora_\$releasever/

dnf makecache
dnf install qownotes
```

::: tip
Előfordulhat, hogy el kell fogadnia a repo kulcsot, mielőtt letölthetné róla.
:::

## Régi telepítési módszer

Használja ezt a módszert, ha a Fedora verziója nem támogatja a ` config-manager ` dnf bővítményt, futtassa ezeket a parancsokat rootként.

Voer de volgende shell-opdrachten uit als root om de repository te vertrouwen.

```bash
rpm --import http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Fedora_34/repodata/repomd.xml.key
```

Voer de volgende shell-opdrachten uit als root om de repository toe te voegen en vanaf daar QOwnNotes te installeren.

```bash
cat > /etc/yum.repos.d/QOwnNotes.repo << EOL
[qownnotes]
name=OBS repo for QOwnNotes (Fedora \$releasever - \$basearch)
type=rpm-md
baseurl=http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Fedora_\$releasever/
gpgcheck=1
gpgkey=http://download.opensuse.org/repositories/home:/pbek:/QOwnNotes/Fedora_\$releasever/repodata/repomd.xml.key
enabled=1
EOL

dnf clean expire-cache
dnf install qownnotes
```

[Directe download](https://build.opensuse.org/package/binaries/home:pbek:QOwnNotes/desktop/Fedora_34) (deze voorbeeldlink is voor Fedora 34)
