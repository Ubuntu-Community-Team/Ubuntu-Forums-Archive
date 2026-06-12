---
title: "A newbie trying to donwload and Install CVS"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by rrsodl on 2008-01-23
Hi,
I'm a newbie here and totally new to Linux so go easy on me :)

I have just installed Ubuntu and I'm so surprised how good it looks and feel. At the moment it's running from an XP directory so, it's not the best option but while I learning it will have to do :)

Now, the first problem that I've come across is that Ubunto does not recognises my wireless card so I have not access to the internet. A little search in google tells me that my card works quite well under Linux but I need to build a driver for it... to be able to do that I need to install CVS ... so I came here searching for info and I found out that I could go to system -> Administration - something package management and install CVS BUT since I don't have internet access this method does not work.

So I have two options:

1 - connect to the router with a wire and install CVS and take it from there.

2. download the CVS and install it manually.

I would like to take the second option so I can learn how to do it... I looked at the site where I can download CVS from  but it looks nothing like I expected - it just seems to be directories - do I need to connect with an FTP program or what?

The place looks like this:


Index of /non-gnu/cvs

Icon  Name                    Last modified      Size  Description[DIR] Parent Directory                             -   
[DIR] binary/                 05-Jun-2007 11:17    -   
[DIR] source/                 05-Jun-2007 10:34    -   


Thanks in advance

Rick

---

### Post by furball_1185 on 2008-01-23
CVS is just a download service that pulls the current version (or whatever you specify) of a code repository somewhere on the Internet. What you are looking at are two directories on that repository; binary and source. The binary will contain files that have already been built for a specific architecture; probably an x86 PC. This may be all you need and would be better for a new person (faster at the very least) since you wouldn't need additional things like compilers to get going. The source directory contains raw source code for making the drivers on your computer. This is a catch all; if your computer can use the drivers, you can make a set from this.

Try the binaries. Hopefully there is some documentation in there to help you along. If not, you will need to build from source. This sin't too hard, but requires additional programs you may/may not have. Keep me posted and I will help with other questions.

---

### Post by Bruce M. on 2008-01-23
Hi rrsodl...

From an XP directory?
How did you install Ubuntu into Windows?

What type of wireless card are you using, maybe Ubuntu has direct support.

---

### Post by Cypher on 2008-01-23
First, go the Ubuntu Packages page for [CVS]("http://packages.ubuntu.com/gutsy/devel/cvs"). Here you will see all the dependencies for CVS which seems to be all system level stuff. So at the bottom of the page, click on i386 which will take you to the list of .DEB files that you an download. Download the file and place it in your Windows partition somewhere.

In Ubuntu you should be able to use NTFS-3G to access the Windows partition with the file, doing so copy the file into Ubuntu. Then run
```

sudo dpkg -i <package name>.deb

```
to install the package into Ubuntu..

This will only get you there partially though, since you will still need to download the sources for your WFi card through the Internet. So you're better off using WinCVS in your Windows machine to download the sources, and then use NTFS-3G to get access to the sources for compilation in Ubuntu...

---

### Post by rrsodl on 2008-01-23
> **furball_1185 said:**
> CVS is just a download service that pulls the current version (or whatever you specify) of a code repository somewhere on the Internet. What you are looking at are two directories on that repository; binary and source. The binary will contain files that have already been built for a specific architecture; probably an x86 PC. This may be all you need and would be better for a new person (faster at the very least) since you wouldn't need additional things like compilers to get going. The source directory contains raw source code for making the drivers on your computer. This is a catch all; if your computer can use the drivers, you can make a set from this.

Try the binaries. Hopefully there is some documentation in there to help you along. If not, you will need to build from source. This sin't too hard, but requires additional programs you may/may not have. Keep me posted and I will help with other questions.

Thanks a lot for the help, everybody!!!

OK, I have found the steps to build the driver and are as follows:

"Driver Installation
This card uses the Linux madwifi drivers which actually work for most cards that use the Atheros ar5210, ar5211, and ar5212 chipsets . Currently, the drivers are only available via CVS. You can get a hold of the drivers using the following command:

root@mgmt:~# cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/madwifi co madwifi

Building and installing the drivers is very easy. The standard commands will work.

root@mgmt:~# cd madwifi
root@mgmt:~# make
root@mgmt:~# make install
Making it work
Once the drivers are installed, load the drivers in the following order:

root@mgmt:~# /sbin/modprobe wlan
root@mgmt:~# /sbin/modprobe ath_hal
root@mgmt:~# /sbin/modprobe ath_pci

With the drivers loaded, /bin/lsmod should look something like this.

root@mgmt:~# lsmod    
Module                  Size  Used by    Tainted: P 
ath_pci                29784   1
ath_hal               115344   1  [ath_pci]
wlan                   46758   1  [ath_pci]
ide-scsi                9424   0
agpgart                39576   0  (unused)
"

I need to get CVS sorted out first :)

I will follow Cypher steps for that - thanks for the help Cypher, very much appreciated.

Bruce M,

I have two versions of uBunto, one is  a pendrive version, quite nice too  - the plans is to learn to use Linux well and do away with XP  and use the pendrive version in my laptop.


Ubunto under XP is dead easy to install - here are the instructions [Ubuntu 7.10 under Windows ]("http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/")  - not the best option I must say but for trying it out it's ok I guess :)

Thanks again for the help.

Rick

---

### Post by rrsodl on 2008-01-24
Hello again!!!!! :)

I'm posting right now from my PC, running Ubuntu 710, and connected to my wireless router - wow - I'm a happy man right now :guitar:

Well, to cut a story short.... I got fed up running Ubuntu from Windows XP, too slow for me lol so I installed it on a 2GB mem stick and it runs like a champ.  I'm so impressed with Linux - I'm configuring the system as I go along and hope to install permanently in a HD at some point.

Guess what? I installed CVS and I didn't need it lol - the driver is not longer in CVS lol nevermind, 


Rick

---

