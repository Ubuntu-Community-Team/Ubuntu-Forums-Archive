---
title: "'apt-get remove's insane behaviour :)"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by zw0rk on 2007-10-06
I don't understand deb's dependencies. I'm trying to remove rhythmbox, apt says, that it will remove GNOME too. But, Gnome ISN'T a part of rhythmbox. How do i remove rhythmbox and leave Gnome alone?

---

### Post by Frak on 2007-10-06
What is the exact error message, it could be that your getting a metapackage error and not an actuall physical dependency error.

---

### Post by zw0rk on 2007-10-06
root@desktop:~# apt-get remove rhythmbox
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1073;&#1099;&#1083;&#1080; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099; &#1072;&#1074;&#1090;&#1086;&#1084;&#1072;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080; &#1085;&#1086; &#1073;&#1086;&#1083;&#1077;&#1077; &#1085;&#1077; &#1090;&#1088;&#1077;&#1073;&#1091;&#1102;&#1090;&#1089;&#1103;:
  libgnomecupsui1.0-1c2a evolution-common planner ekiga libgsf-gnome-1-114 gcalctool gnome-desktop-environment gnome-nettool libgoffice-0-common gnome-games-extra-data
  abiword-gnome dia-libs gucharmap industrial-cursor-theme zenity gnome-games evolution esound libexchange-storage1.2-3 gnome-cards-data gnome-screensaver libgtksourceview1.0-0
  gedit gnome-office abiword-common libpisock9 gnome-themes whois gnumeric-common gtkhtml3.14 guile-1.6-libs gedit-common gnome-utils gnome-themes-extras libcairomm-1.0-1
  libgnome-pilot2 libglibmm-2.4-1c2a gdm-themes fast-user-switch-applet gnome-volume-manager dia-gnome libpt-plugins-v4l eog gdm gnome-backgrounds bug-buddy libnm-glib0
  libgtksourceview-common vino gnome-keyring-manager libgtkmm-2.4-1c2a libqthreads-12 gnome-games-data libgoffice-0-3 totem-gstreamer libgnomevfs2-bin gnome-core dia-common
  libpt-plugins-alsa libgda2-3 gnumeric libopal-2.2.0 gconf-editor libtotem-plparser1 gnome-system-tools libgda2-common gtk2-engines-spherecrystal gstreamer0.10-gnomevfs totem
  python-gnome2-desktop gnome-mount libpt-1.10.0 inkscape libguile-ltdl-1 totem-mozilla file-roller gnome-cups-manager sound-juicer libpisync0
&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1091; 'apt-get autoremove' &#1076;&#1083;&#1103; &#1080;&#1093; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103;.
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1059;&#1044;&#1040;&#1051;&#1045;&#1053;&#1067;:
  gnome rhythmbox
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 2 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1089;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; 0&#1041; &#1072;&#1088;&#1093;&#1080;&#1074;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1088;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1082;&#1080; &#1086;&#1073;&#1098;&#1077;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1091;&#1084;&#1077;&#1085;&#1100;&#1096;&#1080;&#1090;&#1089;&#1103; &#1085;&#1072; 11,1MB.


It's in russian :) It says, that if i remove rhythmox -- all of those packages will be removed too :(

---

### Post by HermanAB on 2007-10-06
Well, the Deb and RPM systems list dependencies to make installing software easier.  It isn't really geared towards removing software.  So, unless you have zero bytes left on your HDD, just leave the thing.  In general, the less changes you make to your system, the longer it will work trouble free - this is unavoidable due to the first law of thermodynamics: Entropy always increases.

If you are hard headed about it, then read the deb man page.  There is a way to remove stuff without following dependencies but I can't recommend it.

Cheers,

Herman

---

### Post by Frak on 2007-10-06
I translated it, and I would leave rythmbox.

Of course the last line when translated came up to
> After unpacking the amount of disk space to decrease employee pay at 11.1 MB.

So, yeah, money is a good reason not to uninstall it also ;)
Darn you Google translate...

---

