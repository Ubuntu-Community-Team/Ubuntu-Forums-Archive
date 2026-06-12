---
title: "Issue migrating GNOME app to MATE (i.e. shell scripts)"
date: 2012-10-18
forum: Any Other OS
---

### Post by Giant Speck on 2012-10-18
DockbarX 0.90 was released a few days ago, and I'm attempting to install it on Linux Mint 13 (the MATE version), but in order to do so, I have to manually "migrate" it over to MATE since MATE uses differently-named core applications to avoid problems with GNOME (since it's a GNOME 2 fork).  I'm running into some issues.

I downloaded the source from DockbarX's Launchpad site, and followed **[these instructions]("http://airinux.blogspot.com/2012/07/howto-make-dockbarx-for-mate.html")** to migrate the application from GNOME to MATE.  The migration script used in the instructions is as follows:

```
    #!/bin/bash
    # Copyright © 2011 Perberos
    #
    # This program is free software; you can redistribute it and/or modify it
    # under the terms of the GNU General Public License as published by the
    # Free Software Foundation; either version 3 of the License, or (at your
    # option) any later version.
    #
    # This program is distributed in the hope that it will be useful, but
    # WITHOUT ANY WARRANTY; without even the implied warranty of
    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
    # General Public License for more details.
    #
    # You should have received a copy of the GNU General Public License along
    # with this program; if not, write to the Free Software Foundation, Inc.,
    # 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
    # either provide a command line option otherwise src folder will be considered.
    if [ $# -gt 0 ]
    then    
      pkgdir=$1 # the folder where is the code, be carefull
    else
      pkgdir=src
    fi
    #support for space in filename
    IFS=$'\n' 
     
    replaces=(
     
        'ior-decode-2' 'matecorba-ior-decode-2'
        'linc-cleanup-sockets' 'matecorba-linc-cleanup-sockets' 
        'typelib-dump' 'matecorba-typelib-dump'
        'libname-server-2' 'libname-matecorba-server-2'
     
        'panel-applet' 'mate-panel-applet'
        'panelapplet' 'matepanelapplet'
        'panel_applet' 'mate_panel_applet'
        'PANEL_APPLET' 'MATE_PANEL_APPLET'
        'PanelApplet' 'MatePanelApplet'
     
        'mate-mate-panel-applet' 'mate-panel-applet'
        'matematepanelapplet' 'matepanelapplet'
        'mate_mate_panel_applet' 'mate_panel_applet'
        'MATE_MATE_PANEL_APPLET' 'MATE_PANEL_APPLET'
        'MateMatePanelApplet' 'MatePanelApplet'
     
        'gnome' 'mate'
        'GNOME' 'MATE'
        'Gnome' 'Mate'
     
        'Metacity' 'Marco'
        'metacity' 'marco'
        'METACITY' 'MARCO'
     
        'Nautilus' 'Caja'
        'nautilus' 'caja'
        'NAUTILUS' 'CAJA'
     
        'Zenity' 'MateDialog'
        'zenity' 'matedialog'
        'ZENITY' 'MATEDIALOG'
     
        'MATE|Utilities' 'GNOME|Utilities'
        'MATE|Desktop' 'GNOME|Desktop'
        'MATE|Applets' 'GNOME|Applets'
        'MATE|Applications' 'GNOME|Applications'
        'MATE|Multimedia' 'GNOME|Multimedia'
     
        'libnotify' 'libmatenotify'
        'LIBNOTIFY' 'LIBMATENOTIFY'
        'Libnotify' 'Libmatenotify'
     
        'bonobo' 'matecomponent'
        'Bonobo' 'MateComponent'
        'BONOBO' 'MATECOMPONENT'
        'bonoboui' 'matecomponentui'
        'BONOBOUI' 'MATECOMPONENTUI'
     
        'gconf' 'mateconf'
        'GConf' 'MateConf'
        'GCONF' 'MATECONF'
     
        'pkmateconfig' 'pkgconfig'
        'PKMATECONFIG' 'PKGCONFIG'
     
        'gweather' 'mateweather'
        'GWeather' 'MateWeather'
        'GWEATHER' 'MATEWEATHER'
     
        'ORBit' 'MateCORBA'
        'orbit' 'matecorba'
        'ORBIT' 'MATECORBA'
     
        'panel-applet' 'mate-panel-applet'
        'panelapplet' 'matepanelapplet'
        'panel_applet' 'mate_panel_applet'
        'PANEL_APPLET' 'MATE_PANEL_APPLET'
        'PanelApplet' 'MatePanelApplet'
     
        # mistakes
        'mate-mate-panel-applet' 'mate-panel-applet'
        'matematepanelapplet' 'matepanelapplet'
        'mate_mate_panel_applet' 'mate_panel_applet'
        'MATE_MATE_PANEL_APPLET' 'MATE_PANEL_APPLET'
        'MateMatePanelApplet' 'MatePanelApplet'
     
        'soup-mate' 'soup-gnome'
        'SOUP_TYPE_MATE_FEATURES_2_26' 'SOUP_TYPE_GNOME_FEATURES_2_26'
        'mateconfaudiosink' 'gconfaudiosink'
        'mateconfvideosink' 'gconfvideosink'
     
        'TAMATECONFIG' 'TAGCONFIG'
     
        # GNOME Keyboard
        'gkbd' 'matekbd'
        'Gkbd' 'Matekbd'
        'GKBD' 'MATEKBD'
     
     
        # GMenu
        'GMenu' 'MateMenu'
        'gmenu' 'matemenu'
        'GMENU' 'MATEMENU'
     
        # polkit
        'polkitgtk' 'polkitgtkmate'
        'polkit-gtk' 'polkit-gtk-mate'
        'PolkitGtk' 'PolkitGtkMate'
        'POLKITGTK' 'POLKITGTKMATE'
        'POLKIT_GTK' 'POLKIT_GTK_MATE'
        'polkit_gtk' 'polkit_gtk_mate'
     
        'polkit_gtk_mate_mate' 'polkit_gtk_mate'
        'polkitgtkmatemate' 'polkitgtkmate'
        'PolkitGtkMateMate' 'PolkitGtkMate'
        'POLKITGTKMATEMATE' 'POLKITGTKMATE'
        'POLKIT_GTK_MATE_MATE' 'POLKIT_GTK_MATE'
        'polkit-gtk-mate-mate' 'polkit-gtk-mate'
     
        # GDM
        'gdm' 'mdm'
        'Gdm' 'Mdm'
        'GDM' 'MDM'
     
     
        # Glib Deprecated
        'G_CONST_RETURN' 'const'
     
        # Eye of GNOME
        'eog' 'eom' # only on the exe generated name
     
        # gedit
        'gedit' 'pluma'
        'GEDIT' 'PLUMA'
        'Gedit' 'Pluma'
     
     
        # evince
        'EVINCE' 'ATRIL'
        'evince' 'atril'
        'Evince' 'Atril'
    )
     
    #
    # rename files and folders
    #
    dirs=$(find "$pkgdir/" -type d | sed "s|^${pkgdir}/||")
    # for revert the order of folders, so the rename is safe
    revertdirs=
     
    for dirsname in ${dirs}; do
        revertdirs="$dirsname $revertdirs"
    done
     
    # directory mv
    for dirsname in ${revertdirs}; do
        oldname=`basename $dirsname`
        newname=$oldname
     
        for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
            newname=${newname/${replaces[$index]}/${replaces[$index + 1]}}
        done
     
        if [ $oldname != $newname ]; then
            echo "renaming folder $oldname to $newname"
     
            path=`dirname "$pkgdir/$dirsname"`
     
            retval=`mv "$path/$oldname" "$path/$newname"`
        fi
    done
     
    #
    # rename files
    #
    files=$(find "$pkgdir/" -type f | sed "s|^${pkgdir}/||")
    # files mv
    for filename in ${files}; do
        oldname=`basename $filename`
        newname=$oldname
     
        for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
            newname=${newname/${replaces[$index]}/${replaces[$index + 1]}}
        done
     
        if [ $oldname != $newname ]; then
            echo "renaming file $oldname to $newname"
     
            path=`dirname "$pkgdir/$filename"`
     
            retval=`mv "$path/$oldname" "$path/$newname"`
        fi
    done
     
    #
    # rename file contents
    #
    files=$(find "$pkgdir/" -type f | sed "s|^${pkgdir}/||")
     
    for filename in ${files}; do
        datacontent=`cat "$pkgdir/$filename"`
        datacontentold=$datacontent
        for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
            #sed -i "s/${replaces[$index]}/${replaces[$index + 1]}/g" "$pkgdir/$filename"
            datacontent=${datacontent//${replaces[$index]}/${replaces[$index + 1]}}
        done
     
        if [ "$datacontentold" != "$datacontent" ]; then
            echo "saving $filename"
            echo "$datacontent" > "$pkgdir/$filename"
        fi
    done


```The instructions state that you need to change "pkgdir=src" to "pkgdir=" and then drop the script into the DockbarX folder and execute it.  However, when I do all of this, the script attempts to modify files outside the folder and not the files within the folder, as evidenced by the following lines my terminal spat back at me when I tried to execute the script:

```
    find: `/proc/1036/task/1036/fd': Permission denied
    find: `/proc/1036/task/1036/fdinfo': Permission denied
    find: `/proc/1036/task/1036/ns': Permission denied
    find: `/proc/1036/fd': Permission denied
    find: `/proc/1036/fdinfo': Permission denied
    find: `/proc/1036/ns': Permission denied
    find: `/proc/1040/task/1040/fd': Permission denied
    find: `/proc/1040/task/1040/fdinfo': Permission denied
    find: `/proc/1040/task/1040/ns': Permission denied
    find: `/proc/1040/fd': Permission denied
    find: `/proc/1040/fdinfo': Permission denied
    find: `/proc/1040/ns': Permission denied
    find: `/proc/1041/task/1041/fd': Permission denied
    find: `/proc/1041/task/1041/fdinfo': Permission denied
    find: `/proc/1041/task/1041/ns': Permission denied
    find: `/proc/1041/fd': Permission denied
    find: `/proc/1041/fdinfo': Permission denied
    find: `/proc/1041/ns': Permission denied
    find: `/proc/1045/task/1045/fd': Permission denied
    find: `/proc/1045/task/1045/fdinfo': Permission denied
    find: `/proc/1045/task/1045/ns': Permission denied
    find: `/proc/1045/task/1050/fd': Permission denied
    find: `/proc/1045/task/1050/fdinfo': Permission denied
    find: `/proc/1045/task/1050/ns': Permission denied
    find: `/proc/1045/task/1674/fd': Permission denied
    find: `/proc/1045/task/1674/fdinfo': Permission denied
    find: `/proc/1045/task/1674/ns': Permission denied
    find: `/proc/1045/fd': Permission denied
    find: `/proc/1045/fdinfo': Permission denied
    find: `/proc/1045/ns': Permission denied
    find: `/proc/1046/task/1046/fd': Permission denied
    find: `/proc/1046/task/1046/fdinfo': Permission denied
    find: `/proc/1046/task/1046/ns': Permission denied
    find: `/proc/1046/task/1049/fd': Permission denied
    find: `/proc/1046/task/1049/fdinfo': Permission denied
    find: `/proc/1046/task/1049/ns': Permission denied
    find: `/proc/1046/fd': Permission denied
    find: `/proc/1046/fdinfo': Permission denied
    find: `/proc/1046/ns': Permission denied
    find: `/proc/1059/task/1059/fd': Permission denied
    find: `/proc/1059/task/1059/fdinfo': Permission denied
    find: `/proc/1059/task/1059/ns': Permission denied
    find: `/proc/1059/fd': Permission denied
    find: `/proc/1059/fdinfo': Permission denied
    find: `/proc/1059/ns': Permission denied
    find: `/proc/1280/task/1280/fd': Permission denied
    find: `/proc/1280/task/1280/fdinfo': Permission denied
    find: `/proc/1280/task/1280/ns': Permission denied
    find: `/proc/1280/fd': Permission denied
    find: `/proc/1280/fdinfo': Permission denied
    find: `/proc/1280/ns': Permission denied
    find: `/proc/1289/task/1289/fd': Permission denied
    find: `/proc/1289/task/1289/fdinfo': Permission denied
    find: `/proc/1289/task/1289/ns': Permission denied
    find: `/proc/1289/fd': Permission denied
    find: `/proc/1289/fdinfo': Permission denied
    find: `/proc/1289/ns': Permission denied
    find: `/proc/1304/task/1304/fd': Permission denied
    find: `/proc/1304/task/1304/fdinfo': Permission denied
    find: `/proc/1304/task/1304/ns': Permission denied
    find: `/proc/1304/fd': Permission denied
    find: `/proc/1304/fdinfo': Permission denied
    find: `/proc/1304/ns': Permission denied
    find: `/proc/1305/task/1305/fd': Permission denied
    find: `/proc/1305/task/1305/fdinfo': Permission denied
    find: `/proc/1305/task/1305/ns': Permission denied
    find: `/proc/1305/fd': Permission denied
    find: `/proc/1305/fdinfo': Permission denied
    find: `/proc/1305/ns': Permission denied
    find: `/proc/1307/task/1307/fd': Permission denied
    find: `/proc/1307/task/1307/fdinfo': Permission denied
    find: `/proc/1307/task/1307/ns': Permission denied
    find: `/proc/1307/fd': Permission denied
    find: `/proc/1307/fdinfo': Permission denied
    find: `/proc/1307/ns': Permission denied
    find: `/proc/1337/task/1337/fd': Permission denied
    find: `/proc/1337/task/1337/fdinfo': Permission denied
    find: `/proc/1337/task/1337/ns': Permission denied
    find: `/proc/1337/task/1340/fd': Permission denied
    find: `/proc/1337/task/1340/fdinfo': Permission denied
    find: `/proc/1337/task/1340/ns': Permission denied
    find: `/proc/1337/fd': Permission denied
    find: `/proc/1337/fdinfo': Permission denied
    find: `/proc/1337/ns': Permission denied
    find: `/proc/1339/task/1339/fd': Permission denied
    find: `/proc/1339/task/1339/fdinfo': Permission denied
    find: `/proc/1339/task/1339/ns': Permission denied
    find: `/proc/1339/fd': Permission denied
    find: `/proc/1339/fdinfo': Permission denied
    find: `/proc/1339/ns': Permission denied
    find: `/proc/1346/task/1346/fd': Permission denied
    find: `/proc/1346/task/1346/fdinfo': Permission denied
    find: `/proc/1346/task/1346/ns': Permission denied
    find: `/proc/1346/fd': Permission denied
    find: `/proc/1346/fdinfo': Permission denied
    find: `/proc/1346/ns': Permission denied
    find: `/proc/1347/task/1347/fd': Permission denied
    find: `/proc/1347/task/1347/fdinfo': Permission denied
    find: `/proc/1347/task/1347/ns': Permission denied
    find: `/proc/1347/fd': Permission denied
    find: `/proc/1347/fdinfo': Permission denied
    find: `/proc/1347/ns': Permission denied
    find: `/proc/1350/task/1350/fd': Permission denied
    find: `/proc/1350/task/1350/fdinfo': Permission denied
    find: `/proc/1350/task/1350/ns': Permission denied
    find: `/proc/1350/fd': Permission denied
    find: `/proc/1350/fdinfo': Permission denied
    find: `/proc/1350/ns': Permission denied
    find: `/proc/1431/task/1431/fd': Permission denied
    find: `/proc/1431/task/1431/fdinfo': Permission denied
    find: `/proc/1431/task/1431/ns': Permission denied
    find: `/proc/1431/fd': Permission denied
    find: `/proc/1431/fdinfo': Permission denied
    find: `/proc/1431/ns': Permission denied
    find: `/proc/1471/task/1471/fd': Permission denied
    find: `/proc/1471/task/1471/fdinfo': Permission denied
    find: `/proc/1471/task/1471/ns': Permission denied
    find: `/proc/1471/fd': Permission denied
    find: `/proc/1471/fdinfo': Permission denied
    find: `/proc/1471/ns': Permission denied
    find: `/proc/1473/task/1473/fd': Permission denied
    find: `/proc/1473/task/1473/fdinfo': Permission denied
    find: `/proc/1473/task/1473/ns': Permission denied
    find: `/proc/1473/fd': Permission denied
    find: `/proc/1473/fdinfo': Permission denied
    find: `/proc/1473/ns': Permission denied
    find: `/proc/1488/task/1488/fd': Permission denied
    find: `/proc/1488/task/1488/fdinfo': Permission denied
    find: `/proc/1488/task/1488/ns': Permission denied
    find: `/proc/1488/fd': Permission denied
    find: `/proc/1488/fdinfo': Permission denied
    find: `/proc/1488/ns': Permission denied
    find: `/proc/1672/task/1672/fd': Permission denied
    find: `/proc/1672/task/1672/fdinfo': Permission denied
    find: `/proc/1672/task/1672/ns': Permission denied
    find: `/proc/1672/fd': Permission denied
    find: `/proc/1672/fdinfo': Permission denied
    find: `/proc/1672/ns': Permission denied
    find: `/proc/1708/task/1708/fd': Permission denied
    find: `/proc/1708/task/1708/fdinfo': Permission denied
    find: `/proc/1708/task/1708/ns': Permission denied
    find: `/proc/1708/fd': Permission denied
    find: `/proc/1708/fdinfo': Permission denied
    find: `/proc/1708/ns': Permission denied
    find: `/proc/1712/task/1712/fd': Permission denied
    find: `/proc/1712/task/1712/fdinfo': Permission denied
    find: `/proc/1712/task/1712/ns': Permission denied
    find: `/proc/1712/fd': Permission denied
    find: `/proc/1712/fdinfo': Permission denied
    find: `/proc/1712/ns': Permission denied
    find: `/proc/1770/task/1770/fd': Permission denied
    find: `/proc/1770/task/1770/fdinfo': Permission denied
    find: `/proc/1770/task/1770/ns': Permission denied
    find: `/proc/1770/fd': Permission denied
    find: `/proc/1770/fdinfo': Permission denied
    find: `/proc/1770/ns': Permission denied
    find: `/proc/1786/task/1786/fd': Permission denied
    find: `/proc/1786/task/1786/fdinfo': Permission denied
    find: `/proc/1786/task/1786/ns': Permission denied
    find: `/proc/1786/task/1787/fd': Permission denied
    find: `/proc/1786/task/1787/fdinfo': Permission denied
    find: `/proc/1786/task/1787/ns': Permission denied
    find: `/proc/1786/task/1788/fd': Permission denied
    find: `/proc/1786/task/1788/fdinfo': Permission denied
    find: `/proc/1786/task/1788/ns': Permission denied
    find: `/proc/1786/task/1789/fd': Permission denied
    find: `/proc/1786/task/1789/fdinfo': Permission denied
    find: `/proc/1786/task/1789/ns': Permission denied
    find: `/proc/1786/task/1790/fd': Permission denied
    find: `/proc/1786/task/1790/fdinfo': Permission denied
    find: `/proc/1786/task/1790/ns': Permission denied
    find: `/proc/1786/task/1791/fd': Permission denied
    find: `/proc/1786/task/1791/fdinfo': Permission denied
    find: `/proc/1786/task/1791/ns': Permission denied
    find: `/proc/1786/task/1792/fd': Permission denied
    find: `/proc/1786/task/1792/fdinfo': Permission denied
    find: `/proc/1786/task/1792/ns': Permission denied
    find: `/proc/1786/task/1793/fd': Permission denied
    find: `/proc/1786/task/1793/fdinfo': Permission denied
    find: `/proc/1786/task/1793/ns': Permission denied
    find: `/proc/1786/task/1794/fd': Permission denied
    find: `/proc/1786/task/1794/fdinfo': Permission denied
    find: `/proc/1786/task/1794/ns': Permission denied
    find: `/proc/1786/task/1795/fd': Permission denied
    find: `/proc/1786/task/1795/fdinfo': Permission denied
    find: `/proc/1786/task/1795/ns': Permission denied
    find: `/proc/1786/task/1796/fd': Permission denied
    find: `/proc/1786/task/1796/fdinfo': Permission denied
    find: `/proc/1786/task/1796/ns': Permission denied
    find: `/proc/1786/task/1797/fd': Permission denied
    find: `/proc/1786/task/1797/fdinfo': Permission denied
    find: `/proc/1786/task/1797/ns': Permission denied
    find: `/proc/1786/task/1798/fd': Permission denied
    find: `/proc/1786/task/1798/fdinfo': Permission denied
    find: `/proc/1786/task/1798/ns': Permission denied
    find: `/proc/1786/task/1799/fd': Permission denied
    find: `/proc/1786/task/1799/fdinfo': Permission denied
    find: `/proc/1786/task/1799/ns': Permission denied
    find: `/proc/1786/task/1800/fd': Permission denied
    find: `/proc/1786/task/1800/fdinfo': Permission denied
    find: `/proc/1786/task/1800/ns': Permission denied
    find: `/proc/1786/task/1801/fd': Permission denied
    find: `/proc/1786/task/1801/fdinfo': Permission denied
    find: `/proc/1786/task/1801/ns': Permission denied
    find: `/proc/1786/task/1802/fd': Permission denied
    find: `/proc/1786/task/1802/fdinfo': Permission denied
    find: `/proc/1786/task/1802/ns': Permission denied
    find: `/proc/1786/task/1803/fd': Permission denied
    find: `/proc/1786/task/1803/fdinfo': Permission denied
    find: `/proc/1786/task/1803/ns': Permission denied
    find: `/proc/1786/task/1804/fd': Permission denied
    find: `/proc/1786/task/1804/fdinfo': Permission denied
    find: `/proc/1786/task/1804/ns': Permission denied
    find: `/proc/1786/task/1805/fd': Permission denied
    find: `/proc/1786/task/1805/fdinfo': Permission denied
    find: `/proc/1786/task/1805/ns': Permission denied
    find: `/proc/1786/task/1806/fd': Permission denied
    find: `/proc/1786/task/1806/fdinfo': Permission denied
    find: `/proc/1786/task/1806/ns': Permission denied
    find: `/proc/1786/task/1807/fd': Permission denied
    find: `/proc/1786/task/1807/fdinfo': Permission denied
    find: `/proc/1786/task/1807/ns': Permission denied
    find: `/proc/1786/task/1808/fd': Permission denied
    find: `/proc/1786/task/1808/fdinfo': Permission denied
    find: `/proc/1786/task/1808/ns': Permission denied
    find: `/proc/1786/task/1809/fd': Permission denied
    find: `/proc/1786/task/1809/fdinfo': Permission denied
    find: `/proc/1786/task/1809/ns': Permission denied
    find: `/proc/1786/task/1810/fd': Permission denied
    find: `/proc/1786/task/1810/fdinfo': Permission denied
    find: `/proc/1786/task/1810/ns': Permission denied
    find: `/proc/1786/task/1811/fd': Permission denied
    find: `/proc/1786/task/1811/fdinfo': Permission denied
    find: `/proc/1786/task/1811/ns': Permission denied
    find: `/proc/1786/task/1812/fd': Permission denied
    find: `/proc/1786/task/1812/fdinfo': Permission denied
    find: `/proc/1786/task/1812/ns': Permission denied
    find: `/proc/1786/task/1813/fd': Permission denied
    find: `/proc/1786/task/1813/fdinfo': Permission denied
    find: `/proc/1786/task/1813/ns': Permission denied
    find: `/proc/1786/task/1814/fd': Permission denied
    find: `/proc/1786/task/1814/fdinfo': Permission denied
    find: `/proc/1786/task/1814/ns': Permission denied
    find: `/proc/1786/task/1815/fd': Permission denied
    find: `/proc/1786/task/1815/fdinfo': Permission denied
    find: `/proc/1786/task/1815/ns': Permission denied
    find: `/proc/1786/task/1816/fd': Permission denied
    find: `/proc/1786/task/1816/fdinfo': Permission denied
    find: `/proc/1786/task/1816/ns': Permission denied
    find: `/proc/1786/task/1817/fd': Permission denied
    find: `/proc/1786/task/1817/fdinfo': Permission denied
    find: `/proc/1786/task/1817/ns': Permission denied
    find: `/proc/1786/task/1818/fd': Permission denied
    find: `/proc/1786/task/1818/fdinfo': Permission denied
    find: `/proc/1786/task/1818/ns': Permission denied
    find: `/proc/1786/task/1819/fd': Permission denied
    find: `/proc/1786/task/1819/fdinfo': Permission denied
    find: `/proc/1786/task/1819/ns': Permission denied
    find: `/proc/1786/task/1820/fd': Permission denied
    find: `/proc/1786/task/1820/fdinfo': Permission denied
    find: `/proc/1786/task/1820/ns': Permission denied
    find: `/proc/1786/task/1821/fd': Permission denied
    find: `/proc/1786/task/1821/fdinfo': Permission denied
    find: `/proc/1786/task/1821/ns': Permission denied
    find: `/proc/1786/task/1822/fd': Permission denied
    find: `/proc/1786/task/1822/fdinfo': Permission denied
    find: `/proc/1786/task/1822/ns': Permission denied
    find: `/proc/1786/task/1823/fd': Permission denied
    find: `/proc/1786/task/1823/fdinfo': Permission denied
    find: `/proc/1786/task/1823/ns': Permission denied
    find: `/proc/1786/task/1824/fd': Permission denied
    find: `/proc/1786/task/1824/fdinfo': Permission denied
    find: `/proc/1786/task/1824/ns': Permission denied
    find: `/proc/1786/task/1825/fd': Permission denied
    find: `/proc/1786/task/1825/fdinfo': Permission denied
    find: `/proc/1786/task/1825/ns': Permission denied
    find: `/proc/1786/task/1826/fd': Permission denied
    find: `/proc/1786/task/1826/fdinfo': Permission denied
    find: `/proc/1786/task/1826/ns': Permission denied
    find: `/proc/1786/task/1827/fd': Permission denied
    find: `/proc/1786/task/1827/fdinfo': Permission denied
    find: `/proc/1786/task/1827/ns': Permission denied
    find: `/proc/1786/task/1828/fd': Permission denied
    find: `/proc/1786/task/1828/fdinfo': Permission denied
    find: `/proc/1786/task/1828/ns': Permission denied
    find: `/proc/1786/task/1829/fd': Permission denied
    find: `/proc/1786/task/1829/fdinfo': Permission denied
    find: `/proc/1786/task/1829/ns': Permission denied
    find: `/proc/1786/task/1830/fd': Permission denied
    find: `/proc/1786/task/1830/fdinfo': Permission denied
    find: `/proc/1786/task/1830/ns': Permission denied
    find: `/proc/1786/task/1831/fd': Permission denied
    find: `/proc/1786/task/1831/fdinfo': Permission denied
    find: `/proc/1786/task/1831/ns': Permission denied
    find: `/proc/1786/task/1832/fd': Permission denied
    find: `/proc/1786/task/1832/fdinfo': Permission denied
    find: `/proc/1786/task/1832/ns': Permission denied
    find: `/proc/1786/task/1833/fd': Permission denied
    find: `/proc/1786/task/1833/fdinfo': Permission denied
    find: `/proc/1786/task/1833/ns': Permission denied
    find: `/proc/1786/task/1834/fd': Permission denied
    find: `/proc/1786/task/1834/fdinfo': Permission denied
    find: `/proc/1786/task/1834/ns': Permission denied
    find: `/proc/1786/task/1835/fd': Permission denied
    find: `/proc/1786/task/1835/fdinfo': Permission denied
    find: `/proc/1786/task/1835/ns': Permission denied
    find: `/proc/1786/task/1836/fd': Permission denied
    find: `/proc/1786/task/1836/fdinfo': Permission denied
    find: `/proc/1786/task/1836/ns': Permission denied
    find: `/proc/1786/task/1837/fd': Permission denied
    find: `/proc/1786/task/1837/fdinfo': Permission denied
    find: `/proc/1786/task/1837/ns': Permission denied
    find: `/proc/1786/task/1838/fd': Permission denied
    find: `/proc/1786/task/1838/fdinfo': Permission denied
    find: `/proc/1786/task/1838/ns': Permission denied
    find: `/proc/1786/task/1839/fd': Permission denied
    find: `/proc/1786/task/1839/fdinfo': Permission denied
    find: `/proc/1786/task/1839/ns': Permission denied
    find: `/proc/1786/task/1840/fd': Permission denied
    find: `/proc/1786/task/1840/fdinfo': Permission denied
    find: `/proc/1786/task/1840/ns': Permission denied
    find: `/proc/1786/task/1841/fd': Permission denied
    find: `/proc/1786/task/1841/fdinfo': Permission denied
    find: `/proc/1786/task/1841/ns': Permission denied
    find: `/proc/1786/task/1842/fd': Permission denied
    find: `/proc/1786/task/1842/fdinfo': Permission denied
    find: `/proc/1786/task/1842/ns': Permission denied
    find: `/proc/1786/task/1843/fd': Permission denied
    find: `/proc/1786/task/1843/fdinfo': Permission denied
    find: `/proc/1786/task/1843/ns': Permission denied
    find: `/proc/1786/task/1844/fd': Permission denied
    find: `/proc/1786/task/1844/fdinfo': Permission denied
    find: `/proc/1786/task/1844/ns': Permission denied
    find: `/proc/1786/task/1845/fd': Permission denied
    find: `/proc/1786/task/1845/fdinfo': Permission denied
    find: `/proc/1786/task/1845/ns': Permission denied
    find: `/proc/1786/task/1846/fd': Permission denied
    find: `/proc/1786/task/1846/fdinfo': Permission denied
    find: `/proc/1786/task/1846/ns': Permission denied
    find: `/proc/1786/task/1847/fd': Permission denied
    find: `/proc/1786/task/1847/fdinfo': Permission denied
    find: `/proc/1786/task/1847/ns': Permission denied
    find: `/proc/1786/task/1848/fd': Permission denied
    find: `/proc/1786/task/1848/fdinfo': Permission denied
    find: `/proc/1786/task/1848/ns': Permission denied
    find: `/proc/1786/task/1850/fd': Permission denied
    find: `/proc/1786/task/1850/fdinfo': Permission denied
    find: `/proc/1786/task/1850/ns': Permission denied
    find: `/proc/1786/task/1851/fd': Permission denied
    find: `/proc/1786/task/1851/fdinfo': Permission denied
    find: `/proc/1786/task/1851/ns': Permission denied
    find: `/proc/1786/fd': Permission denied
    find: `/proc/1786/fdinfo': Permission denied
    find: `/proc/1786/ns': Permission denied
    find: `/proc/1939/task/1939/fd': Permission denied
    find: `/proc/1939/task/1939/fdinfo': Permission denied
    find: `/proc/1939/task/1939/ns': Permission denied
    find: `/proc/1939/fd': Permission denied
    find: `/proc/1939/fdinfo': Permission denied
    find: `/proc/1939/ns': Permission denied
    find: `/proc/1977/task/1977/fd': Permission denied
    find: `/proc/1977/task/1977/fdinfo': Permission denied
    find: `/proc/1977/task/1977/ns': Permission denied
    find: `/proc/1977/task/1978/fd': Permission denied
    find: `/proc/1977/task/1978/fdinfo': Permission denied
    find: `/proc/1977/task/1978/ns': Permission denied
    find: `/proc/1977/task/1979/fd': Permission denied
    find: `/proc/1977/task/1979/fdinfo': Permission denied
    find: `/proc/1977/task/1979/ns': Permission denied
    find: `/proc/1977/fd': Permission denied
    find: `/proc/1977/fdinfo': Permission denied
    find: `/proc/1977/ns': Permission denied
    find: `/proc/1994/task/1994/fd': Permission denied
    find: `/proc/1994/task/1994/fdinfo': Permission denied
    find: `/proc/1994/task/1994/ns': Permission denied
    find: `/proc/1994/task/1996/fd': Permission denied
    find: `/proc/1994/task/1996/fdinfo': Permission denied
    find: `/proc/1994/task/1996/ns': Permission denied
    find: `/proc/1994/task/2436/fd': Permission denied
    find: `/proc/1994/task/2436/fdinfo': Permission denied
    find: `/proc/1994/task/2436/ns': Permission denied
    find: `/proc/1994/fd': Permission denied
    find: `/proc/1994/fdinfo': Permission denied
    find: `/proc/1994/ns': Permission denied
    find: `/proc/1995/task/1995/fd': Permission denied
    find: `/proc/1995/task/1995/fdinfo': Permission denied
    find: `/proc/1995/task/1995/ns': Permission denied
    find: `/proc/1995/fd': Permission denied
    find: `/proc/1995/fdinfo': Permission denied
    find: `/proc/1995/ns': Permission denied
    find: `/proc/2070/task/2070/fd': Permission denied
    find: `/proc/2070/task/2070/fdinfo': Permission denied
    find: `/proc/2070/task/2070/ns': Permission denied
    find: `/proc/2070/task/2071/fd': Permission denied
    find: `/proc/2070/task/2071/fdinfo': Permission denied
    find: `/proc/2070/task/2071/ns': Permission denied
    find: `/proc/2070/task/2072/fd': Permission denied
    find: `/proc/2070/task/2072/fdinfo': Permission denied
    find: `/proc/2070/task/2072/ns': Permission denied
    find: `/proc/2070/fd': Permission denied
    find: `/proc/2070/fdinfo': Permission denied
    find: `/proc/2070/ns': Permission denied
    find: `/proc/2282/task/2282/fd': Permission denied
    find: `/proc/2282/task/2282/fdinfo': Permission denied
    find: `/proc/2282/task/2282/ns': Permission denied
    find: `/proc/2282/task/2290/fd': Permission denied
    find: `/proc/2282/task/2290/fdinfo': Permission denied
    find: `/proc/2282/task/2290/ns': Permission denied
    find: `/proc/2282/fd': Permission denied
    find: `/proc/2282/fdinfo': Permission denied
    find: `/proc/2282/ns': Permission denied
    find: `/proc/2312/task/2312/fd': Permission denied
    find: `/proc/2312/task/2312/fdinfo': Permission denied
    find: `/proc/2312/task/2312/ns': Permission denied
    find: `/proc/2312/fd': Permission denied
    find: `/proc/2312/fdinfo': Permission denied
    find: `/proc/2312/ns': Permission denied
    find: `/proc/2350/task/2350/fd': Permission denied
    find: `/proc/2350/task/2350/fdinfo': Permission denied
    find: `/proc/2350/task/2350/ns': Permission denied
    find: `/proc/2350/task/2351/fd': Permission denied
    find: `/proc/2350/task/2351/fdinfo': Permission denied
    find: `/proc/2350/task/2351/ns': Permission denied
    find: `/proc/2350/fd': Permission denied
    find: `/proc/2350/fdinfo': Permission denied
    find: `/proc/2350/ns': Permission denied
    find: `/proc/11437/task/11437/fd': Permission denied
    find: `/proc/11437/task/11437/fdinfo': Permission denied
    find: `/proc/11437/task/11437/ns': Permission denied
    find: `/proc/11437/fd': Permission denied
    find: `/proc/11437/fdinfo': Permission denied
    find: `/proc/11437/ns': Permission denied
    find: `/proc/11985/task/11985/fd': Permission denied
    find: `/proc/11985/task/11985/fdinfo': Permission denied
    find: `/proc/11985/task/11985/ns': Permission denied
    find: `/proc/11985/task/11986/fd': Permission denied
    find: `/proc/11985/task/11986/fdinfo': Permission denied
    find: `/proc/11985/task/11986/ns': Permission denied
    find: `/proc/11985/task/11987/fd': Permission denied
    find: `/proc/11985/task/11987/fdinfo': Permission denied
    find: `/proc/11985/task/11987/ns': Permission denied
    find: `/proc/11985/task/12022/fd': Permission denied
    find: `/proc/11985/task/12022/fdinfo': Permission denied
    find: `/proc/11985/task/12022/ns': Permission denied
    find: `/proc/11985/fd': Permission denied
    find: `/proc/11985/fdinfo': Permission denied
    find: `/proc/11985/ns': Permission denied
    find: `/proc/14530/task/14530/fd': Permission denied
    find: `/proc/14530/task/14530/fdinfo': Permission denied
    find: `/proc/14530/task/14530/ns': Permission denied
    find: `/proc/14530/fd': Permission denied
    find: `/proc/14530/fdinfo': Permission denied
    find: `/proc/14530/ns': Permission denied
    find: `/proc/14678/task/14678/fd': Permission denied
    find: `/proc/14678/task/14678/fdinfo': Permission denied
    find: `/proc/14678/task/14678/ns': Permission denied
    find: `/proc/14678/fd': Permission denied
    find: `/proc/14678/fdinfo': Permission denied
    find: `/proc/14678/ns': Permission denied
    find: `/proc/14685/task/14685/fd': Permission denied
    find: `/proc/14685/task/14685/fdinfo': Permission denied
    find: `/proc/14685/task/14685/ns': Permission denied
    find: `/proc/14685/fd': Permission denied
    find: `/proc/14685/fdinfo': Permission denied
    find: `/proc/14685/ns': Permission denied
    find: `/proc/14690/task/14690/fd': Permission denied
    find: `/proc/14690/task/14690/fdinfo': Permission denied
    find: `/proc/14690/task/14690/ns': Permission denied
    find: `/proc/14690/fd': Permission denied
    find: `/proc/14690/fdinfo': Permission denied
    find: `/proc/14690/ns': Permission denied
    find: `/proc/14692/task/14692/fd': Permission denied
    find: `/proc/14692/task/14692/fdinfo': Permission denied
    find: `/proc/14692/task/14692/ns': Permission denied
    find: `/proc/14692/fd': Permission denied
    find: `/proc/14692/fdinfo': Permission denied
    find: `/proc/14692/ns': Permission denied
    find: `/proc/14703/task/14703/fd': Permission denied
    find: `/proc/14703/task/14703/fdinfo': Permission denied
    find: `/proc/14703/task/14703/ns': Permission denied
    find: `/proc/14703/fd': Permission denied
    find: `/proc/14703/fdinfo': Permission denied
    find: `/proc/14703/ns': Permission denied
    find: `/proc/14724/task/14724/fd': Permission denied
    find: `/proc/14724/task/14724/fdinfo': Permission denied
    find: `/proc/14724/task/14724/ns': Permission denied
    find: `/proc/14724/fd': Permission denied
    find: `/proc/14724/fdinfo': Permission denied
    find: `/proc/14724/ns': Permission denied
    find: `/proc/14818/task/14818/fd': Permission denied
    find: `/proc/14818/task/14818/fdinfo': Permission denied
    find: `/proc/14818/task/14818/ns': Permission denied
    find: `/proc/14818/fd': Permission denied
    find: `/proc/14818/fdinfo': Permission denied
    find: `/proc/14818/ns': Permission denied
    find: `/proc/14824/task/14824/fd': Permission denied
    find: `/proc/14824/task/14824/fdinfo': Permission denied
    find: `/proc/14824/task/14824/ns': Permission denied
    find: `/proc/14824/fd': Permission denied
    find: `/proc/14824/fdinfo': Permission denied
    find: `/proc/14824/ns': Permission denied
    find: `/proc/14846/task/14846/fd': Permission denied
    find: `/proc/14846/task/14846/fdinfo': Permission denied
    find: `/proc/14846/task/14846/ns': Permission denied
    find: `/proc/14846/fd': Permission denied
    find: `/proc/14846/fdinfo': Permission denied
    find: `/proc/14846/ns': Permission denied
    find: `/proc/14905/task/14905/fd/5': No such file or directory
    find: `/proc/14905/task/14905/fdinfo/5': No such file or directory
    find: `/proc/14905/fd/5': No such file or directory
    find: `/proc/14905/fdinfo/5': No such file or directory

```I'm not sure what I'm doing wrong if it's trying to mess with files it isn't supposed to.  I asked the DockbarX developer to try it out on his own and he was able to get it to work, so it has to be something I'm doing.  I don't know anything about shell scripting, so I don't know if it's anything to do with the script itself.  :/

---

### Post by Giant Speck on 2012-10-18
Nevermind.  I figured out what I was doing wrong.  I didn't include the period in "pkgdir=.".

---

