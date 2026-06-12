---
title: "Aparença Ubuntu 10.10"
date: 2011-01-02
forum: Catalan Team
---

### Post by negu on 2011-01-02
Hola, m'he decidit a actualitzar l'ubuntu al 10.10 i la veritat és que ha anat molt bé el que m'ha succeït és que intentant canviar l'aparença l'hi he posat la d'un mac, amb aquestes ordres:
tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp

cd /tmp/Macbuntu-10.10/

./install.shel fet és que ho voldría desfer per tornar a l'aparença de l'ubuntu i no se com fer-ho.

moltes gràcies

---

### Post by wgarcia on 2011-01-02
Has d'anar al menú Sistema -> Preferències -> Aparença i escollir el tema que vulguis, per exemple "Ambiance" és el que ve amb Ubuntu per defecte des de la versió 10.04.

---

### Post by negu on 2011-01-03
Gràcies wgarcia, però el "problema" que tinc és que l'aparença és com la d'un Mac no tinc visibles les entrades a sistema, llocs i aplicacions així com el botó d'apagada i clar m'agradaría recuperar l'aparença original de l'ubuntu.
per això la meva idea era desfer l'acció d'aparença de MAC.

gràcies un altre cop

---

### Post by kimet on 2011-01-03
Hauries de tornat a descarregar aquest fitxer Macbuntu-10.10.tar.gz i descomprimir-lo per veure que t'ha instal.lat i desinstalar-ho manualment, o veure si te algún script de desinstal.lació.

---

### Post by negu on 2011-01-03
Hola kimet ja m'he baixat el paquet i si que té una carpeta per a desinstalar-lo, però no se com fer-ho manualment.

a l'arxiu per a desinstalarlo, hem surt això:

#!/bin/bash

# Macbuntu - Mac OS X Transformation Pack
# Author: lookout, elmigueluno
# Send feedback to [email]lookout@losoft.org[/email], [email]elmigueluno@gmail.com[/email]
# Homepage: [http://www.losoft.org/macbuntu/](http://www.losoft.org/macbuntu/)
# 
# Copyright (c) 2010 Jan Komadowski
# 
# This program is free software. Feel free to redistribute and/or
# modify it under the terms of the GNU General Public License v3
# as published by the Free Software Foundation.
# This program is distributed in the hope that it will be useful
# but comes WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
# 
# See the GNU General Public License for more details.

UBUVER="10.10"
UBUNTU="Ubuntu $UBUVER"

MACBUNTU="Macbuntu-$UBUVER"
VERSION="2.3"

MACBUNTUHOME="$HOME/.macbuntu"

CURRENT="$MACBUNTUHOME/$UBUVER-$VERSION"
BACKUP="$MACBUNTUHOME/backup"
BACKUPDIR="$BACKUP/$(date +%Y-%m-%d-%H:%M)"
BACKUPCURRENT="$BACKUP/current"

DOCKYPID=$(ps -o pid= -C docky)
COMPIZPID=$(ps -o pid= -C compiz)

RESOLUTION=$(xdpyinfo | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
VRES=$(echo $RESOLUTION | sed 's/.*x//')
HRES=$(echo $RESOLUTION | sed 's/x.*//')

ARCH=$(uname -m)
ARCHDIR=`[ "$ARCH" == "x86_64" ] && echo "x64" || echo "x32"`

force=$1
tester=0

chk_user()
{
    echo ""
    echo "Checkin script user..."
    if [ $(whoami) = "root" ]
    then
        echo "Failed."
        echo "Root user not allowed, please run this script as a regular user."
        echo "Exiting..."
        exit 1;
    fi
    echo "Passed"
}

chk_root()
{
    echo ""
    echo "Checkin for a root access..."
    s=`sudo cat /etc/issue`
    if [ -n "$s" ]; then
        return
    fi
    echo "Authorization failed."
    echo "Exiting..."
    exit 1;
}

chk_system()
{
    echo ""
    echo "Checking Ubuntu version..."
    s=`cat /etc/issue | grep -i "$UBUNTU"`
    if [ ! -n "$s" ]; then
        echo "Failed. System not supported, script will end here"
        echo "To ignore their compatibility with current OS try ./uninstall.sh force"
        echo "Exiting..."
        exit 1;
    fi
    echo "Passed"
}

chk_program()
{
    s=`dpkg --status $1 | grep -q not-installed`
    if [ ! -n "$s" ]; then
        return 1
    fi
    return 0
}

chk_version()
{
    echo ""
    echo "Checking currently installed version of $MACBUNTU..."
    d=$MACBUNTUHOME/current
    if [ -f "$d" ]; then
        s=`cat $MACBUNTUHOME/current | grep "$UBUVER-$VERSION"`
        if [ ! -n "$s" ]; then
            echo "Failed. Currently installed version is not compatible with this uninstall"
            echo "Exiting..."
            exit 1;
        fi
    else
        echo "Failed. The script is not able to determine what version is currently installed"
        echo "Exiting..."
        exit 1;
    fi
}

# Changing current to script dir
cd -- "$(dirname -- "$0")"

echo ""
echo "Macbuntu - Mac OS X Transformation Pack"
echo ""
echo "Deinstallation script"
echo ""
echo "Attention!"
echo "This script will slide back to default Ubuntu desktop"
echo "all $MACBUNTU components will be removed permanently"

case "$force" in
    --force|force) ;;
    *) chk_system ;;
esac

chk_version
chk_user

echo ""
echo "This script will completely remove $MACBUNTU and slide back to default Ubuntu desktop now"
echo "You must have root privileges to be able to uninstall all this components."
echo ""
echo "Attention!"
echo "Running scripts with root privileges is dangerous, if you do not trust the software"
echo "or you are unsure about the origin of this software, please abort (Control+C)."
echo "Macbuntu guarantee the safe code only if the application comes from this address"
echo "https://sourceforge.net/projects/macbuntu/"
echo ""
echo "Do you want to continue [Y/n]?"
read ans
case "$ans" in
    n*|N*)
    echo "Installation aborted. Exiting..."
    exit 0;
esac

chk_root

if [ $tester == 0 ] ; then

echo "Uninstalling Macbuntu..."
rm -rf ~/.icons/$MACBUNTU-Cursors/
rm -rf ~/.icons/Macbuntu-Cursors/
sudo rm -rf /usr/share/icons/$MACBUNTU-Cursors/
sudo rm -rf /usr/share/icons/Macbuntu-Cursors/
rm -rf ~/.icons/$MACBUNTU-Icons/
rm -rf ~/.icons/Macbuntu-Icons/
sudo rm -rf /usr/share/icons/$MACBUNTU-Icons/
sudo rm -rf /usr/share/icons/Macbuntu-Icons/
sudo rm -f /usr/share/icons/applelogo.png
sudo rm -f /usr/share/icons/applelogo.tif
sudo rm -f /usr/share/icons/applelogo-black.svg
sudo rm -f /usr/share/icons/LoginIcons/apps/64/applelogo.png
sudo rm -f /usr/share/icons/LoginIcons/apps/64/applelogo.tif
sudo rm -f /usr/share/icons/LoginIcons/apps/64/applelogo-black.svg
rm -rf ~/.themes/$MACBUNTU/
rm -rf ~/.themes/Macbuntu/
sudo rm -rf /usr/share/themes/$MACBUNTU/
sudo rm -rf /usr/share/themes/Macbuntu/
rm -f ~/.fonts.conf
sudo rm -rf /usr/share/fonts/mac/ && sudo fc-cache -f -v

killall docky

echo ""
echo "Uninstalling Application Menu, Docky, Ubuntu-Tweak..."
sudo apt-get autoremove docky ubuntu-tweak appmenu-gtk indicator-applet-appmenu indicator-appmenu

# Disable Compiz
if [ ! -z $COMPIZPID ]; then
    nohup metacity --replace > /dev/null &
fi

echo ""
echo "Unsetting..."
gconftool-2 --recursive-unset /apps/docky-2
gconftool-2 --recursive-unset /apps/panel
gconftool-2 --recursive-unset /apps/compiz

# Reloading Gnome Panel
killall gnome-panel

echo "Setting up Compiz Fusion..."
# Animation
sudo cp -f compiz/$ARCHDIR/original/libanimation.so /usr/lib/compiz/
sudo cp -f compiz/$ARCHDIR/original/animation.xml /usr/share/compiz/

echo "Setting up theme..."
# Metacity
gconftool-2 --set /apps/gwd/metacity_theme_opacity --type float 1
# Backgrounds
gconftool-2 --set /desktop/gnome/background/picture_filename --type string "/usr/share/backgrounds/warty-final-ubuntu.png"
# Gtk Theme
gconftool-2 --set /desktop/gnome/interface/gtk_theme --type string "Ambiance"
gconftool-2 --set /apps/metacity/general/theme --type string "Ambiance"
gconftool-2 --set /desktop/gnome/interface/icon_theme --type string "ubuntu-mono-dark"
# Cursor
gconftool-2 --set /desktop/gnome/peripherals/mouse/cursor_theme --type string "DMZ-White"
gconftool-2 --set /desktop/gnome/peripherals/mouse/cursor_size --type int 24
# Button layout
gconftool-2 --set /apps/metacity/general/button_layout --type string "close,minimize,maximize:"
# Icons
gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "icons"
gconftool-2 --set /desktop/gnome/interface/buttons_have_icons --type boolean false
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type boolean false
# Nautilus
gconftool-2 --set /apps/nautilus/preferences/default_folder_viewer --type string "icon_view"
gconftool-2 --set /apps/nautilus/preferences/side_pane_view --type string "NautilusPlacesSidebar"
gconftool-2 --set /apps/nautilus/preferences/sort_directories_first --type boolean true
gconftool-2 --set /apps/nautilus/preferences/start_with_location_bar --type boolean true
gconftool-2 --set /apps/nautilus/preferences/always_use_location_entry --type boolean false
gconftool-2 --set /apps/nautilus/preferences/start_with_sidebar --type boolean true
gconftool-2 --set /apps/nautilus/preferences/start_with_status_bar --type boolean true
gconftool-2 --set /apps/nautilus/preferences/start_with_toolbar --type boolean true
# Compositing manager
gconftool-2 --set /apps/metacity/general/compositing_manager --type boolean true
# Fonts
gconftool-2 --set /desktop/gnome/interface/font_name --type string "Sans 10"
gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 10"
gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 10"
gconftool-2 --set /apps/metacity/general/titlebar_font --type string "Sans Bold 10"
gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 10" 
# Terminal
gconftool-2 --set /apps/gnome-terminal/global/use_menu_accelerators --type boolean true
gconftool-2 --set /apps/gnome-terminal/profiles/Default/scrollback_unlimited --type boolean true
gconftool-2 --set /apps/gnome-terminal/profiles/Default/use_theme_background --type boolean true
gconftool-2 --set /apps/gnome-terminal/profiles/Default/use_theme_colors --type boolean true

echo "Setting up login screen..."
# Login screen
# Backgrounds
sudo -u gdm gconftool-2 --set /desktop/gnome/background/picture_filename --type string "/usr/share/backgrounds/warty-final-ubuntu.png"
# Gtk Theme
sudo -u gdm gconftool-2 --set /desktop/gnome/interface/icon_theme --type string "LoginIcons"
sudo -u gdm gconftool-2 --set /desktop/gnome/interface/gtk_theme --type string "Ambiance"
sudo -u gdm gconftool-2 --set /apps/metacity/general/theme --type string "Ambiance"
# Cursor
sudo -u gdm gconftool-2 --set /desktop/gnome/peripherals/mouse/cursor_size --type int 24
sudo -u gdm gconftool-2 --set /desktop/gnome/peripherals/mouse/cursor_theme --type string "DMZ-White"
# Logo
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/logo_icon_name --type string "computer"
sudo rm -rf /usr/share/icons/LoginIcons/icon-theme.cache
# Fonts
sudo -u gdm gconftool-2 --set /desktop/gnome/interface/font_name --type string "Sans 10"
sudo -u gdm gconftool-2 --set /apps/nautilus/preferences/desktop_font --type string "Sans 10"

echo "Setting up Plymouth theme..."
sudo rm -rf /lib/plymouth/themes/Paw-Ubuntu/
sudo rm -rf /lib/plymouth/themes/Paw-OSX/
sudo update-alternatives --set default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
sudo update-initramfs -u

echo "Setting up repository"
sudo remove-apt-repository tualatrix/ppa
sudo remove-apt-repository globalmenu-team/ppa
sudo rm -f /usr/bin/remove-apt-repository
sudo apt-get update

# Reloading Compiz
if [ ! -z $COMPIZPID ]; then
    nohup compiz --replace >/dev/null &
fi

echo "Finishing installation..."
rm -rf $CURRENT/
rm -rf $BACKUPCURRENT/
rm -f $MACBUNTUHOME/current
sleep 3

echo ""
echo "$MACBUNTU deinstallation complete!"
echo "Bye"

else # Tester

echo "Tester..."

fi # End Tester


moltes gràcies per la paciència

---

### Post by kimet on 2011-01-03
De la mateixa manera que el vas instal.lar, des de un terminal et situes a la carpeta on l'has descomprimit. P.ex.
```
cd /home/xxxx/xxxx/Macbuntu-10.10/
```
I executes l'script:
```
./uninstall.sh
```
Suposant que es digui així.
A mes, es possible que hi hagin algún fitxer "readme" amb instruccions  d'insta/desinstalació al paquet.
 
Salut.

---

### Post by wgarcia on 2011-01-03
Em sembla que el menú Sistema -> Preferències, s'accedeix amb una icona que hi ha a la "barra plafó" horizontal que surt a baix de la pantalla quan passes el ratolí per sobre. Possiblement la icona és el símbol d'Ubuntu, el mateix que al tema per defecte d'Ubuntu surt al panell superior a l'extrem esquerre.

Per cert, quan hagis d'enganxar tanta informació millor fer-lo en un arxiu adjunt.

---

### Post by negu on 2011-01-03
Gràcies Kimet m'ha anat perfecte aquesta resposta, tindré en compte lo d'afegir l'arxiu wgarcia.
un altre cosa que m'ha succeit es que m'ha desaparegut la barra inferior de l'escriptori on surt la paparera i els diferents escriptoris, se que potser son consultes absurdes però soc nou i costa una mica tot plegat.

Gràcies

---

### Post by wgarcia on 2011-01-05
Cliques al panell superior, i esculls "Quadre nou". T'apareixerà el panell inferior, i aquí cliques amb el botó dret i "Afegeix al quadre", et sortirà una llista i busca "Paperera". També potser vos afegir "Llista de finestres" que és el que surt per defecte per canviar entre apolicacions obertes al quadre inferior.

---

