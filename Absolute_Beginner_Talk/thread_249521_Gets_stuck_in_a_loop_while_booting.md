---
title: "Gets stuck in a loop while booting"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by renesisspeed on 2006-09-02
Hi, I just installed ubuntu today and am completly new to linux.

Specs:
ubuntu 5.10
Toshiba Tecra 8000 laptop
P2 233
128mb ram
4gb hd

no nic
on external power

Ok so I just install ubuntu 5.10 today, after the install completed the system went through the boot sequence and to the login screen, at which point before i could even finish entering my user name it went back to the loading screen with the spinning cursor on the screen. After a minute or so it went back the login screen where i was able to finish entering my user name. I had to repeat this whole thing to enter my password, but before i could finish it said "login tim med out after 60 seconds"
So I rebooted hoping it would work, only to find that now every time it gets stuck in the boot sequence when it gets to the part saying "checking battery state.............[ok]"
Then it goes to a blank screen, then the loading screen then the boot screen IE "checking battery state.............[ok]" to repeat seemingly endlessly.

I really wanted to give this a shot but dont know what to do. So any help would be greatly appreciated. of course for all I know I cant even run it on such an old laptop. lol

thanks in advance
renesisspeed

---

### Post by nrwilk on 2006-09-02
5.10 is an older version.

You may want to try Dapper, which is version 6.06.

you can download a 6.06.1 iso here: [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

I'm not sure if this will help with your problem, but it certainly will not hurt to try it, if you have the time, bandwidth, and blank CDs around...

---

### Post by renesisspeed on 2006-09-02
the only reason i went with 5.10 is because 6.06 requires more minimum ram than I have and less hard drive space. from what I read laptops are supported, of course I dont know to what extent...

---

### Post by nrwilk on 2006-09-02
> **renesisspeed said:**
> the only reason i went with 5.10 is because 6.06 requires more minimum ram than I have and less hard drive space. from what I read laptops are supported, of course I dont know to what extent...

I'm running ubuntu 6.06.1 on a laptop right now.  Granted, there are several things that don't completely work.  But, it's better than running any other OS...

What are your laptop's specs?

---

### Post by renesisspeed on 2006-09-02
Specs:
ubuntu 5.10
Toshiba Tecra 8000 laptop
P2 233
128mb ram
4gb hd

no nic
on external power

 PS I just tried the 5.10 live boot cd and it worked fine....?

---

### Post by nrwilk on 2006-09-02
> **renesisspeed said:**
> Specs:
ubuntu 5.10
Toshiba Tecra 8000 laptop
P2 233
128mb ram
4gb hd

no nic
on external power

 PS I just tried the 5.10 live boot cd and it worked fine....?

Oh man!  I could have just looked at your first post.  Sorry!

Because you say that the live disk runs correctly, we know that your hardware is capable of running Gnome.  Did you run a checksum on the iso before you burnt the original disk?  It might have become corrupted during download.

---

### Post by renesisspeed on 2006-09-02
well, it installed fine so i would think it is fine, but.... 
I only have quick sfv, and when i downloaded the .iso file it didnt come with anything else(.sfv or otherwise)... how do i verify it?

---

### Post by nrwilk on 2006-09-02
> **renesisspeed said:**
> well, it installed fine so i would think it is fine, but.... 
I only have quick sfv, and when i downloaded the .iso file it didnt come with anything else(.sfv or otherwise)... how do i verify it?

Well, I've never done a checksum in Windows, so I'm not sure which programs are used for it.  I just did a google search and found several, though.  You can find a file with the correct checksum sequence on the same page where you downloaded the iso.

---

### Post by nrwilk on 2006-09-03
I also just thought of something else.  If you want to use ubuntu on an older system, you may have more success running xfce instead of gnome.  You can download an xubuntu install disk, or if you get your install working, you can download it very easily to replace gnome.

Xfce is a lot lighter and easier on your system resources.  A lot of people successfully use it on systems where Gnome and KDE won't run, or won't run quickly enough.

Just a thought I had.  I like it more than gnome too, and they look a lot alike.

---

### Post by renesisspeed on 2006-09-03
Well I havent had any luck with 5.10, so I installed 6.06 ubuntu and it works, but runs rather slow.
I was just reading about Xubuntu and was thinking about giving that a go. Hopefully It will run better..... :-)

---

### Post by nrwilk on 2006-09-03
to install it, just do this simple command:
```
sudo aptitude install xubuntu-desktop
``` 
Then, restart the computer (you could also restart the x-server by just hitting ctrl-alt-backspace).  At the GDM login screen, click on menu>sessions, and choose xfce.  When you restart the computer - or the x-server - GDM will default to the last DE (Gnome, XFCE, KDE, etc...) that you were using the last time you were logged in.  So, you should only have to select XFCE once.  Especially if you remove gnome.

To remove Gnome, issue this very long command:
```
sudo aptitude remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
``` 
Since you have limited disk space and Gnome runs slower on that machine, You'll probably want to remove gnome if you like xfce.

---

### Post by renesisspeed on 2006-09-03
ok, well granted I'm a total noob at terminal commands, but i tryed it and it said it couldnt find the package for xfce or something (this was with 6.06 ubuntu installed) . So i decided to try installing xubuntu 6.06 from scratch. I put the cd in and it launched to the live cd no problem, but any time i try to install it freezes up.

So in short, the only version Ive been able to get working is ubuntu 6.06 which runs rather slow. I would like to get either ubuntu 5.10 or xubuntu 6.06 working, but dont know what to do.

Ive messed around a little with other distros, but aside from these install problems ubuntu seems to be one of the easiest to use and has some of the lower system req's, so i would really prefer to stick with it rather than look for something else, and I'm not really ready to put linux on one of my desktops yet, so if anyone has a suggestion as to why i'm having this problem I would be very gratefull. thx
-renesisspeed

---

### Post by nrwilk on 2006-09-03
Don't give up on ubuntu yet.  There's still hope. :) 

> **renesisspeed said:**
> it said it couldnt find the package for xfce or something.

Can you please show us the command that you used and also the output it gave you?  This is the type of thing you will get asked for a lot.  The output almost always has some very helpful info on why the command didn't work.

The correct command is:```
sudo aptitude install xubuntu-desktop
```

Then after that finishes, and *ONLY after you've verified that xfce works*, you should remove Gnome to free space on your disk.

nrwilk

---

### Post by renesisspeed on 2006-09-03
that is exactly how I typed the command, but I am in the process of reinstalling ubuntu 6.06 so I'll have to wait and try it again to tell you exactly what it said. I'll post again as soon as it is done installing (will be a while as the cdrom on this dinosaur laptop is very slow)and try running "sudo aptitude install xubuntu-desktop" again.

---

### Post by nrwilk on 2006-09-03
> **renesisspeed said:**
> that is exactly how I typed the command, but I am in the process of reinstalling ubuntu 6.06 so I'll have to wait and try it again to tell you exactly what it said. I'll post again as soon as it is done installing (will be a while as the cdrom on this dinosaur laptop is very slow)and try running "sudo aptitude install xubuntu-desktop" again.

Sweet!  sounds good. :) 

nrwilk

---

### Post by renesisspeed on 2006-09-04
ok, I typed "sudo aptitude install xubuntu-desktop" and this is what it said

password*****
Reading package lists... done
building dependency tree... done
reading extended state information
initializing package states... done
building tag database... done
couldnt find any package whose name or description matched "xubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0b of archives. after unpacking 0b will be used.

---

### Post by nrwilk on 2006-09-04
I love how you learn when helping others.

hehe, so I didn't know this before but it seems that the xubuntu-desktop package in in the universe repository.  So, let's enable universe and multiverse, because this is probably something you'll want to do anyway.

First, backup your sources.list file.  This is the file containing the adresses of the repository servers.  to do this, issue this command:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
This will just make a duplicate file called "sources.list.backup"

Now, open the file to edit it:```
sudo gedit /etc/apt/sources.list
```
It will now open in an editor.

Copy all of the following text and replace the text in your file with it:
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Save the file and close gedit.

Now, go to the terminal and issue these commands:
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

It should then work.

nrwilk

---

### Post by renesisspeed on 2006-09-04
so I copy and pasted everything, and it didnt work. Unfortunatly the laptop it is on is not online so copying text over to a windows platform obscures things a bit. But this is what it said in terminal after editing the file and running the various commands.

bulltoad@ubuntu-TT:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
bulltoad@ubuntu-TT:~$ sudo gedit /etc/apt/sources.list
bulltoad@ubuntu-TT:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Temporary failure resolving 'archive.canonical.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
bulltoad@ubuntu-TT:~$ sudo aptitude install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "xubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
bulltoad@ubuntu-TT:~$


and here is what my sources.list file looks like now


[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by nrwilk on 2006-09-04
You've done everything correctly.  So, let's see if we can figure out what's going wrong.

Can you access the internet at all on the laptop under ubuntu?

Also, can you give us the output of this command:
```
cat /etc/resolv.conf
```

nrwilk

---

### Post by renesisspeed on 2006-09-04
it says no such file or directory :-(

and no, there is no network adapter on the laptop.
I downloaded a .bin installer from the xfce website and put it on a cd. I dont know if that will do me any good but....

---

### Post by nrwilk on 2006-09-04
> **renesisspeed said:**
> it says no such file or directory :-(

and no, there is no network adapter on the laptop.
I downloaded a .bin installer from the xfce website and put it on a cd. I dont know if that will do me any good but....

Doh! :mad: 

hehe, well that's the problem!

Using aptitude installs software from servers called repositories.  we had been trying to access these servers without a working internet connection.  hehe :-D

So, I'm not sure what you can do to get xfce on there short of installing it with the xubuntu disk.

If you have the xubuntu CD and already have ubuntu on the computer, there may be some way to use the xubuntu CD as a repository itself.  There can be local repositories in this way.  In fact, when you install ubuntu, the disk you install it from is automatically added to the list of repositories.

Unfortunately, I've never tried anything like that.  I always remove the CD repository as soon as I install, too.

Because we're pretty far off from the original thread topic now, I'd suggest starting a new thread which asks how to use the xubuntu CD as a repository on a ubuntu (Gnome) system.

I really hope we can get your setup running xfce.  I'm glad it works well (although slowly) with Gnome, though!

nrwilk

---

### Post by renesisspeed on 2006-09-04
ok, I got xubuntu to install using the "alternate" cd. :-D
and it runs better than ubuntu.

I would still kind of like to know why I couldnt get the others to work, but at least it is working.

Undoubtedly I'm going to have more questions as I get further into it. So thanks for all your help, and thanks for any future help. :-)

-renesisspeed

EDIT: 
Just read your last post, I had tryed seeing if I could use the xubuntu cd while I still had ubuntu installed, but since I know nothing about it I wasnt able to get it to work. Also I noticed the another person had problems with xubuntu live cd freezing while installing. It was suggested that they try the alternate cd as well. It worked for me so hopefully it worked for them as well.

---

