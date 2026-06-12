---
title: "How to make kubuntu faster like xp"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-26
i am a kubuntu user........

when i used windows xp in my amd athlon xp with nvidia geforce 2 card with system memory of 128mb(96+32mb videocard) my system works very fast ........but when i use kubuntu i feel the system is working too slowly ..........Can i make my kubuntu faster like xp by installing drivers for nvidia card and kernel for amd??????

If there any other suggestions please give me

i have already used prilinking technique, and faster drapper methods suggest any new methods to make my system work faster...........

i dont like to use xubuntu..........i need kubuntu itself

---

### Post by whizbaby on 2006-09-26
Think about it, because KDE is a ressource-hulking device.

---

### Post by aysiu on 2006-09-26
I would use *kde-core* instead of Kubuntu.

And, I don't think it would be terrible to install NVidia drivers. I don't think using the AMD kernel will make much of a difference, though.

You may also want to install and run *kpersonalizer* and turn off almost all the effects (except icon preview and wallpaper).

---

### Post by K.Mandla on 2006-09-26
There are some tips here that are not too difficult to perform.

[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

The part about a processor-specific kernel might help. I think you might want the linux-k7 kernel, but I'm not sure because I haven't had the chance to use an AMD in a while.

Have you installed the proprietary nvidia drivers (it's also in that post)? That will speed your video up considerably.

---

### Post by kurian on 2006-09-27
hi, i havnt installed the nvidia driver...

will the existing driver for nvidia will detect the video ram(in my case 32mb) automatically or will these 32mb will be detected only by using the original nvidia driver????

is it because of this reason my kubuntu system is slower than windows xp??????

will it be faster after installing the nvidia drivers..?????

One more thing to say in windows xp it says there is 96mb ram and there is about 30-45mb ram free....but in kubuntu it says your system has got only 91 mb ram and only nearly 2 mb is free....

any idea about this???

i want to run kubuntu faster like windows xp......??

---

### Post by whizbaby on 2006-09-27
> **kurian said:**
> will the existing driver for nvidia will detect the video ram(in my case 32mb) automatically or will these 32mb will be detected only by using the original nvidia driver????

is it because of this reason my kubuntu system is slower than windows xp??????

Don't think so, only need that for 3d.

---

### Post by kurian on 2006-09-28
Hi, any one knows how to make kubuntu work faster like xp.........??? iam a simple desktop user so i dont need many advanced kubuntu features any help please

---

### Post by whizbaby on 2006-09-28
Have you tried any of the above mentioned(e.g. *EDIT: use kpersonalizer,* install only kde-core, install chipset specific kernel)? Be a bit more verbose if you need help! Anyway, KDE is (following my experience) the slowest desktop so far. Last thing you could try is installing the latest KDE (3.5.4), which is said to be faster due to binary configuration files:
[http://www.kde.org/info/3.5.4.php](http://www.kde.org/info/3.5.4.php)

---

### Post by WalmartSniperLX on 2006-09-28
have you ever ran xp without any video drivers? its really slow. You should install your driver because right now you're letting your cpu do all the work in a process heavy environment (kde):D

---

### Post by kuja on 2006-09-28
> **kurian said:**
> i am a kubuntu user........

when i used windows xp in my amd athlon xp with nvidia geforce 2 card with system memory of 128mb(96+32mb videocard) my system works very fast ........but when i use kubuntu i feel the system is working too slowly ..........Can i make my kubuntu faster like xp by installing drivers for nvidia card and kernel for amd??????

If there any other suggestions please give me

i have already used prilinking technique, and faster drapper methods suggest any new methods to make my system work faster...........

i dont like to use xubuntu..........i need kubuntu itself

128mb RAM really isn't sufficient for running KDE, or GNOME either for that matter. 

The best way to improve your experience would be to simply add more RAM. 

You could get a 256MB stick for about $30, 512mb for about $60, or 2 512mb(dual channel) for around $110.

In my experience the proprietary Nvidia drivers have been a bit more stable, and faster even in 2d operations. One thing I noticed is that clicking+dragging to select things will seem really sluggish in KDE if you don't have the proprietary Nvidia driver installed.

---

### Post by ashokpappu on 2006-09-28
did u try stopping all un wanted services on ubuntu.  That would help

---

### Post by kurian on 2006-09-29
> **WalmartSniperLX said:**
> have you ever ran xp without any video drivers? its really slow. You should install your driver because right now you're letting your cpu do all the work in a process heavy environment (kde):D

hi,,, thanks for that good remark.... iam also dreaming that after i install the proper drivers the system will be faster....will soon install those drivers for nvidia..and will surely post the result

---

### Post by kuja on 2006-09-29
I'm still pretty convinced it's the RAM, kurian. You said you have 128MB, right? I experienced slowdowns even with 256MB of RAM. Popped in another 256MB stick and was amazed by the difference in speed! Like the difference between day and night.

---

### Post by kerry_s on 2006-09-29
Actually he said "96+32mb videocard" so you can bet he has less than 96mb since some is allocated to the cpu and 32mb vid memory is only for the vid.

Do you have swap?

I'm currently running openbox with konqueror, kinda a mini mini kde. It takes a little while to set up just right but i think it's what you need. I'm not saying it's going to be fast, but it will be faster than installing any kde. The problem is i'm not sure you know enough to do a sever+openbox+konqueror setup.

I'll run through the procedure, just in case you get brave.

1. Grab a copy of the alternate cd(if you don't all ready have one)
2. Install the server(which is just the base,no gui)
3. login and do> sudo su <that makes you root
4. nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos(they start with "deb")
ctrl and x and y and enter to save
5. apt-get update
6. apt-get install x-window-system-core xterm gdm konqueror konsole kate synaptic openbox obconf menu menu-xdg
7. run> update-menus
8. run> reboot
9. select openbox in session and login(should be gui now)
10. right click the desktop

11. If you got this far the hard parts over you just got to set it all up now, which takes time. You can start the kde stuff from terminal. But you will still need to setup so that everything starts when you log in.

Kde stuff to run in terminal->

kicker
kdesktop

12. go to /usr/share/xsessions and right click openbox.desktop select actions> edit as root

13. Where it says> Exec=openbox <we want to change that to> Exec=/home/(user)/.xsession <user will be your name

14. Press the home button and view>show hidden files

15. right clck> create new> text file
name it .xsession
put this in it

```
#!/bin/sh

kicker &
kdesktop &
kdeinit &

exec openbox 

```

now close and save and right click it>properties>permissions> check "Is executable" to make it executable.

Okay that's all i can think of right now, there are some things i'm still trying to work out, like the logout button not working so i had to make one that works or use the openbox menu.

You'll have to come back with questions for things i didn't mention. ;) I tried to include a pic but i keep getting this error->
Fatal error: Direct Instantiation of vB_Image_Abstract prohibited. in /includes/class_image.php on line 188

Here's a pic->  [http://img241.imageshack.us/img241/2063/snapshotlw4.jpg](http://img241.imageshack.us/img241/2063/snapshotlw4.jpg)

---

### Post by sbergman27 on 2006-09-29
To be honest, I'm surprised it is usable at all with 96MB main memory.  If the memory partitioning could be changed, that might help some.

I really don't see how any tweaks are going to make it fast, though.

Adding memory is the right thing to do.

I know he said he didn't like Xubuntu, but with 96MB ram, I would *seriously* consider it.

---

### Post by kurian on 2006-09-30
> **sbergman27 said:**
> To be honest, I'm surprised it is usable at all with 96MB main memory.  If the memory partitioning could be changed, that might help some.

I really don't see how any tweaks are going to make it fast, though.

Adding memory is the right thing to do.

I know he said he didn't like Xubuntu, but with 96MB ram, I would *seriously* consider it.

The reason i said i dont like to use xubuntu is because as everyone knows its less functional...

Iam insisting on kubuntu OS because if XP works really fast in my computer with 96mb+32mb(for video card)  then why should not kubuntu also work in the same manner .....Also iam a newbie in linux OS so simply for trying with kubuntu i am not ready to waste the money for upgrading ram since xp works well in my system .....I only demand the opensource community to place a speed matching with that of the windows and nothing more than that....

---

### Post by aysiu on 2006-09-30
Every time I've seen XP on a computer with less than 512 MB of RAM, it's moved like molasses. You must have some freaky computer for anything but Fluxbox or Windows 95 to "work really fast" on 96 MB of RAM.

---

### Post by Karlos on 2006-09-30
kurian, 
You need to understand that linux uses ram in a different way to windows. windows only puts in the ram the files it needs to open a particular program after working out what it can already use out of the files already in the ram. Thats why you have to defrag and its also how viruses can spread. linux shelves things in a different way and hense does need more ram.
the cost of a new stick of ram is not much and it will make a massive difference...

---

### Post by kurian on 2006-09-30
> **aysiu said:**
> Every time I've seen XP on a computer with less than 512 MB of RAM, it's moved like molasses. You must have some freaky computer for anything but Fluxbox or Windows 95 to "work really fast" on 96 MB of RAM.

but beleive me xp works really fine in my system....i havent experienced any problem , the applications pop up faster ....

---

### Post by aysiu on 2006-09-30
Fast*er* I can believe. *Fast* on 96 MB of RAM I'd have to see in person to believe.

That said, have you tried any of the suggestions given?

My earlier suggestion was to use *kde-core* (basic KDE) instead of *kubuntu-desktop* (Ubuntu's default KDE). Someone else suggested installing NVidia drivers.

Installing NVidia drivers is easy:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

Replacing *kubuntu-desktop* with *kde-core* is a bit more complicated, though. The easi*est* way I can think to do this would be to remove *kubuntu-desktop* completely and then install *kde-core*.

Launch up Kate (the text editor) and paste this code in the document: ```
#/bin/bash
sudo /etc/init.d/kdm stop
sudo apt-get remove acpi acpi-support acpid adept akregator amarok anacron apmd ark arts bc bicyclerepair bluez-cups bluez-pcmcia-support bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libstdc++5 libxp6 min12xxw mkisofs openoffice.org openoffice.org-kde pbbuttonsd pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
sudo aptitude update
sudo aptitude install kde-core
sudo /etc/inid.d/kdm restart
``` Then save the document in your home directory as *minimalkde.sh*

Log out of KDE and press Control-Alt-F1

This will bring you to a terminal mode. Log in. Then type these commands: ```
chmod +x minimalkde.sh
./minimalkde.sh
``` Watch the sparks fly. By the end, you should be back in graphical mode. If not, press Control-Alt-F7 to get back there.

Log in again. A wizard called KPersonalizer should run the first time you log into KDE. For effects, disable everything except wallpaper and image previews.

Should be a lot faster.

---

### Post by sbergman27 on 2006-09-30
> **aysiu said:**
> Fast*er* I can believe. *Fast* on 96 MB of RAM I'd have to see in person to believe.

Me too.  And to that end, I'm going to try this.  Sounds like a fun  little Saturday project.

I'm sure you already know this, but for those who don't, appending:

mem=96M

to the boot string will force the kernel to use only that much memory.  Great for simulating  a low memory machine.

I'll let you all know what I find out.

---

### Post by mips on 2006-09-30
To install nVidia or ATI drivers rather look at this thread, [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

I don't think there is an easier way of installing the drivers than the above guide by tseliot.

---

### Post by sbergman27 on 2006-09-30
Well, it's been an interesting morning.  I installed kubuntu-desktop and xubuntu desktop on to my fully updated Ubuntu Edgy laptop.

Machine specs:

Sempron 3000+
768MB RAM (but restricted to 96MB for these tests)
40GB Harddrive

I appended "mem=96M" to the boot string in grub to restrict it to using only 96MB of the RAM.

Measuring desktop performance is a bit of a black art.  How to measure responsiveness?  So I took the easy way out and decided on a couple of simple task that pretty much everyone performs:

1. Logging in.
2. Logging in and bringing up a browser.

So, for each desktop, I logged in twice and recorded the time for the second login.

I then repeated the test, but as soon as the desktop was to a point that I could click to bring up a browser, I started a browser.  Again, the whole login, start up browser cycle was repeated twice and the second timing was recorded.

For the browser tests, I tried with 2 different browsers for each desktop:

1. The default browser for the desktop environment.
2. Firefox 2.0 as shipped with the current Edgy.

So for KDE, I used Konqueror and FF.
For Gnome I used Epiphany and FF.
For XFCE I used Epiphany and FF.

Note that XFCE doesn't have a default browser, but even dragging in the requisite Gnome libs, Epiphany managed to beat out FF by a hair.

All desktops are at pretty much the default settings.  For KDE, I did set the desktop effects to minimum for best performance, but that's about it.  The browser home page, in all cases, was set to [www.google.com](www.google.com).  In all cases, I timed until the desktop and/or app was completely up, and hard drive activity had stopped.

Here are the results.  All times are reported in seconds:

```

XFCE Desktop Only  : 6
XFCE Epiphany      : 40
XFCE Firefox       : 42

Gnome Desktop Only : 27
Gnome Epiphany     : 61
Gnome Firefox      : 64

KDE Desktop Only   : 82
KDE Konqueror      : 138
KDE Firefox        : 170

```

Comments:

XFCE *rocks* for low memory machines.  I used each desktop for a bit just to get a feel for how it would be to use in 96MB.  Of the three desktops, XFCE was the *only* one that seemed zippy, even fun, to use.  The log in time of only 6 seconds was amazing.  During the second run, there was almost *no* disk activity required.  I used XFCE for a few weeks, a while back, and was impressed with its features, though I had to do a bit more digging than with Gnome to find the best way to do things.  But the functionality packed into that small footprint is impressive.   If my machine were at all memory constrained I would still be using it.

Gnome was OK.  I definitely wouldn't call it fun.  But it was pretty usable.  It actually did much better than I was expecting.  In the last few releases, reduction of memory usage has been a major goal, and I'd say they've made some progress. I know that 2.8 would not do as well as 2.16 did.

In 96MB, KDE was a bit of a performance disaster, taking almost 3 minutes(!) to log in and bring up Firefox. (These times do *not* include the boot time.)  In one case, Konqueror was not able to bring up the google home page, but instead gave a message that something had died unexpectedly, though I suspect it actually timed out.  

So, based upon this limited benchmark, I would say that Kubuntu is probably the least appropriate desktop for a machine so severely memory constrained as this, there being about a 3 fold difference between it and Gnome, and a 4 to 14 fold difference with XFCE in this particular set of tests.

---

### Post by easyease on 2006-09-30
thanks for that research sbergman! i found that interesting, from my experience ubuntu has been faster without a k in front of it, Ive never tried xubuntu though so Illl bear your research in mind for future.
 I shall also repeat what has already been advised to the original poster.........get more ram, ya know it makes sense.

---

### Post by aysiu on 2006-09-30
Kubuntu is slower than Ubuntu, but that doesn't mean KDE is slower than Gnome.

I would highly advise, if you like KDE, to install *kde-core* instead of *kubuntu-desktop*, which is what I also advised the original post-er.

---

### Post by sbergman27 on 2006-09-30
> **aysiu said:**
> Kubuntu is slower than Ubuntu, but that doesn't mean KDE is slower than Gnome.

I would highly advise, if you like KDE, to install *kde-core* instead of *kubuntu-desktop*, which is what I also advised the original post-er.

I'll test that in a while.  At this point, I really should do a Xubuntu install and then just install kde-core on top of that, I think, to make sure I've gotten rid of all the Kubuntu-desktop stuff.  Do you agree?

---

### Post by aysiu on 2006-09-30
Or you could just do this: ```
sudo apt-get remove acpi acpi-support acpid adept akregator amarok anacron apmd ark arts bc bicyclerepair bluez-cups bluez-pcmcia-support bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libstdc++5 libxp6 min12xxw mkisofs openoffice.org openoffice.org-kde pbbuttonsd pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
sudo aptitude update
sudo aptitude install kde-core
``` By the way, both [Nalmeth](http://ubuntuforums.org/member.php?u=52561) and I have found *kde-core* to be faster than *kubuntu-desktop*. So if you did as well, that would be three people.

---

### Post by sbergman27 on 2006-09-30
> **aysiu said:**
> Or you could just do this:

Benchmarks are notorious for being strongly affected by things one didn't think about... and my laptop is stateless.  I'll do the fresh install and compare kde-core with gnome-core + epiphany.

Of course, it should be stressed that this is all at 96MB and can't be extrapolated past that.

---

### Post by Josh1 on 2006-09-30
> **WalmartSniperLX said:**
> have you ever ran xp without any video drivers? its really slow. You should install your driver because right now you're letting your cpu do all the work in a process heavy environment (kde):D

Exactly. And I wouldn't use kubuntu for sucha  low setup ;).

---

### Post by aysiu on 2006-09-30
I'm not sure what Nalmeth's specs were, but I've tried *kde-core* on both 128 MB of RAM (766 MHz processor) and 512 MB of RAM (2.1 GHz processor), and in both cases, it's been significantly faster than *kubuntu-desktop*--several seconds faster to load GTK applications.

I didn't compare it to *gnome-core* because I was just interested in seeing how fast I could get KDE.

---

### Post by rccharles on 2006-09-30
> **kurian said:**
> 
Iam insisting on kubuntu OS because if XP works really fast in my computer with 96mb+32mb(for video card)  then why should not kubuntu also work in the same manner .....Also iam a newbie in linux OS so simply for trying with kubuntu i am not ready to waste the money for upgrading ram since xp works well in my system

I thought that 128meg was required for Windows XP.  Most people would say 256meg is the minium anyway.

Your painting yourself into a corner by saying you do not want to add memory.

.....> **kurian said:**
> I only demand the opensource community to place a speed matching with that of the windows and nothing more than that....
As they say, you are not comparing apples to apples here. 

Windows XP came out in 2001 whereas you are using a 2006 version of Ubuntu.  

A newer operation system will use more fancy graphics.  To make a comparison, you would need to use a more robust desktop environment. 

Windows will have a fast video driver.  Have you installed a fast Linux video driver?

Development is costly.  Windows Vista will require 1gig of memory.  Ubuntu needs to compete with Windows Vista not Windows XP.  You should be thinking you are getting a Windows Vista competor, Ubuntu, running in only 96 + 32 meg of memory.

Robert

---

### Post by aysiu on 2006-09-30
According to Microsoft: > **128 megabytes (MB) of RAM** or higher recommended (64 MB minimum supported; may limit performance and some features) [http://www.microsoft.com/windowsxp/home/upgrading/sysreqs.mspx](http://www.microsoft.com/windowsxp/home/upgrading/sysreqs.mspx)

According to Ubuntu: > Table 1 Recommended Minimum Requirements

Install Type
	

RAM
	

Hard Drive Space

Desktop
	

**256 megabytes**
	

3 gigabytes

Server
	

64 megabytes
	

500 megabytes  [http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

If you want 96 MB of RAM to work quickly, you should use XFCE at the very least, but more likely Fluxbox or IceWM will suit your needs. Even with a light window manager like IceWM, you can still have "modern" applications like Thunderbird, Firefox, F-Spot, Rhythmbox, etc.

---

### Post by kinematic on 2006-09-30
> **whizbaby said:**
> Think about it, because KDE is a ressource-hulking device.

gnome actually uses more resources then kde :mrgreen:

---

### Post by aysiu on 2006-09-30
One thing I will say:

People's generalizations about Gnome and KDE are usually meaningless--based on personal experience on one computer (sample size = 1) and with a particular distro's implementation of the DE.

Not always, but usually, that's the case. Some people--not many--have tried both KDE and Gnome in various distro flavors on different computers.

KDE in Mepis is much faster than Kubuntu, I've found. Some people claim that SuSE's Gnome is faster than Ubuntu's Gnome (I haven't used SuSE lately, so I don't know if this is true). I've found that *kde-core* tends to be faster than *kubuntu-desktop*, and I'd imagine *gnome-core* is similarly faster than *ubuntu-desktop*.

The default installations for Ubuntu and Kubuntu seem to have a lot of random services running--Bluetooth and a lot of laptop support services, which are both useless to me (I don't use Bluetooth, and I use a desktop computer).

---

### Post by sbergman27 on 2006-09-30
OK.  Get ready for this. I installed Xubuntu Edgy Beta 1 and updated.  I installed kde-core and gnome-core and reran the test using the same procedure outlined in my previous post.  I went through and turned off all the services I don't need.  I can't guarantee they were exactly the same services I had running before, but it should be pretty close.  The results are, indeed, quite different.

```

XFCE Desktop Only: 7
XFCE Firefox     : 31
XFCE Epiphany    : 29

Gnome-Core Desktop Only: 19
Gnome-Core Firefox     : 44
Gnome-Core Epiphany    : 43

KDE-Core Desktop Only  : 9
KDE-Core Konqueror     : 15
KDE-Core Firefox       : 32

```

Comment:

Kubuntu-desktop *sucks* for low memory machines.  KDE-Core *rocks*.  
At least according to this metric.
I'm impressed.  And I'm a Gnome fan.

---

### Post by tacubuntuforums on 2006-09-30
I wonder how you managed to install kubuntu.
I wasn't even able to use the Drapper Drake Ubuntu CD fine (and here people say kubuntu uses more memory). It was very slow and at the 3rd step, or so, of the install process it stoppped, it couldn't go furhter. All this happened in a Dell, Pentium 4, 256MB RAM.
Afeter buying a 500MB RAM Card for my sister's PC, everything went over wheels.
But now I read that maybbe I should use nvidia's driver's. I remember that PC used an Nvidia video card.
Are you people shure about the convenience of downloading and istalling those drivers.
Could you, please, write me a brief explanation of all the process I should follow to do that.

---

### Post by sbergman27 on 2006-09-30
> **tacubuntuforums said:**
> I wonder how you managed to install kubuntu.

Well, in the first set of tests, I had installed Ubuntu previously (with 768MB ram).  I installed xfce and kubuntu-desktop with synaptic. (With 96MB.  It was slow but it worked.)

I ran the tests with 96MB.

In the second instance I installed Xubuntu (with 768MB).  Then I installed kde-core and gnome-core, rebooted into 96MB and ran the tests.

If I had a machine that really and truly only had 96MB here is what I would do:

1. Install in text mode from the Xubuntu Alternate CD.  The alternate cd will install with less memory than the standard Xubuntu CD, and is faster and more flexible. (I believe they say it will install in "less than 128MB" of ram.

2. Then I would apt-get kde-core.

3. I would also stick to kde and qt apps *only* where possible.  Mixing in gtk2 apps is going to mean that qt, kde, and gtk2 libs are going to have to be loaded.  Sticking with KDE and QT apps should be most efficient.

Be warned that the Xubuntu alternate install CD seems to be broken for Xubuntu Edgy Beta.  It blew up chrooting to the new root filesystem during the install.  But Xubuntu Dapper should be fine.

---

### Post by kurian on 2006-09-30
hi, it seems that most of you really took installing kubunut in 96mb + 32mb environment with a little surprise.........but its true....

first of all i need to know whats the basic difference between kde-desktop and kde-core...

if kde-core could perform well then how could i convert my existing installation to kde-core i only have a live cd with me no alternate cd....

---

### Post by tacubuntuforums on 2006-09-30
> **Karlos said:**
> kurian, 
You need to understand that linux uses ram in a different way to windows. windows only puts in the ram the files it needs to open a particular program after working out what it can already use out of the files already in the ram. .......

Karlos,
This sounds interesting. Could you, please, explain this clearer and with more detail. Thanks

---

### Post by drivel on 2006-09-30
It is said that edgy will be faster than Dapper Drake

---

### Post by tacubuntuforums on 2006-09-30
> **aysiu said:**
> Fast*er* I can believe. *Fast* on 96 MB of RAM I'd have to see in person to believe.

That said, have you tried any of the suggestions given?

My earlier suggestion was to use *kde-core* (basic KDE) instead of *kubuntu-desktop* (Ubuntu's default KDE). Someone else suggested installing NVidia drivers.

Installing NVidia drivers is easy:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

Replacing *kubuntu-desktop* with *kde-core* is a bit more complicated, though. The easi*est* way I can think to do this would be to remove *kubuntu-desktop* completely and then install *kde-core*.

Launch up Kate (the text editor) and paste this code in the document: ```

#/bin/bash
sudo /etc/init.d/kdm stop
sudo apt-get remove acpi acpi-support acpid adept akregator amarok anacron apmd ark arts bc bicyclerepair bluez-cups bluez-pcmcia-support bluez-utils bogofilter brltty cdparanoia cdrdao cdrecord cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dc diveintopython doc-base doc-debian dvd+rw-tools example-content foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod gs-esp gtk2-engines-gtk-qt gwenview hal hotkey-setup hplip hplip-ppds irssi k3b kaddressbook kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin landscape-client language-selector-qt lftp libarts1-akode libgl1-mesa libglut3 libnss-mdns libpam-foreground libsasl2-modules libstdc++5 libxp6 min12xxw mkisofs openoffice.org openoffice.org-kde pbbuttonsd pmount pnm2ppa powermanagement-interface powernowd python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-unit python-xdg python-xmpp python2.4-dbus python2.4-dictclient python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-pycurl qca-tls readahead scim-qtimm screen skim slocate smbclient speedcrunch ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bitstream-vera ttf-dejavu ttf-freefont ttf-gentium ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-thai-tlwg unzip usplash vorbis-tools wlassistant wvdial x-ttcidfont-conf x-window-system-core xcursor-themes xkeyboard-config xserver-xorg-input-synaptics xterm zip
sudo aptitude update
sudo aptitude install kde-core
sudo /etc/inid.d/kdm restart
``` Then save the document in your home directory as *minimalkde.sh*

Log out of KDE and press Control-Alt-F1

This will bring you to a terminal mode. Log in. Then type these commands: ```
chmod +x minimalkde.sh
./minimalkde.sh
``` Watch the sparks fly. By the end, you should be back in graphical mode. If not, press Control-Alt-F7 to get back there.

Log in again. A wizard called KPersonalizer should run the first time you log into KDE. For effects, disable everything except wallpaper and image previews.

Should be a lot faster.


Also, Aysiu, I'm interested in your post.
I understand it, but I'd like to know how did you reach that solution as I may want to use it in several occasions. More exactly:
1) How did you build the list of packages to remove?
2) How to go the way back (unistall kde-core and place back kubuntu-desktop) [kde-core is kde? I thought there was only one kde,one gnome, etc. So there are different versions of the "same" desktop too?
3) How is that done 'in general', for any desktop change?

Finally, after all what is being said here, I wonder what are the advantages of kubuntu then.

---

### Post by sbergman27 on 2006-10-01
> **tacubuntuforums said:**
> 
1) How did you build the list of packages to remove?
2) How to go the way back (unistall kde-core and place back kubuntu-desktop) [kde-core is kde? I thought there was only one kde,one gnome, etc. So there are different versions of the "same" desktop too?
3) How is that done 'in general', for any desktop change?

Finally, after all what is being said here, I wonder what are the advantages of kubuntu then.

In synaptic, you can rightclick on a package and select properties.  There is a tab that will show the dependencies.  I think that's where the list comes from .

(Can you really remove all that without apt complaining about packages that depend upon some of those?)

There is only one KDE, but there are different ways to package and configure it.  The Kubuntu-desktop is (obviously) heavier and runs more stuff by default.  I *think* kde-core is the default confiuration from the kde project with little or no modification.

As to what Kubuntu is good for, remember that we're focusing on low memory here.  I don't use Kubuntu, but one would assume that the extra stuff that gets loaded is good for something when you have 256MB or more of memory.

---

### Post by kurian on 2006-10-01
hello , i have installed the nvidia drivers too but the speed remains same...

i Think the reason is too much of consumption of memory when iam using windows xp in my system (96 + 32 mb) it shows a 40mb free physical ram

but now in kubuntu it shows that you are having only 2mb freee what a drastic difference why is it so is there any process running that draws memory ....

---

### Post by sbergman27 on 2006-10-01
> **kurian said:**
> but now in kubuntu it shows that you are having only 2mb freee what a drastic difference why is it so is there any process running that draws memory ....

This is a very common misunderstanding.  Linux dynamically uses any free memory for the disk cache to speed up access to recently used file data.  When that memory is needed for programs it is automatically freed for use.

The "buffer" and "cache" values that you see in, e.g., the output of the "free" command, represent cached filesystem data.

Free memory is wasted memory, so Linux always tries to put it to use.  So "free memory" as reported by system tools is always going to be low.  You have to remember that buffer and cache are as good as free.

Memory that has been allocated, but not recently used goes to "swap" on disk, to free up real ram for better use.

Linux tries to balance program memory, disk cache, and swap for best performance.

Does that make sense?

---

### Post by rexd on 2006-10-01
:confused: I have filled in the last box with access number name and password but there seems to be no way to conect to the internet. several Icons ae grayd out, Could you please tell me what to do to activate the internet? ](*,) 
The must be an icon or two to do this but there are no instructions.
[email]rexd@istnet.net.au[/email]

---

### Post by sbergman27 on 2006-10-01
> **rexd said:**
> :confused: I have filled in the last box with access number name and password but

You probably want to start a new thread for this.

At the top of the "Absolute Beginner Talk" forum, click "New Thread".  Buried in this thread, you might not be noticed.

---

### Post by tacubuntuforums on 2006-10-02
Thank you sbergman27

But I still don't understand  how to build that list of packages to remove a desktop. You mean a desktop is only one package and I should see which packages depend on it (need it)? because the dependencies work the other way round, don't they?. I mean, for one package you can see what packages it needs to operate, but not what packages need it.

One question about booting with low mem for tests:
If I have grub intalled, I boot with grub showing me the menu list of OS options (to choose which to boot with), how can I boot one of those linux options with low memory? I tried inserting a line "mem=250" to the lines that correspond to the Linux option I use most in the menu list, and then pressed b to boot using that extra line but it booted with all the memory.


> **sbergman27 said:**
> This is a very common misunderstanding.  Linux dynamically uses any free memory for the disk cache to speed up access to recently used file data.  When that memory is needed for programs it is automatically freed for use.

The "buffer" and "cache" values that you see in, e.g., the output of the "free" command, represent cached filesystem data.

Free memory is wasted memory, so Linux always tries to put it to use.  So "free memory" as reported by system tools is always going to be low.  You have to remember that buffer and cache are as good as free.

So to know what part of the memory is actually needed we must substract the cache and buffer (too?) to the used memory?

> **sbergman27 said:**
> Memory that has been allocated, but not recently used goes to "swap" on disk, to free up real ram for better use.

Linux tries to balance program memory, disk cache, and swap for best performance.

Does that make sense?

I thought the swap was only used when the ram was full and the system needed more memory (or that's what you also mean?)

---

### Post by tacubuntuforums on 2006-10-02
KURIAN?

May I ask you...
How much memory does your Windox XP antivirus needs?
How much memory your browser (Iexplore?) needs?
My antivirus for Wini2000 is quite heavy and needs something between 60 and 100 MB.
Just my desktop background-image, in a Debian distro, is 1.1MB. That's 2% of what your system uses?

Are you stating that your WinXp needs only 56MB of RAM???
Could you tell us how much memory does Microchoff suggest you use for your WinXP edition?

Maybe you're running Win95.
Once my sister was using 96MB or so for a Win2000 instal and it was vveery sloooww.

If you want to see the memory that the kubuntu (as well as your windos) processes are using, use the System monitor (like in windi). There, you can sort them by memory use.
I don't know kubuntu, but maybe you have a mai deamon, mai server o mail alerts;

---

