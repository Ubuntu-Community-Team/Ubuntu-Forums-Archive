---
title: "Error message on desktop"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-06-09
I get the following error message after I boot to Gnome:

[I]Could not load icon
Details:  Icon 'khelpcenter.xpm' not found[/I]

I think this is a result of my trying to fix some ATI driver issues I followed the instructions from [here]("http://ubuntuforums.org/showthread.php?t=143283&page=12") & that gave me this result:

sudo aptitude remove linux-restricted-modules-2.6.15-23-386
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
linux-restricted-modules-386
The following packages will be REMOVED:
linux-restricted-modules-2.6.15-23-386
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 22.1MB will be freed.
The following packages have unmet dependencies:
linux-restricted-modules-386: Depends: linux-restricted-modules-2.6.15-23-386 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-386
linux-restricted-modules-386

Score is -652

Accept this solution? [Y/n/q/?]


I'm a little skittish to go any further because earlier I followed the instructions at the bottom of the page here & had the following programs removed:

akregator ark arts artsbuilder flac gqview graveman gtk2-engines-gtk-qt
gtk2-engines-xfce gwenview ivman k3b kappfinder karm katapult kate
kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings
kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins
kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
kdepim-kresources kdepim-wizards kdeprint kdm khelpcenter kio-apt
kio-locate kitchensync klaptopdaemon klipper kmenuedit kmilo kmix
knetworkconf knode knotes koffice-data koffice-libs konq-plugins
konqueror-nsplugins konserve kontact konversation kooka kopete korganizer
kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita kscd
kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksvg ksysguard
ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings
kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager
kwifimanager libcdio3 libdbh1.0-1 libgadu3 libgnokii2 libid3tag0
libiso9660-3 libkipi0 libkpimexchange1 libkscan1 liblockdev1 liboggflac3
libpoppler0c2-qt libpythonize0 libsamplerate0 libvcdinfo0 libxine1c2
metamail mousepad ncompress ocrad poster psutils python-kde3
python-opengl python2.4-dev python2.4-kde3 python2.4-opengl qca-tls qobex
rox-filer sox speedcrunch sylpheed sylpheed-claws-scripts sylpheed-i18n
vcdimager vorbis-tools xfce4 xfce4-appfinder xfce4-artwork
xfce4-battery-plugin xfce4-clipman-plugin xfce4-diskperf-plugin
xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme
xfce4-minicmd-plugin xfce4-netload-plugin xfce4-sensors-plugin
xfce4-session xfce4-systemload-plugin xfce4-taskmanager
xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin
xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4
xine-ui xubuntu-artwork-usplash zoo


Can anyone help?

---

### Post by an.echte.trilingue on 2006-06-09
I would try this first:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

That tends to fix lots of problems.

---

### Post by mcduck on 2006-06-09
Instead of installing any specific kernel version or restricted modules version you should get the linux-386, linux-686 or linux-K7 package. It depends on latest version of kernel, restricted modules and kernel headers, making sure you'll always have the latest version available.

---

### Post by JGKC9AYC on 2006-06-09
[QUOTE=mcduck]Instead of installing any specific kernel version or restricted modules version you should get the linux-386, linux-686 or linux-K7 package. It depends on latest version of kernel, restricted modules and kernel headers, making sure you'll always have the latest version available.[/QUOTE]

I'm a little new to this.  I went to the "Download Ubuntu" link & it appears the only options I have for my AMD machine is either the 386 package (which i'm currently running...upgrade from Breezy) or the 64-bit package.
If I remember right, the kernel i'm running is 2.6.15-23-386.  What & where is the 686 kernel?
Thanks

---

### Post by mcduck on 2006-06-09
[QUOTE=JGKC9AYC]I'm a little new to this.  I went to the "Download Ubuntu" link & it appears the only options I have for my AMD machine is either the 386 package (which i'm currently running...upgrade from Breezy) or the 64-bit package.
If I remember right, the kernel i'm running is 2.6.15-23-386.  What & where is the 686 kernel?
Thanks[/QUOTE]
You'll find it, as well as every app one could possibly need, In Ubuntus repositories. Open System/Administration/Synaptic Package Manager and enjoy the power of Linux :D

Or open a terminal (Applications/Accessories/Terminal), type 'sudo apt-get install linux-686', press enter, give your password and wait while your new kernel is downloaded&installed for you..

Here's a guide about installing things in Ubuntu, it has nice instructions how to use Synaptic and might come handy for you anyway: [http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")

---

### Post by JGKC9AYC on 2006-06-09
[QUOTE=mcduck]You'll find it, as well as every app one could possibly need, In Ubuntus repositories. Open System/Administration/Synaptic Package Manager and enjoy the power of Linux :D

Or open a terminal (Applications/Accessories/Terminal), type 'sudo apt-get install linux-686', press enter, give your password and wait while your new kernel is downloaded&installed for you..

Here's a guide about installing things in Ubuntu, it has nice instructions how to use Synaptic and might come handy for you anyway: [http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")[/QUOTE]

I went & did both things you suggested...the Synaptic Package Manager as well as the sudo apt-get.......& i'm still getting the error message about the Could not load icon
Details: Icon 'khelpcenter.xpm' not found
When I was in Synaptic, I marked all the boxes that were already shaded (I assume from the earlier deletion) & marked them for re-installation.  However, KDE is not an option when I get to the login screen...only Gnome & X.

---

### Post by JGKC9AYC on 2006-06-10
So in order for me to get back all the programs that were deleted, i'll have to do this:

```
sudo apt-get install kubuntu-desktop
```

Is that correct?

---

### Post by JGKC9AYC on 2006-06-10
Anyone?

---

