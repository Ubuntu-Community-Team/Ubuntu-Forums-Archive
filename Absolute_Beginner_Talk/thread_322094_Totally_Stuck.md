---
title: "Totally Stuck"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by VidK on 2006-12-20
Hi --

I'm a newbie to both Ubuntu and Linux (yay me!) and I've managed to get Ubuntu installed on an 80 gig HD. 3 Gigs for WinXP/NTFS, 3 for Ubuntu/EXT3, 2 for LinuxSwap/EXT3, and the rest for data as EXT3. I'm using the FS reader/writer for WinXP to write/read the data partition. I'm using a Dell 1450 wi-fi card to connect to the internet on Windows... but this all brings me to where I'm stuck with Ubuntu. I'm a Linux newbie so please be kind:

1) I'm unable to write to my "documents" folder - the 60+gig folder that is me EXT3 partition. When I try to write a text file or anything in Ubuntu it tells me I don't have permission. When I check the properties, it tells me the creator is "root" and I'm logged in as "david" - the initial login name I gave when I first installed Ubuntu. I thought the first install account was, by default, "root". What gives?

2) I've tried using the "ndiswrapper" to install the Dell Windows drivers for my Wi-Fi card, but I don't even know how to compile in Linux. I found a step-by-step compiling and installion how-to here - but I can't get anything to work. How do I do all this??

3) I've tried using Dell's Linux drivers for th card, but they want me to d/l and install something called "dkms" and "rpm". I tried that but had about as much success with that as ndiswrapper".

Help! PLeeeeease! ](*,) 

David

---

### Post by macogw on 2006-12-20
Hook yourself up to a wired connection.  Open a terminal (applications > accessories > terminal) and type:
```

sudo aptitude install build-essential  alien
```
Now you have everything you need to build from source.  You won't need ndiswrapper if they have Linux drivers.  .rpm is a Red Hat Package Manager binary file.  Ubuntu is based on Debian, so it uses .deb.  Don't worry though.  All you have to do is download the .rpm that Dell offers, then open up the terminal and type in
```
sudo alien DellsDriverPackage.rpm
```
replacing DellsDriverPackage.rpm with the name of whatever the .rpm you downloaded is.  It will create a .deb for you.  Double-click on that .deb and tell it to install.  Now you have wireless drivers.

Your "documents" folder in Linux should be called /home/David which is represented in the terminal as ~

---

### Post by VidK on 2006-12-20
I don't have a wired connection or access to one, atm. :(

---

### Post by macogw on 2006-12-20
In that case, [http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) if you're on edgy or [http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential) for dapper.  Download build-essential (d/l link is at the bottom of the screen) and then download everything with a red circle or green diamond next to it.    When you're in the pages for those dependencies, make sure you get any red circles/green diamonds they have too.  Either burn to a cd or save on a floppy or flash drive.  Then you can boot into Linux, insert the disk/usb drive and double click on all those things to install them.

Do the same thing for [http://packages.ubuntu.com/edgy/admin/alien](http://packages.ubuntu.com/edgy/admin/alien) on edgy or [http://packages.ubuntu.com/dapper/admin/alien](http://packages.ubuntu.com/dapper/admin/alien) on dapper


It won't work if you miss anything that any of them depend on, so be careful to get all of them, okay?  This is an annoying way to download stuff, but once you have an internet connection, it's very easy.

---

### Post by VidK on 2006-12-20
ok... I did what you suggested and, yes, it was a pain. But, I got through it and I have a ton more errors. I've listed the errors (usually either conflicts with other items or dependency issues) and, for the dependency issues, the files I have that I downloaded that *should* work - but aren't.

rpm_4.4.1-5ubuntu2.1_i386- not satisfiable: libbeecrypt6

alien_8.64_all.deb- not satisfiable: rpm

build-essential_11.1_i386.deb
- Dependency not satifiable:gcc; I have gcc_4.0.3-1_i386, gcc-4.0_4.0.3-lubuntu5_i386, 

gcc-4.0-base_4.0.3-lubuntu5_i386

binutils_2.16.1cvs20060117-1ubuntu2.1_i386- conflicts with installed package 'binutils'

perl-modules_5.8.7-10ubuntu1_all.deb- conflicts with installed package 'perl-modules'

perl-base_5.8.7-10ubuntu1_i386.deb- conflict with perl-base

gcc_4.0.3-1_i386.deb- dependency not satisfiable: cpp ; I have cpp-4.0_4.0.3-lubuntu5_i386.deb

libc6-dev_2.3.6-0ubuntu20_i386.deb- conflicts with lib6-dev

g++_4.0.3-1_i386.deb
- not satisfiable: cpp ; I have cpp-4.0_4.0.3-lubuntu5_i386.deb

g++-4.0_4.0.3-1ubuntu5_i386.deb- not satisfiable: libstdc++6-4.0-dev; I have 

libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb, libstdc++6_4.0.3-1ubuntu5_i386.deb

libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb- not satisfiable: g++-4.0; I have g++_4.0.3-1_i386.deb

-- ty for your help, btw... David--

---

### Post by macogw on 2006-12-21
If it says it conflicts with installed package and names something essentially the same, then you already have a version of it installed and I don't think you need to worry about it (ex: binutils)

libbeecrypt6: [http://packages.ubuntu.com/dapper/devel/libbeecrypt6](http://packages.ubuntu.com/dapper/devel/libbeecrypt6)

Okay, build-essential is saying you need gcc.  gcc is saying you need cpp.  build-essential won't believe gcc is there until all its dependencies (ex: cpp) are there.  cpp isn't there because all of IT's dependencies aren't met.  I told you it'd be a pain in the butt.

g++ says it needs libstdc even though you have it because libstdc still needs some other files before it'll be functional

hmm You're doing this by double clicking them right?  Maybe the fact that they aren't being done simultaneously is confusing them because none of them see their dependencies at the right times.  Try putting them all in a folder on your desktop named deb then go to the terminal and type in

```

cd ~/Desktop/deb
sudo dpkg -i *

```
That should install everything in that folder and hopefully keep them from thinking their dependencies are missing when they're really just sort of waiting in line.

---

### Post by jbutler12 on 2006-12-21
Wouldnt it be much easier just to use ndiswrapper?

See [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Keep in mind you have to install ndiswrapper-utils.  This is done without an internet connection by putting your Ubuntu CD in the drive, going to Synaptic Package Manger (system->admin->Synaptic Package Manager) and searching for ndiswrapper-utils.  They will install off the CD.  Then just follow the instructions on that site.

---

### Post by rccharles on 2006-12-21
Try APTonCD. 

"APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection."

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

jbayone  provided this tip.

Robert

---

### Post by macogw on 2006-12-21
> **rccharles said:**
> Try APTonCD. 

"APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection."

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

jbayone  provided this tip.

Robert

:-O neat! *will remember*

---

### Post by VidK on 2006-12-21
Hi... I heard alot of about 'ndiswrapper'. Even though I *have* the Linux drivers... I tried using ndiswrapper to use the Windows drivers. I got the following error when I tried to install ndiswrapper...

W: Failed to fetch cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb
  MD5Sum mismatch

Any suggestions?

David

---

### Post by DarkOx on 2006-12-21
It looks like it can't read your installation CD. You can get the necessary files off of the internet, though. First, find out what version of Ubuntu you're running. Open a terminal in Ubuntu and type:

> cat /etc/issue

It will say something like "Ubuntu 6.10" or "Ubuntu 6.06". If it says 6.10, you're using the most recent, and therefore potentially unstable, version of Ubuntu. If it says 6.06, you're using a slightly less recent, but more bug-free version of Ubuntu. Anyways, you can find the ndiswrapper package you need [here]("http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8") for 6.10 and [here]("http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils") for 6.06.

From the webpage, scroll down to where it says "Download ndiswrapper-utils", and select either the i386 version or the amd64 version. If you're using an intel-based processor, you're the i386 version (most computers are of this type, so it's a safe bet this is the one you need). Download the package from any one of the mirrors (doesn't matter which one), and save it somewhere convenient, such as a flash drive or a floppy disk.

In Ubuntu, open up a file browser, and find the file you downloaded. Right-click it and select the option to install the package (which I believe is the first one and says something like "GDeb package installer", or something). Installation should happen automatically, and ndiswrapper should be ready to go. Hopefully your guide will work now, if not post back and someone'll help you.

---

### Post by VidK on 2006-12-21
I'm definately running Dapper (6.06). I downloaded the ndiswrapper-util from the link you provided and I tried what you suggested and got the following error:

Error: Failed to satisfy all dependencies (broken cache)

---

### Post by VidK on 2006-12-21
By the way, I think I was able to get the Linux drivers installed for my adapter. (It's a USB Wi-Fi adapter Dell model 1450) But things still aren't working. The lights aren't blinking on the adapter and I have no way of knowing if the driver is even installed properly.

When I go to System > Admin > Networking - there's a wireless card (ES2 - is it's designation I think) but it doesn't look like it's connected. I don't get a list of available networks to connect to or the option to do so.

???

](*,) 

David (head hurting now)

---

