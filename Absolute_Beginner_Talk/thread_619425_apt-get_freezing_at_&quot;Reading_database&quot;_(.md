---
title: "apt-get freezing at &quot;Reading database&quot; (reinstall Ubuntu?)"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Aquilastudio.com on 2007-11-21
My apt-get downloads the file nicely but when it comes to
 (Reading Database...
 it never finishes reading it. I cant install anything please help.!!!!!!!!!!!!!!!!!!!!!!!!!!!!



:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by Aquilastudio.com on 2007-11-21
My Apt-get Works Until It Reaches: 

(reading Database...

Then It Freezes! Help Me Please

---

### Post by Aquilastudio.com on 2007-11-21
After I installed gusty, apt-get began stopping at 
(Reading Database... 
please help:(:(:(

---

### Post by Inxsible on 2007-11-21
Be patient. Don't start new threads every 15 mins. You already have 3 threads now

[http://ubuntuforums.org/showthread.php?t=619425](http://ubuntuforums.org/showthread.php?t=619425)

[http://ubuntuforums.org/showthread.php?t=619417](http://ubuntuforums.org/showthread.php?t=619417)

---

### Post by overdrank on 2007-11-21
> **Aquilastudio.com said:**
> After I installed gusty, apt-get began stopping at 
(Reading Database... 
please help:(:(:(

Also paste the output of the terminal and tell us what you are trying to install.

---

### Post by Aquilastudio.com on 2007-11-21
sudo aptitude install xserver-xorg-core
[sudo] password for alexander:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libglitz-glx1 libglitz1 
The following packages have been automatically kept back:
  compiz-core compiz-gnome compiz-plugins karbon kchart kdelibs-data 
  kdelibs4c2a kexi kformula kivio kivio-data koffice-data koffice-libs 
  koshell kplato kpresenter kpresenter-data krita krita-data kspread 
  kthesaurus kugar kword kword-data libc6-dev libdecoration0 libflac++6 
  libpng12-0 libqt3-mt linux-restricted-modules-common 
The following packages have been kept back:
  bittorrent capplets-data compiz cupsys cupsys-bsd cupsys-client 
  cupsys-common eog evince evolution evolution-common evolution-data-server 
  evolution-data-server-common evolution-plugins file-roller firefox 
  firefox-gnome-support gcalctool gdm gedit gedit-common ghostscript 
  ghostscript-x gnome-about gnome-cards-data gnome-control-center 
  gnome-desktop-data gnome-games gnome-games-data gnome-menus gnome-panel 
  gnome-panel-data gnome-screensaver gnome-session gnome-system-monitor 
  gs-common gs-esp gs-esp-x gtk2-engines gtkhtml3.14 hwdb-client-common 
  hwdb-client-gnome koffice libc6 libc6-i686 libcamel1.2-10 libcupsimage2 
  libcupsys2 libcupsys2-dev libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 
  libegroupwise1.2-13 libexchange-storage1.2-3 libflac8 libgnome-desktop-2 
  libgnome-menu2 libgnome-window-settings1 libgnomeui-0 libgnomeui-common 
  libgs8 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common 
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpoppler-glib2 
  libpoppler-qt2 libpoppler2 libsmbclient libssl0.9.8 libwnck-common 
  libwnck22 linux-restricted-modules-2.6.22-14-generic openssl 
  poppler-utils python-bittorrent python-gmenu samba-common smbclient 
  sound-juicer svgatextmode ubufox xorg-driver-fglrx 
0 packages upgraded, 0 newly installed, 2 to remove and 118 not upgraded.
Need to get 0B of archives. After unpacking 344kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 



BUT THIS HAPPENS FOR ALL INSTALATIONS

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> My Apt-get Works Until It Reaches: 

(reading Database...

Then It Freezes! Help Me Please

That's not much information. What was the last program you tried to install?

Try 

> sudo apt-get clean

and see if you can run an 

> sudo apt-get update

after.

---

### Post by Aquilastudio.com on 2007-11-21
I still need help! Please reply!!!!!!!

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> I still need help! Please reply!!!!!!!

There is a response in your other thread.

This is a very responsive community, but you also need to do some legwork yourself, and be patient.

---

### Post by stroyan on 2007-11-21
Try[LIST]
[*]sudo apt-get check
[*]sudo apt-get clean
[*]sudo apt-get install -f
[/LIST]

---

### Post by Aquilastudio.com on 2007-11-21
I ran both of your commnads and they worked but I already tried these and they do nothing. The last instalation I ran was i forget

---

### Post by mellowd on 2007-11-21
Then try another app and post the output

---

### Post by Aquilastudio.com on 2007-11-21
sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
alexander@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.
alexander@ubuntu:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alexander@ubuntu:~$ su
Password: 
root@ubuntu:/home/alexander# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
The following packages will be REMOVED:
  libglitz-glx1 libglitz1
0 upgraded, 0 newly installed, 2 to remove and 118 not upgraded.
Need to get 0B of archives.
After unpacking 344kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 

I have been trying this for a month now but I still dont have a solution. Please help

---

### Post by Aquilastudio.com on 2007-11-21
root@ubuntu:/home/alexander# sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  compiz
1 upgraded, 0 newly installed, 0 to remove and 117 not upgraded.
Need to get 31.7kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main compiz 1:0.6.0+git20071008-0ubuntu1.1 [31.7kB]
Fetched 31.7kB in 1s (22.6kB/s)
(Reading database ...

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> I ran both of your commnads and they worked but I already tried these and they do nothing. The last instalation I ran was i forget

Next step:

> dpkg configure -a

I would break out aptitude at this point, and see what file is holding up the update.

---

### Post by Aquilastudio.com on 2007-11-21
I did this command. But how do I do that thing with aptitude?

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> I did this command. But how do I do that thing with aptitude?

So that command came up with nothing?

---

### Post by Aquilastudio.com on 2007-11-21
This is what happened:

root@ubuntu:/home/alexander# dpkg --configure -a
root@ubuntu:/home/alexander#

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> I have been trying this for a month now but I still dont have a solution. Please help

Reinstall. 

Seriously. If you have been researching this for a month, and still it is not fixed, then back your files up and do a clean install.

---

### Post by justin whitaker on 2007-11-21
> **Aquilastudio.com said:**
> This is what happened:

root@ubuntu:/home/alexander# dpkg --configure -a
root@ubuntu:/home/alexander#

According to your other thread, you have had this issue for a month. I would back your files up, and do a clean install.

---

### Post by Aquilastudio.com on 2007-11-21
How do I do that?

---

### Post by Aquilastudio.com on 2007-11-21
Please Reply!

---

### Post by Aquilastudio.com on 2007-11-21
I still need help?

Can it have anything to do with repristories?

If i reinstall apt- get will it help?

If so how do i do it?

---

### Post by Aquilastudio.com on 2007-11-21
How can I reinstall ubuntu without loosing anything. 99% risk-free please.

---

### Post by Aquilastudio.com on 2007-11-21
I still need help please!!!!!

---

### Post by az on 2007-11-21
> **Aquilastudio.com said:**
> How can I reinstall ubuntu without loosing anything. 99% risk-free please.

Back up any file you don't want to lose to another hard drive.

---

### Post by Aquilastudio.com on 2007-11-21
How do I reinstall though?

---

### Post by Aquilastudio.com on 2007-11-21
Help please !!!!!!!

---

### Post by OffAxis on 2007-11-21
```
sudo less /var/log/dpkg.log | grep error
```
should tell you which package failed to install completely.

and when you say it freezes, do you mean the terminal session or the entire system locks?

---

### Post by OffAxis on 2007-11-21
First of all Aquilastudio.com, you need to stop spamming the boards.

---

### Post by dasunst3r on 2007-11-21
The most risk-free way to go about reinstalling Ubuntu is to back up the files you have, particularly in /home.  Before selecting files to copy-and-paste, however, you would want to hit *Ctrl+H* in Nautilus to reveal hidden files.  After that, insert your LiveCD and install as usual.

---

### Post by oneadvent on 2007-11-21
i have to ask, how long did you wait?

What are you trying to install?

how much ram do you have?

---

### Post by Aquilastudio.com on 2007-11-21
I waited all night.

This happens when I install anything

I have 1.25 gigs of ram

---

### Post by Aquilastudio.com on 2007-11-21
The command does nothing 

The blinker still blinks but the line never ends

---

### Post by OffAxis on 2007-11-21
The question is: what do you need to backup?
Most things of consequence reside in your home directory.
/home/[your user name]

But if it's something more substantial (like an apache2 config file) those are in various places.

```
cp -r [source directory path] [destination directory path]
```
will copy a folder and all it's sub-folders (and files) to another location, like a usb drive.

The safest way would be to burn your data to a DVD and verify the data integrity afterwards.

---

### Post by oneadvent on 2007-11-21
One other thing,and then I'm out, and someone else is gonna need to help.

Does it happen when you install from source?

---

### Post by lespaul_rentals on 2007-11-21
Before you install any more applications, run the following:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Tell us if any errors come up when running these two commands.

---

### Post by Aquilastudio.com on 2007-11-21
What do you mean?

---

### Post by Aquilastudio.com on 2007-11-21
The first command works 
The second one freezes at Reading Database

---

### Post by OffAxis on 2007-11-21
How about
```
sudo less /var/log/dpkg.log | tail
```

---

### Post by tech9 on 2007-11-21
> **Aquilastudio.com said:**
> What do you mean?

he means manual installs

did you try...

sudo apt-get update 

yet?

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> What do you mean?He means run those commands in a terminal.

You know how to get to a terminal right?:confused:

---

### Post by Aquilastudio.com on 2007-11-21
No it doesnt i think. If you meand downloading and then dpkg

---

### Post by Aquilastudio.com on 2007-11-21
alexander@ubuntu:~$ sudo less /var/log/dpkg.log | tail
2007-11-21 12:44:47 status installed libglitz-glx1 0.5.6-1
2007-11-21 12:53:30 startup packages configure
2007-11-21 13:22:05 startup packages remove
2007-11-21 13:22:05 status installed libglitz-glx1 0.5.6-1
2007-11-21 13:22:12 startup packages configure
2007-11-21 13:30:15 startup packages remove
2007-11-21 13:30:15 status installed libglitz-glx1 0.5.6-1
2007-11-21 13:32:24 startup packages configure
2007-11-21 13:32:29 startup archives unpack
2007-11-21 13:38:13 startup packages configure

---

### Post by mellowd on 2007-11-21
Why do you keep making new posts asking the same question?

---

### Post by lespaul_rentals on 2007-11-21
> **Aquilastudio.com said:**
> No it doesnt i think. If you meand downloading and then dpkg

Wait, so you're saying you would grab a .deb from the Internet then run dpkg in the terminal manually?  Well if you did that, you might have effed-up your database or repositories.

Can you please paste the output of:

```
sudo apt-get update
```

Please?

---

### Post by Aquilastudio.com on 2007-11-21
alexander@ubuntu:~$ sudo less /var/log/dpkg.log | tail
2007-11-21 12:44:47 status installed libglitz-glx1 0.5.6-1
2007-11-21 12:53:30 startup packages configure
2007-11-21 13:22:05 startup packages remove
2007-11-21 13:22:05 status installed libglitz-glx1 0.5.6-1
2007-11-21 13:22:12 startup packages configure
2007-11-21 13:30:15 startup packages remove
2007-11-21 13:30:15 status installed libglitz-glx1 0.5.6-1
2007-11-21 13:32:24 startup packages configure
2007-11-21 13:32:29 startup archives unpack
2007-11-21 13:38:13 startup packages configure
alexander@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
alexander@ubuntu:~$

---

### Post by bapoumba on 2007-11-21
*Ahem*
Threads merged, and please stop bumping so often, thanks. Once or twice per day is enough.

---

### Post by tyggna1 on 2007-11-21
I had problems too.  If you press ctrl-alt-F1 and go CLI only, sometime it helps (esp in Gutsy, I've found).  Press alt-F7 to go back to GUI.

---

### Post by Aquilastudio.com on 2007-11-21
What is CLI only?

---

### Post by lespaul_rentals on 2007-11-21
Wow, that is really odd.  Your repositories seem fine.  I run Feisty and nothing like this has happened to me.  Maybe try using Synaptic/Adept?  I have no idea.

---

### Post by Aquilastudio.com on 2007-11-21
Synaptic freezes in the smae spot.

What is Adept?

---

### Post by lespaul_rentals on 2007-11-21
It's KDE's default package installer.

You're running Gutsy, you said?

---

### Post by Aquilastudio.com on 2007-11-21
I have gusty but gnome not KDE

---

### Post by lespaul_rentals on 2007-11-21
You might just try using Feisty instead.  I've never had this problem with Feisty.

---

### Post by Aquilastudio.com on 2007-11-21
How do I revert back to fiesty? I would be glad to

---

### Post by El_Belgicano on 2007-11-21
Hey, I've got a question about the reilstallation process, does it remove my installed programs, settings, ... I mean, can I just let him reinstal the kernel ...
thnx

---

### Post by Incense on 2007-11-21
> **Aquilastudio.com said:**
> This is what happened:

root@ubuntu:/home/alexander# dpkg --configure -a
root@ubuntu:/home/alexander#

Why were you running as root? I think you may have messed up your system, and i would really recommend you, back up your data (pictures, music, documents etc) to a CD or DVD, place the live disc back into your system and reinstall. I think it's going to save you a lot of time and heartache at this point.

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> How do I revert back to fiesty? I would be glad toSince nothing is working for you as of now, you might as well do a fresh install of Feisty. Download the live CD and install it.

---

### Post by Aquilastudio.com on 2007-11-21
I think it does. But can somebody answer my question.

---

### Post by Aquilastudio.com on 2007-11-21
I have the cd. How do I install it?

---

### Post by Inxsible on 2007-11-21
> **El_Belgicano said:**
> Hey, I've got a question about the reilstallation process, does it remove my installed programs, settings, ... I mean, can I just let him reinstal the kernel ...
thnx
If you have a separate home partition, then it will save the settings and config files for all the apps you have. provided of course that you do not format the home drive during the install.

---

### Post by Aquilastudio.com on 2007-11-21
How do I reach instalation process?

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> I have the cd. How do I install it?Boot up with the CD. Use the option Start or Install Ubuntu Then on the desktop click Install.


How did you install it the first time ?

---

### Post by mellowd on 2007-11-21
> **Aquilastudio.com said:**
> I have the cd. How do I install it?

???

How did you install it the first time?

Boot off the CD and go from there

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> How do I reach instalation process?Read my post in your other thread :roll:

---

### Post by Aquilastudio.com on 2007-11-21
First time. Somebody did it for me.

---

### Post by tech9 on 2007-11-21
> **Aquilastudio.com said:**
> I have the cd. How do I install it?


you can't be serious :shock:... I would suggest reading up on basics of Linux and Ubuntu  if you are not sure how to install it.

---

### Post by Aquilastudio.com on 2007-11-21
I still need help installing fiesty on gusty

---

### Post by Aquilastudio.com on 2007-11-21
The thing is I had problems with partitioning and my live disk would not load sometimes.

---

### Post by mellowd on 2007-11-21
If I were you, I'd backup my important data. Then read a bit about installing ubuntu.

---

### Post by Incense on 2007-11-21
> **Aquilastudio.com said:**
> I still need help installing fiesty on gusty

Put the disc in, reboot the computer, click install and follow the directions. That's all there is to it.

---

### Post by Aquilastudio.com on 2007-11-21
I will be back after I ty the CD please keep posting

---

### Post by El_Belgicano on 2007-11-21
I'm actually dual-booting so could I export my home directory (settings and ...) in an archive on my windows partition, reinstal Ubuntu and then have everything restored from that archive?
I don't have a separate home, but I've read some threads about it, and I'll make one when I get my Gutsy running again ... The thing is I think I made a mistake by changing some permissions in my home folder, and now I can't load Gutsy... Got the Ubuntu loading bar, then some console text and a disc check, freezes at about 48% and give a command prompt as root ...
Some advice?
Thnx

---

### Post by lespaul_rentals on 2007-11-21
Okay, first, backup any data you want to save.

Next, get the 7.04 Feisty Fawn LiveCD.  You can get this from a mirror specified by this site, or a BitTorrent tracker.  Get the i386 version.  Try this link:  [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

Burn it to a CD.

Reboot your computer with the LiveCD, then follow the steps to install.  When it asks how you want to partition your drive, select "Guided - Use whole disk".

There, you have Fiesty.

---

### Post by Inxsible on 2007-11-21
> **El_Belgicano said:**
> I'm actually dual-booting so could I export my home directory (settings and ...) in an archive on my windows partition, reinstal Ubuntu and then have everything restored from that archive?
I don't have a separate home, but I've read some threads about it, and I'll make one when I get my Gutsy running again ... The thing is I think I made a mistake by changing some permissions in my home folder, and now I can't load Gutsy... Got the Ubuntu loading bar, then some console text and a disc check, freezes at about 48% and give a command prompt as root ...
Some advice?
Thnxat the root command prompt you can try this command```
startx
```

---

### Post by Aquilastudio.com on 2007-11-21
Keep posting, My Live Cd did not boot. Help please!

---

### Post by Aquilastudio.com on 2007-11-21
My live CD is not read by any of my 3 computers. One is a Dell with an intell. Another is a gateway and the last is a hp with a amd processor

---

### Post by El_Belgicano on 2007-11-21
"command startx is availaible in usr/bin/startx
the command could not be located because /usr/bin is not included in the PATH environment variable
bash: startx: command not found"
was the answer ...
:( some other stronger trick to try (LiveCD maybe, then give the permissions back to my home folder ??)
or something else ...
thnx

---

### Post by Inxsible on 2007-11-21
do you have the boot from CD option as the first choice in your BIOS ?

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> Keep posting, My Live Cd did not boot. Help please!
do you have the boot from CD option as the first choice in your BIOS ?

---

### Post by tech9 on 2007-11-21
> **Aquilastudio.com said:**
> My live CD is not read by any of my 3 computers. One is a Dell with an intell. Another is a gateway and the last is a hp with a amd processor

Are you burning the ISO as an image? What are you using to burn it to disk and how are you doing it?

My guess is that you are burning the image file to the disk as a data CD.

---

### Post by Aquilastudio.com on 2007-11-21
I burn it using the LINUX CD?DVD burner I will try again in 5 minutes

---

### Post by tech9 on 2007-11-21
> **Inxsible said:**
> do you have the boot from CD option as the first choice in your BIOS ?

make sure you also set CD as 1st in the boot priority, in your BIOS, or at least set it as higher priority than your hard drive.

---

### Post by lespaul_rentals on 2007-11-21
> **Inxsible said:**
> do you have the boot from CD option as the first choice in your BIOS ?

*sigh*  No offense to this guy, I really mean no degradation, but if he doesn't know how to achieve and burn a LiveCD, I don't think BIOS is the place for him to lurk.

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> I burn it using the LINUX CD?DVD burner I will try again in 5 minutes
Dude !!

Slow down ! Burn a CD as an iso image not as a Data disk.

you need a lot of reading up to do !!

---

### Post by Inxsible on 2007-11-21
> **lespaul_rentals said:**
> *sigh*  No offense to this guy, I really mean no degradation, but if he doesn't know how to achieve and burn a LiveCD, I don't think BIOS is the place for him to lurk.
you may be quite right !

---

### Post by tech9 on 2007-11-21
> **Aquilastudio.com said:**
> I burn it using the LINUX CD?DVD burner I will try again in 5 minutes

Just do this...

If it is a true image file (ISO) then,

right-click on the ISO file and click write to disk - ubuntu is smart enough to burn it as an ISO, not data

---

### Post by Aquilastudio.com on 2007-11-21
That is exactly what I did :)

---

### Post by tech9 on 2007-11-21
> **Aquilastudio.com said:**
> That is exactly what I did :)

Then you should have a bootable LiveCD...

---

### Post by tech9 on 2007-11-21
> **lespaul_rentals said:**
> *sigh*  No offense to this guy, I really mean no degradation, but if he doesn't know how to achieve and burn a LiveCD, I don't think BIOS is the place for him to lurk.

seconded!

---

### Post by Aquilastudio.com on 2007-11-21
I am sorry but I have been in the bios millions of times. I have installed many versions of linux. I am just not so sure about installing ubuntu on my computer because I have put:

A new motherboard
A video card
1 gig of ram
a soundcard
a diskette drive
a cassete drive 
a tv input card

into that piece of junk. Many of these things are not supported so I have many problems. :twisted:

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> Ill check in 5 minutes. Keep posting!

> **Aquilastudio.com said:**
> keep postingand do what ?
What do you mean keep posting ?

---

### Post by overdrank on 2007-11-21
> **Aquilastudio.com said:**
> I am sorry but I have been in the bios millions of times. I have installed many versions of linux. I am just not so sure about installing ubuntu on my computer because I have put:

A new motherboard
A video card
1 gig of ram
a soundcard
a diskette drive
a cassete drive 
a tv input card

into that piece of junk. Many of these things are not supported so I have many problems. :twisted:

Why did you not say that you replaced all that hardware in your first post? :confused:

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> I have installed many versions of linux.Then installing Ubuntu should be a breeze for you. You said someone else installed it for you right ?

---

### Post by cwrann on 2007-11-21
Are you  booting from the cd/dvd drive or when you boot the computer does it boot to the HDD?

---

### Post by Aquilastudio.com on 2007-11-21
Yes I did. So can you help me with my effed up computer?

---

### Post by Aquilastudio.com on 2007-11-21
Keep posting about the process and help El_Belgicano

---

### Post by tech9 on 2007-11-21
> **overdrank said:**
> Why did you not say that you replaced all that hardware in your first post? :confused:

I would agree... if your hardware isn't supported, then this could be the source of your problems - especially if you went into your BIOS and set CD-ROM as 1st boot priority

---

### Post by asmiller-ke6seh on 2007-11-21
Run, do NOT WALK, to your nearest big bix bookstore, and buy a copy of _[COLOR="DarkRed"]UBUNTU FOR NON-GEEKS[/COLOR]_.

Turn to page one. Read and follow along on your computer. There is a good LiveCD copy of Ubuntu 6.06 bound into the book. Once you have finished the book you will be a lot more comfortable with Ubuntu. By that time, you will probably have a fully updated, and fully operational installation of Ubuntu ... and I bet you'll be using Ubuntu Gutsy Gibbon by that time, too.

---

### Post by lespaul_rentals on 2007-11-21
> **Aquilastudio.com]I have installed many versions of linux.[/quote]

[QUOTE=Aquilastudio.com said:**
> First time. Somebody did it for me.

Well I don't know what to think.  You either just lost your Linux virginity or you've been through this a thousand times.  No offense, but judging from your use of punctuation/grammar, posting three demanding threads about the same subject, and inability to burn a LiveCD, it seems like you are a new user.

But that's okay!  :)  We are here to help *everyone* from the veterans to the noobs!  So don't worry, we will help you, but you must be honest with us when we ask about your expertise.

---

### Post by Aquilastudio.com on 2007-11-21
Can you help?

---

### Post by tyggna1 on 2007-11-21
You might not *need* a reinstall--you rarely do.  CLI stands for Command-line interface.  It's kinda like the terminal.

If you press ctrl-alt-F1, you'll get to CLI only mode, like I said.   I have that same problem with application installs in Gutsy, and this is a work around.  If you're comfortable typing in
```
sudo apt-get install
```
then you very likely can do this in the ctrl-alt-F1 area after logging in.   Pressing Alt-F7 will get you back to your GUI--graphical user interface.   CLI is text based (like DOS), and GUI is what you usually see.

As for reinstall--I've had that problem too with the feisty live CD.  Try downloading the alternate CD, and then booting from the CD drive (F12 calls the boot device menu on some computers).

But, personally, I think you'd benefit from doing more reading and less posting.

---

### Post by Aquilastudio.com on 2007-11-21
I did that but my computer burps a bit at Reading Database but then stopps.

---

### Post by lespaul_rentals on 2007-11-21
Don't mess around with Gutsy anymore.  If you're having this big of a headache with it *just switch now*.    If you want good hardware support, you might try MEPIS 6.5.  It has good hardware support and is incredibly stable.

---

### Post by lespaul_rentals on 2007-11-21
WOW!!!!!!!!!!!!11111111111111111111111111111111oneoenoeneoneone

Listen mate, I am trying to help you, but you are typing like a 10-year old.  Just calm down!  We are trying to help you!

---

### Post by cwrann on 2007-11-21
What happens when you boot the live CD? (one exclamation point is fine if not excessive.)

---

### Post by Aquilastudio.com on 2007-11-21
PSST: WHAT IF I AM TEN? Just Joking..

When I load my system with the cd in it already. It showes my dell picture and loads the Bios. After that It stay unnormaly long at a black screen. The cd is going wicked fast cause I can hear it. After that the noise stops and nexdoor neighboor grub asks me what I want to boot.

---

### Post by mellowd on 2007-11-21
throw the cd away and do a new one

---

### Post by Aquilastudio.com on 2007-11-21
Sure I am doing it now.

---

### Post by cwrann on 2007-11-21
Go to [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) to find out what hardware is compatible out of box and what hardware is not.

---

### Post by Aquilastudio.com on 2007-11-21
I have a copy of that page pasted on my wall. :KS

---

### Post by lespaul_rentals on 2007-11-21
Well as long as your BIOS is set up correctly, it should boot from the CD, or at least ask you to press a button to boot from the CD.

Did you compare the MD5 checksum of the .iso you have with the .iso you downloaded?

---

### Post by cwrann on 2007-11-21
Is all the new hardware you installed compatible or not? If it is then a working live CD should get your computer up and running.

---

### Post by ericesque on 2007-11-21
I'm sorry, but this guy is either pulling our leg or padding his post count.  There's no way that someone who has installed any number of linux distros would have any trouble installing Ubuntu. If it's not working at this point it's a hardware issue and there's no magical command that is going to fix the problem. 

New mobo?  RMA it.  Remove the sound card, the tv tuner, the floppy, and the cassette (?) drive.  --Just for now to eliminate possible driver compatibility issues.

If you can achieve this and get a functional install, we'll talk about getting that other hardware to work as well.

---

### Post by Aquilastudio.com on 2007-11-21
I think my cd drive is messed up but I have a usb cd drive. Is this an option.

---

### Post by cwrann on 2007-11-21
Is the new disk working in any of your 3 computers now?

---

### Post by Samhain13 on 2007-11-21
> I'm sorry, but this guy is either pulling our leg or padding his post count.

Either that or gunning for more search engine visibility for user's domain? Highly suspect.

---

### Post by bapoumba on 2007-11-21
*cough*
Hello ;)

---

### Post by Inxsible on 2007-11-21
> **Aquilastudio.com said:**
> I think my cd drive is messed up but I have a usb cd drive. Is this an option.Why don't you inform us about your hardware in the beginning? Or are you trying to make everyone go on a wild goose chase.

You let everyone know that you changed a bunch of hardware somewhere in the post 60s or 70s and now you tell us its a usb cd drive !!!


Does your Bios have ability to boot from USB drives?

---

### Post by Aquilastudio.com on 2007-11-21
I have a cd drive.

Ihave a USB drive

I also have Phoienix rom Bios

---

### Post by edwardTheGreat on 2007-11-21
> **Inxsible said:**
> Be patient. Don't start new threads every 15 mins. 

+1 for that

oh and the thread title 'I Need Help Now. Please Help Me'  isn't very informative about what the problem is, I think you should choose something that describes the problem so people that want to help can actually see what they are trying to help you with.

Anyway, I'm sure everyone else will get you on your way.

---

### Post by Aquilastudio.com on 2007-11-22
OK here is a very thorough overview of my system.
I double booted Windows and Fiesty on one computer. I had Windows for 2 years before. 
My computer has a Ati Radeon video card. It has a Creative Soundcard. My cd drive is really bad But I have a usb cd drive. My computer has a motherboard found in Dell Dimension 4600. I did a 2 day upgrade to Gusty. After that everything went wrong. The compiz-fusion that I installed on fiesty through a lot of pain was gone. Half of my sound was messed up. In my search for installing compiz, I was installing many things and changing many repristories. After that, COmpiz di d not work and my apt-get install started freezing a (reading Database.. I needed help desperately. I installed gusty the day it came out. I need help. 
Can I reinstall fiesty without. If I have a cd can I install without booting the CD but inside Ubuntu? Is my hard drive good to throw away?

---

### Post by mikewhatever on 2007-11-22
> **Aquilastudio.com said:**
> OK here is a very thorough overview of my system.
I double booted Windows and Fiesty on one computer. I had Windows for 2 years before. 
My computer has a Ati Radeon video card. It has a Creative Soundcard. My cd drive is really bad But I have a usb cd drive. My computer has a motherboard found in Dell Dimension 4600. I did a 2 day upgrade to Gusty. After that everything went wrong. The compiz-fusion that I installed on fiesty through a lot of pain was gone. Half of my sound was messed up. In my search for installing compiz, I was installing many things and changing many repristories. After that, COmpiz di d not work and my apt-get install started freezing a (reading Database.. I needed help desperately. I installed gusty the day it came out. I need help. 
Can I reinstall fiesty without. If I have a cd can I install without booting the CD but inside Ubuntu? Is my hard drive good to throw away?

Since your system seems to be really messed up, fixing it is impractical. Backup your files and reinstall, Feisty, Gutsy, does not matter.

> Can I reinstall fiesty without.

Excuse me?

> If I have a cd can I install without booting the CD but inside Ubuntu?

No.

> Is my hard drive good to throw away?

That's up to you.

---

### Post by tyggna1 on 2007-11-22
haven't tried this myself--but, it might be worth a shot.

If you edit your sources.list (I believe it's under /etc/apt/) 
and change all the "gutsy" to "feisty"  and then type in:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It might trick your computer into thinking that you want to "upgrade" to feisty.

---

### Post by por100pre1 on 2007-11-22
> **Aquilastudio.com said:**
> First time. Somebody did it for me.

Can you contact that person in order to help you with the reinstall? **Backup your user folder to removable media or external hard disk drive even your Windows files.** I'm afraid this could get worse. :-k

---

### Post by Jense on 2007-11-22
The upgrade didn't work for a lot of people (including me). To fix it, based on your previous threads, you will have to reinstall. You could be done with that if you had started last night after getting that advice. It's not hard. Fixing messed up database sounds hard to me, no idea how you can do that, plus you will probably have other problems. 
So:
Download 

[http://hr.releases.ubuntu.com/kubuntu/gutsy/kubuntu-7.10-alternate-i386.iso](http://hr.releases.ubuntu.com/kubuntu/gutsy/kubuntu-7.10-alternate-i386.iso)

opening in kubuntu should put you right into the burning dialog - just burn it.

Advising how to best keep your date is difficult without knowing your partition setup. If your homedirectory is on a different partition from your system partition, then its easy - if not - burn it to cd/dvd.

Do some reading first as to how to set up your partitions properly.

[http://www.control-escape.com/linux/lx-partition.html](http://www.control-escape.com/linux/lx-partition.html)

Doing this properly once will save you a lot of trouble in the future.

Reinstall, copy your backup into the home folder - restart. DO NOT INSTALL THE PROPRIETARY DRIVER FOR FOR YOUR ATI CARD right away - do some reading first to see if it will work.

Generally - lots of the problems you described have been solved in this Forum - use the search function before doing a million posts.
To use Ubuntu you better accept, that you will have to READ stuff to get it to work, though lots of things work out of the box, it still depends heavily on your hardware.

After reinstall you will find that lots of things work out of the box - Compiz for example is now included in the repositories so

sudo apt-get install compiz, 

or using apt-manager will do this for you (only if your grafiphics work right)

---

### Post by Aquilastudio.com on 2007-11-24
So u want me to install xubuntu instead of ubuntu?

---

### Post by steveneddy on 2007-11-24
This thread is so funny!

---

### Post by lespaul_rentals on 2007-11-26
How many installs did you say you did again?

---

### Post by tech9 on 2007-11-27
> **steveneddy said:**
> This thread is so funny!

it is... ;)

---

### Post by Aquilastudio.com on 2007-11-28
I proboably attempted to install compiz 25 times that day. I know it sounds crazy but I needed my computer for a presentastion and half of the things did not work. :mad:

---

### Post by Aquilastudio.com on 2007-11-29
Solution: I used the Alternative CD, I hope this will work :). This thread was a very big help. Thankyou all for your comments and for helping me with my messed up ubuntu !

---

### Post by Aquilastudio.com on 2007-12-10
I can not boot the cd.!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Aquilastudio.com on 2007-12-10
The cd grinds a bit but then the system starts grub!

---

### Post by Aquilastudio.com on 2007-12-24
I would be thankful for some help on this problem.

---

### Post by Aquilastudio.com on 2008-03-23
PLEASE HELP! I DESPERATELY NEED APT_GET> IF THERE IS A WAY TO INSTALL COMPIZ WITHOUT APT-GET please tell me!

---

### Post by bapoumba on 2008-03-23
> **Aquilastudio.com said:**
> PLEASE HELP! I DESPERATELY NEED APT_GET> IF THERE IS A WAY TO INSTALL COMPIZ WITHOUT APT-GET please tell me!
Hmm, could you please post a brief summary of your current situation?

---

