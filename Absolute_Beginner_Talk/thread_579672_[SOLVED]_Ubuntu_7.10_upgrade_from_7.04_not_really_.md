---
title: "[SOLVED] Ubuntu 7.10 upgrade from 7.04 not really working."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-10-18
Hello I'm a bit n00bish so please bear with me. 

At about 2a.m last night I tried to upgrade to gusty gibbon. it started to download i think and then my laptop froze and i had to restart. When i got back it would only let me do a partial download and i had to install 646 updates. it installed all except for 4 of them and it wont let me install the last four. there is a button on the update manager saying "update distribution" or something similar and when i click on that all i get is a little window that is empty and is named "Distribution upgrade" i can't close this window and have to restart to get rid of it.

oh and other things like the icon for the terminal has changed and everything (scrollbars, buttons etc) is in simple graphics mode..grey and square like windows 95 (hate to compare it to that but i dont know what else to compare it to... lol)

thanks a million,

Dara

---

### Post by mikeyphi on 2007-10-18
Know what you mean by 'safe graphics mode'!!

Probably need to go to Screens & Graphics and check Video card driver is installed - then change screen resolution.

---

### Post by Frak on 2007-10-18
run
```
sudo apt-get install -f
```

In the terminal
Applications->Accessories->Terminal

And Paste the results.

---

### Post by DaraJava on 2007-10-18
[sudo] password for dara:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 376 not upgraded.



Wow thanks for the quick responses... this community is great!

mikeyphi i my driver is set properly so i dont know whats going on there.

---

### Post by Frak on 2007-10-18
> **DaraJava said:**
> [sudo] password for dara:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 376 not upgraded.



Wow thanks for the quick responses... this community is great!

mikeyphi i my driver is set properly so i dont know whats going on there.
Run
```
sudo apt-get autoremove
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by DaraJava on 2007-10-18
The first 2 commands you gave me work well i think.

The last command you gave me gives this:



Unknown command "safe-upgrade"
aptitude 0.4.4
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

---

### Post by Frak on 2007-10-18
Run

```
sudo apt-get autoremove
sudo aptitude update
sudo aptitude upgrade
```

That tells me that your apt and aptitude were not upgraded, yet.

---

### Post by DaraJava on 2007-10-18
The last one gave me this:


dara@dara-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  amarok-xine g++-4.1 imagemagick kaffeine-xine kdebase-bin 
  kdebase-kio-plugins kdeedu-data kdelibs-data kdelibs4c2a kdesktop 
  khelpcenter koffice-libs libarts1c2a libavahi-qt3-1 libcairomm-1.0-1 
  libcompress-zlib-perl libcurl3-gnutls libfontconfig1-dev libfreetype6-dev 
  libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libid3-3.8.3c2a libkcal2b 
  libkdegames1 libkdepim1a libkleopatra1 libkmime2 libkonq4 
  libkpimidentities1 libktnef1 libmodplug0c2 libofa0 libopenexr2c2a libpq5 
  libqt3-mt libqt4-core libqt4-gui libraptor1 libsmpeg0 libstdc++6-4.1-dev 
  libtunepimp5 libxfont-dev libxft-dev libxine1 linux-image-generic 
  python-qt3 python-sip4 python2.4 python2.4-minimal tetex-bin tetex-extra 
The following packages have been kept back:
  amarok apt apt-utils aptitude aspell at-spi bind9-host brltty brltty-x11 
  capplets-data cdrdao compiz compiz-core compiz-gnome compiz-plugins 
  contact-lookup-applet cpp cpp-4.1 cupsys cupsys-bsd cupsys-client 
  cupsys-driver-gutenprint dbus deskbar-applet dmsetup dnsutils dpkg 
  dselect dvd+rw-tools eject ekiga eog espeak espeak-data evince evolution 
  evolution-common evolution-data-server evolution-data-server-common 
  evolution-exchange evolution-plugins evolution-webcal f-spot file-roller 
  firefox firefox-gnome-support fontconfig fontconfig-config g++ gcalctool 
  gcc gcc-4.1 gcc-4.1-base gconf-editor gdebi gdebi-core gdm gedit 
  gedit-common gettext-base gij gimp gimp-data gimp-print gimp-python gksu 
  gnome-about gnome-app-install gnome-applets gnome-applets-data 
  gnome-control-center gnome-games gnome-games-data gnome-keyring 
  gnome-keyring-manager gnome-mag gnome-media gnome-media-common 
  gnome-mount gnome-nettool gnome-orca gnome-panel gnome-panel-data 
  gnome-pilot gnome-power-manager gnome-screensaver gnome-session 
  gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-utils gnome-volume-manager gnupg gs-esp-x 
  gstreamer0.10-plugins-good gstreamer0.10-x gthumb gtk2-engines 
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap hpijs 
  hplip hplip-data human-theme iproute kaffeine kalarm katomic kbackgammon 
  kformula kmplot kpoker lftp libaspell15 libatspi1.0-0 libblkid1 
  libbonoboui2-0 libbonoboui2-common libcaca0 libcairo2 libcamel1.2-10 
  libcupsimage2 libcupsys2 libcurl3 libdjvulibre15 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 
  libenchant1c2a libespeak1 libexchange-storage1.2-3 libfontconfig1 
  libfreetype6 libgail-common libgail-gnome-module libgail18 libgcc1 
  libgcj-bc libgconf2.0-cil libgdiplus libgdl-1-0 libgimp2.0 libgksu2-0 
  libgksuui1.0-1 libglade2-0 libglade2.0-cil libglu1-mesa 
  libgnome-desktop-2 libgnome-keyring0 libgnome-media0 
  libgnome-window-settings1 libgnome2.0-cil libgnomecanvas2-0 
  libgnomecanvas2-common libgnomekbd-common libgnomekbd1 libgnomekbdui1 
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 
  libgnomevfs2-common libgnomevfs2-extra libgnutls13 libgtk2.0-0 
  libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19 libgtkspell0 
  libgucharmap6 libgutenprintui2-1 libhsqldb-java libhunspell-1.1-0 
  libicu36 libkrb53 liblaunchpad-integration0 liblpint-bonobo0 libmagick9 
  libmetacity0 libmusicbrainz4c2a libnautilus-burn4 libnautilus-extension1 
  libnotify1 libpam-modules libpanel-applet2-0 libpango1.0-0 libpt-1.10.0 
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librsvg2-2 
  librsvg2-common libscim8c2a libsdl-ttf2.0-0 libsexy2 libsigc++-2.0-0c2a 
  libsmbclient libsndfile1 libstdc++6 libtag1c2a libvte-common libvte9 
  libwmf0.2-7 libwnck-common libwpd8c2a libwps-0.1-1 libxfont1 libxft2 
  libxplc0.3.13 linux-headers-generic lshw metacity metacity-common 
  nautilus nautilus-cd-burner nautilus-data nautilus-sendto netbase 
  network-manager network-manager-gnome notification-daemon openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us 
  openoffice.org-impress openoffice.org-java-common 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer openssh-client 
  poppler-utils python-apt python-at-spi python-central python-glade2 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gtk2 python-gtkhtml2 python-notify python-uno 
  python-virtkey python-vte python2.5 python2.5-minimal qcad rhythmbox 
  rss-glx samba-common scim scim-gtk2-immodule scim-modules-socket 
  scim-modules-table scim-tables-additional scribus smbclient sound-juicer 
  ssh-askpass-gnome synaptic tomboy toshset totem totem-mozilla totem-xine 
  tsclient ttf-dejavu ttf-indic-fonts ubuntu-artwork ubuntu-desktop 
  update-notifier vino wireless-tools wvdial xfd xsane xsane-common 
  xserver-xorg xserver-xorg-core xserver-xorg-input-evdev 
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-video-all 
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-mga 
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion 
  xserver-xorg-video-sis xserver-xorg-video-tseng xserver-xorg-video-via 
  xserver-xorg-video-voodoo yelp zenity 
0 packages upgraded, 0 newly installed, 0 to remove and 376 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Frak on 2007-10-18
Try
```
sudo aptitude full-upgrade
```

---

### Post by DaraJava on 2007-10-18
dara@dara-laptop:~$ sudo aptitude full-upgrade
Unknown command "full-upgrade"
aptitude 0.4.4
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

---

### Post by DaraJava on 2007-10-18
What the heck are super cow powers anyway?

---

### Post by Frak on 2007-10-18
> **DaraJava said:**
> What the heck are super cow powers anyway?
Its a joke meaning nothing was done, so no super user privileges were needed.

---

### Post by DaraJava on 2007-10-18
Haha Thats good.

Do you have any ideas?

---

### Post by Frak on 2007-10-18
> **DaraJava said:**
> Haha Thats good.

Do you have any ideas?
None at the moment, I'm about to leave, but I'll think about it while I'm gone.

I just can't think of why it won't upgrade.

---

### Post by DaraJava on 2007-10-18
Ok thanks a million man. Talk to you later.

---

### Post by nikef on 2007-10-18
hope you get it 2 work,this is what i love about this site  :)

---

### Post by DaraJava on 2007-10-18
Yeah me too. This site is brill! Everyone helps so much and everyone is so friendly

---

### Post by Frak on 2007-10-18
try
```
sudo aptitude dist-upgrade
```

I'm going to try everything ;)

---

### Post by dynamethod on 2007-10-18
imo just wait till you get the live cd dude, ive upgraded to gutsy from fiesty and im finding ALOT of problems so far :S

---

### Post by DaraJava on 2007-10-18
Did what you said Frak. It took ages for the command you gave mo to finish what it was doing and when it finished it told me to restart. When it restarted the Ubuntu loading bar came on and loaded and then it went onto some text. it had the following format:


 * Starting/enabling/checking/running (Name of some program)...                            [ OK ]



This happens everytime I started Ubuntu. But this time the text just stayed there. I waited 10 mins then I restarted. The same thing happened the next time until it came to the text page. The text that I described above just flashed for a second and then I was asked my username and password in text mode. Now all I can do is enter stuff from the command prompt. I have no idea what to do. Any ideas?


P.S.

the last line of text on that page is

 * Running local boot scripts (/etc/rc.local)                            [ OK ]


P.P.S

Doesnt ask for username/password anymore just stays on page with all the writing

---

### Post by Frak on 2007-10-18
> **DaraJava said:**
> Did what you said Frak. It took ages for the command you gave mo to finish what it was doing and when it finished it told me to restart. When it restarted the Ubuntu loading bar came on and loaded and then it went onto some text. it had the following format:


 * Starting/enabling/checking/running (Name of some program)...                            [ OK ]



This happens everytime I started Ubuntu. But this time the text just stayed there. I waited 10 mins then I restarted. The same thing happened the next time until it came to the text page. The text that I described above just flashed for a second and then I was asked my username and password in text mode. Now all I can do is enter stuff from the command prompt. I have no idea what to do. Any ideas?


P.S.

the last line of text on that page is

 * Running local boot scripts (/etc/rc.local)                            [ OK ]


P.P.S

Doesnt ask for username/password anymore just stays on page with all the writing
type your login and password right after that.

That is a bug where "Login" does not appear. It still waits for input though.

---

### Post by DaraJava on 2007-10-19
I did that and it just goes to a CLI. I think it might just be to do with my video card driver but I don't know how to change that:confused:... Told you I was a n00b. Ah well ... A n00b in need is a n00b indeed.

---

### Post by Frak on 2007-10-19
> **DaraJava said:**
> I did that and it just goes to a CLI. I think it might just be to do with my video card driver but I don't know how to change that:confused:... Told you I was a n00b. Ah well ... A n00b in need is a n00b indeed.
I knew from the get-go that because it went to terminal, X failed. Run this command.
```
sudo dpkg-reconfigure xserver-xorg
```
Answer what it says, redownload the drivers if needed (just ask if you need help ;)), and it should work :)

---

### Post by oleoleole on 2007-10-19
About those super cow powers... try: apt-get moo

:p

---

### Post by DaraJava on 2007-10-20
apt-get moo....hiarious


I did what you said frak and it worked thanks a million. one problem though. When i go to reply in this forum firefox closes down after i type 3-4 letters. It doesnt happen in any other input boxes though. Dont know whats going on there. 

Oh and i have a good video card for my laptop but i cant get the 3d desktop effects. The video card is ATI and i know that that is quite waek in terms of drivers for linux but could you help me out on that? thanks a million.

Thank you so much for helping me on everything,

Dara.

---

### Post by Perfect Storm on 2007-10-20
If you're not addicted to firefox plugins I can recommend epiphany instead, it's fast lightweighted and well intergrated into the theme you're using on ubuntu. You can give it a spin and see if you like it;

```
sudo aptitude install epiphany-browser epiphany-extensions
```

---

### Post by DaraJava on 2007-10-20
> **Artificial Intelligence said:**
> If you're not addicted to firefox plugins I can recommend epiphany instead, it's fast lightweighted and well intergrated into the theme you're using on ubuntu. You can give it a spin and see if you like it;

```
sudo aptitude install epiphany-browser epiphany-extensions
```

Yeah it's nice. I'll try it out for a few days to see what I think. Cheers! :grin:

---

### Post by Frak on 2007-10-20
> **DaraJava said:**
> apt-get moo....hiarious


I did what you said frak and it worked thanks a million. one problem though. When i go to reply in this forum firefox closes down after i type 3-4 letters. It doesnt happen in any other input boxes though. Dont know whats going on there. 

Oh and i have a good video card for my laptop but i cant get the 3d desktop effects. The video card is ATI and i know that that is quite waek in terms of drivers for linux but could you help me out on that? thanks a million.

Thank you so much for helping me on everything,

Dara.
You could also try Swiftweasel, it is optimized for a certain processor arch's, though I can't guarantee it would give you a different result.

[http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

---

### Post by DaraJava on 2007-10-20
I'll try that, thanks. Can I just ask an unrelated question because i think the people here are well-informed of computers? 

If I take WEP encryption off my router and leave it publicly accessable will my laptop be accessable at all by any hackers at all? I'm just wondering because my friend says it could and if the only concern would be my neighbors stealing my wireless internet then I don't mind at all. 

Thank you,

Dara.

---

### Post by Frak on 2007-10-20
> **DaraJava said:**
> I'll try that, thanks. Can I just ask an unrelated question because i think the people here are well-informed of computers? 

If I take WEP encryption off my router and leave it publicly accessable will my laptop be accessable at all by any hackers at all? I'm just wondering because my friend says it could and if the only concern would be my neighbors stealing my wireless internet then I don't mind at all. 

Thank you,

Dara.
As long as you block all ports (they are by default), then you'll be fine 90% of the time. The other way is to filter requests to where your computer does NOT respond to requests. Then your compuer will be 100% safe because only your ISP and you will know that your computer is on the internet.

---

### Post by DaraJava on 2007-10-20
Hehe thats good enough for me. Thanks a mil.

---

