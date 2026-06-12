---
title: "Help: Java-ATK-Wrapper"
date: 2009-11-10
forum: Assistive Technology &amp; Accessibility
---

### Post by mari23 on 2009-11-10
[FONT=Book Antiqua][SIZE=3][COLOR=#244061]            [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]Hello everyone,[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]I'm trying to install the Java ATK Wrapper 0.28 on both Ubuntu 9.10 and 9.04, working with sun-java6-jdk, but I'm in trouble and I hope someone can help me.[/FONT][/COLOR][/SIZE]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061]I've downloaded the JAW from [/COLOR][/SIZE][/FONT][[FONT=Book Antiqua][SIZE=3][COLOR=#0000ff]http://ftp.gnome.org/pub/GNOME/sources/java-atk-wrapper/[/COLOR][/SIZE][/FONT]]("http://ftp.gnome.org/pub/GNOME/sources/java-atk-wrapper/")[SIZE=3][COLOR=#244061][FONT=Book Antiqua] and I've followed the instructions in INSTALL.txt.[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]After the ./configure command, the terminal had the following message:[/FONT][/COLOR][/SIZE]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]…[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]checking for JAW... configure: error: Package requirements ( [/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]atk      >= 1.17.0[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]     glib-2.0[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]     gthread-2.0[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]     gmodule-2.0[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]     gdk-2.0[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]) were not met:[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]No package 'atk' found[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]No package 'glib-2.0' found[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]No package 'gthread-2.0' found[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]No package 'gmodule-2.0' found[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]No package 'gdk-2.0' found[/COLOR][/SIZE][/FONT]
[FONT=Courier New][SIZE=3][COLOR=#244061]…[/COLOR][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]So I downloaded the package libatspi-dev (is this the right package?), then I ran [/FONT][/COLOR][/SIZE]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]. / configure --prefix=/usr/share/gnome-2.0 JAVA_HOME=/usr/lib/jvm/java-6-sun[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]sudo make[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]sudo make install[/FONT][/COLOR][/SIZE]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]and the installation seemed to have been completed successfully, but Orca does not read any Java demo application and the terminal does not display any error message![/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]What's missing?[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#244061][FONT=Book Antiqua]What can I do?[/FONT][/COLOR][/SIZE]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061] [/COLOR][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061][/COLOR][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061]Thanks [/COLOR][/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=3][COLOR=#244061]Maria Teresa[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Book Antiqua] [/FONT][/COLOR]

---

