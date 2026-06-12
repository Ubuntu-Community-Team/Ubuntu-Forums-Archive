---
title: "editing menu"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2006-12-09
I installed menu so that i wouldn't have to manually add all the programs to icewm's menu. is there a easy program to edit the menu in programs.

---

### Post by aysiu on 2006-12-09
Yes, edit a file (or, if it doesn't yet exist, create a file) called /home/cosmoshell/.icewm/programs

Mine looks something like this: ```
# This is an example for IceWM's menu definition file.
#
# Place your variants in /etc/X11/icewm or in $HOME/.icewm
# since modifications to this file will be discarded when you
# (re)install icewm.
#



menu "Accessories" folder {
  prog    "Calculator" "/usr/share/icons/Tango/24x24/apps/gnome-calculator.png" gcalctool
  prog    "Text Editor" "/usr/share/icons/Tango/24x24/apps/text-editor.png" gedit
  prog    "Character Map" "/usr/share/icons/Tango/24x24/apps/gucharmap.png" "/usr/bin/gucharmap"
  prog    "Dictionary" "/usr/share/pixmaps/gnome-dictionary.png" "/usr/bin/gnome-dictionary"
  prog    "File Manager" "/usr/share/icons/Tango/24x24/apps/file-manager.png" "/usr/bin/thunar"
  prog    "Search Files/Folders" "/usr/share/icons/Tango/24x24/actions/gnome-searchtool.png" "/usr/bin/gnome-search-tool"
  prog    "Terminal" "/usr/share/icons/Tango/24x24/apps/gnome-terminal.png" gnome-terminal
  prog    "Help" "/usr/share/icons/hicolor/192x192/apps/yelp-icon-big.png" "/usr/bin/yelp"
}
menu "Games" folder {
  prog    "Gnibbles" /usr/share/pixmaps/gnibbles.xpm /bin/sh -c "/usr/games/gnibbles"
  prog    "Four-in-a-row" /usr/share/pixmaps/gnect.xpm /bin/sh -c "/usr/games/gnect"
  prog    "Gataxx" /usr/share/pixmaps/gataxx.xpm /bin/sh -c "/usr/games/gataxx"
  prog    "Gnome GYahtzee" /usr/share/pixmaps/gtali.xpm /bin/sh -c "/usr/games/gtali"
  prog    "Gnome Iagno" /usr/share/pixmaps/iagno.xpm /bin/sh -c "/usr/games/iagno"
  prog    "Gnome Lines" /usr/share/pixmaps/glines.xpm /bin/sh -c "/usr/games/glines"
  prog    "Gnome Mahjongg" /usr/share/pixmaps/gnome-mahjongg.xpm /bin/sh -c "/usr/games/mahjongg"
  prog    "Gnome Blackjack" /usr/share/pixmaps/blackjack.xpm /bin/sh -c "/usr/games/blackjack"
  prog    "Gnome FreeCell" /usr/share/pixmaps/freecell.xpm /bin/sh -c "/usr/games/sol --variation freecell"
  prog    "Gnome Solitaire Games" /usr/share/pixmaps/aisleriot.xpm /bin/sh -c "/usr/games/sol"
  prog    "Gnome Klotski" /usr/share/pixmaps/gnotski.xpm /bin/sh -c "/usr/games/gnotski"
  prog    "Gnome Robots" /usr/share/pixmaps/gnobots2.xpm /bin/sh -c "/usr/games/gnobots2"
  prog    "Gnome Tetravex" /usr/share/pixmaps/gnotravex.xpm /bin/sh -c "/usr/games/gnotravex"
  prog    "Gnomine" /usr/share/pixmaps/gnomine.xpm /bin/sh -c "/usr/games/gnomine"
  prog    "Same Gnome" /usr/share/pixmaps/gsame.xpm /bin/sh -c "/usr/games/same-gnome"
  prog    "Gnometris" /usr/share/pixmaps/gnometris.xpm /bin/sh -c "/usr/games/gnometris"
}
menu "Graphics" folder {
  prog    "GNU Image Manipulation Program" /usr/share/gimp/2.0/images/wilber-icon.png /bin/sh -c "/usr/bin/gimp-2.2"
  prog    "gThumb Image Viewer" /usr/share/pixmaps/gthumb.xpm /bin/sh -c "/usr/bin/gthumb"
  prog    "XSane" /usr/share/pixmaps/xsane.xpm /bin/sh -c "/usr/bin/xsane"
}
menu "Office" folder {
  prog    "Evince Document Viewer" /usr/share/icons/gnome/24x24/apps/postscript-viewer.png /bin/sh -c "/usr/bin/evince"
  prog    "OpenOffice.org Calc" /usr/share/icons/gnome/32x32/apps/openofficeorg-20-calc.xpm /bin/sh -c "/usr/bin/oocalc"
  prog    "OpenOffice.org Draw" /usr/share/icons/gnome/32x32/apps/openofficeorg-20-draw.xpm /bin/sh -c "/usr/bin/oodraw"
  prog    "OpenOffice.org Impress" /usr/share/icons/gnome/32x32/apps/openofficeorg-20-impress.xpm /bin/sh -c "/usr/bin/ooimpress"
  prog    "OpenOffice.org Math" /usr/share/icons/gnome/32x32/apps/openofficeorg-20-math.xpm /bin/sh -c "/usr/bin/oomath"
  prog    "OpenOffice.org Writer" /usr/share/icons/gnome/32x32/apps/openofficeorg-20-writer.xpm /bin/sh -c "/usr/bin/oowriter"
}
menu "Internet" folder {
  prog    "Evolution" "/usr/share/icons/gnome/24x24/apps/evolution-mail.png" "/usr/bin/evolution"
  prog    "Firefox Web Browser" "/usr/share/pixmaps/firefox.png" "firefox"
  prog    "Gaim" "/usr/share/icons/Tango/24x24/apps/gaim.png" "/usr/bin/gaim"
}
menu "Sound and Video" folder {
  prog    "Mixer" /usr/share/pixmaps/gnome-mixer.xpm /bin/sh -c "/usr/bin/gnome-volume-control"
  prog    "CD Player" /usr/share/pixmaps/gnome-cd.xpm /bin/sh -c "/usr/bin/gnome-cd"
  prog    "Sound Recorder" /usr/share/pixmaps/gnome-grecord.xpm /bin/sh -c "/usr/bin/gnome-sound-recorder"
  prog    "Rhythmbox" /usr/share/pixmaps/rhythmbox.xpm /bin/sh -c "/usr/bin/rhythmbox"
  prog    "Sound Juicer" "/usr/share/icons/hicolor/24x24/apps/sound-juicer.png" "/usr/bin/sound-juicer"
  prog    "Totem Movie Player" /usr/share/totem/media-player-48.png /bin/sh -c "/usr/bin/totem"
}
menu "System" folder {
  prog    "Boot Admin" "/usr/share/gnome/help/boot-admin/C/figures/boot-tool.png" "/usr/bin/boot-admin"
  prog    "Disks Admin" "/usr/share/gnome-system-tools/pixmaps/disks.png" "/usr/bin/disks-admin"
  prog    "DSL/PPPoE configuration tool" /usr/share/pixmaps/pppoeconf.xpm /bin/sh -c "x-terminal-emulator  -T \"DSL/PPPoE configuration tool\" -e sh -c \"/usr/sbin/pppoeconf\""
  prog    "GDM flexiserver" /usr/share/pixmaps/gdm.xpm /bin/sh -c "gdmflexiserver"
  prog    "GDM Setup" /usr/share/pixmaps/gdm.xpm /bin/sh -c "gksu gdmsetup"
  prog    "GNOME Bug Report Tool" /usr/share/pixmaps/bug-buddy.xpm /bin/sh -c "/usr/bin/bug-buddy"
  prog    "GNOME CUPS Manager" "/usr/share/pixmaps/gnome-cups-manager/printer-tray-normal.png" "/usr/bin/gnome-cups-manager"
  prog    "GNOME Floppy Formatter" /usr/share/pixmaps/gfloppy.xpm /bin/sh -c "/usr/bin/gfloppy"
  prog    "GNOME Log Viewer" /usr/share/pixmaps/gnome-system-log.xpm /bin/sh -c "/usr/bin/gnome-system-log"
  prog    "GNOME Network Tool" /usr/share/pixmaps/gnome-nettool.xpm /bin/sh -c "/usr/bin/gnome-nettool"
  prog    "GNOME system monitor" "/usr/share/icons/Tango/24x24/apps/gnome-monitor.png" "/usr/bin/gnome-system-monitor"
  prog    "Network Admin" "/usr/share/icons/Tango/24x24/places/network.png" "/usr/bin/network-admin"
  prog    "Synaptic Package Manager" /usr/share/synaptic/pixmaps/synaptic_32x32.xpm /bin/sh -c "/usr/bin/gksu /usr/sbin/synaptic"
  prog    "Time Admin" /usr/share/gnome-system-tools/pixmaps/time.png /bin/sh -c "/usr/bin/time-admin"
  prog    "User accounts Admin" /usr/share/icons/Tango/24x24/apps/config-users.png /bin/sh -c "/usr/bin/users-admin"
}
``` That's the Programs submenu in the main menu. If you want to edit the main menu directly, edit and/or create a file called /home/cosmoshell/.icewm/menu

Mine looks like this: ```
prog "Thunderbird" "/usr/share/pixmaps/mozilla-thunderbird.xpm" thunderbird
prog "Firefox" "/usr/share/pixmaps/firefox.png" mozilla
prog "Epiphany" "/usr/share/icons/KDEOSXicons/128x128/apps/epiphany.png" epiphany
prog "Opera" "/usr/share/pixmaps/opera.xpm" opera
separator
prog "Gimp" "/usr/share/icons/KDEOSXicons/128x128/apps/gimp.png" gimp
prog "Inkscape" "/usr/share/icons/KDEOSXicons/128x128/apps/inkscape.png" inkscape
prog "Kolourpaint" "/usr/share/icons/KDEOSXicons/128x128/apps/kpaint.png" kolourpaint
separator
prog "Acrobat Reader" "/usr/share/icons/KDEOSXicons/128x128/apps/acroread.png" acroread
prog "Scribus" "/usr/share/icons/crystalsvg/48x48/apps/scribus.png" scribus
prog "OpenOffice Writer" "/usr/share/icons/KDEOSXicons/128x128/apps/ooo-writer.png" oowriter
prog "OpenOffice Calc" "/usr/share/icons/KDEOSXicons/128x128/apps/ooo-calc.png" oocalc
separator
prog "Amarok" "/usr/share/icons/KDEOSXicons/128x128/apps/amarok.png" amarok
prog "Calculator" "/documents/linux_accessories/kde/osxicons/128x128/apps/speedcrunch.png" gcalctool
prog "Gedit" "/documents/linux_accessories/kde/osxicons/128x128/apps/kwrite2.png" gedit
prog "GnomeSword" "/usr/share/pixmaps/gnomesword/gs2-48x48.png" gnomesword2
prog "Gnometris" "/usr/share/pixmaps/gnome-gtetris.png" /usr/games/gnometris
prog "Rhythmbox" "/usr/share/icons/KDEOSXicons/128x128/apps/amarok.png" rhythmbox
``` As you can see, both follow very similar formats. They have the word *prog*, the name of the program (how you want it to appear in the menu), the icon for the program, and then the command to launch the program.

---

### Post by cosmoshell on 2006-12-09
thanks very helpfull. by the way i found the programs file in /etc/X11/icewm
some reason its not in /home/cosmoshell/.icewm

---

