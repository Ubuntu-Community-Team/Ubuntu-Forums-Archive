---
title: "No GUI???"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Neo_XY on 2007-07-03
Hi everyone,

I just finished in installing the Ubuntu Server, after rebooting it came up a command line login screen, why?
how do I make it to auto start in to GUI Desktop?

This is my first time in linux world.

Thanks in advance for your help.

N.

---

### Post by Rocket2DMn on 2007-07-03
Hehe, the server edition does not come with a GUI, but you can install one.
```
sudo apt-get install ubuntu-desktop
```
then you can run
```
startx
```

---

### Post by Neo_XY on 2007-07-04
I tried to type the first command and it gave me this message:

sudo apt-get install ubuntu-desktop

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop

The Server CD is in the CD drive E: already. I burned the ISO into this CD.

N.

---

### Post by Outrunner on 2007-07-04
Its supposed to download ubuntu-desktop from the internet not to install it from the CD. I suggest ejecting the CD

---

### Post by Hobo Joe on 2007-07-04
In the command line, type:
```

sudo nano /etc/apt/sources.list

```

Then find the repositories that have 'cd' in them, and comment them out by putting '##' in front of the lines.

That should do it.

---

### Post by Neo_XY on 2007-07-04
I downloaded this file "ubuntu-desktop_1.43_i386.deb" to my Windows PC, how do I install it?

---

### Post by Neo_XY on 2007-07-04
How do I go out to the internet?
I am at command line only.

---

### Post by Neo_XY on 2007-07-04
What am I supposed to do after this command "sudo nano /etc/apt/sources.list"?
I put ## at the beginning of line deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_....

If I type sudo apt-get install ubuntu-desktop, it would get me the same error message:
"E: Couldn't find package ubuntu-desktop"

Drive E: is my CD drive, it seems to me it looking for this file in the E: drive.

---

### Post by Hobo Joe on 2007-07-04
> **Neo_XY said:**
> What am I supposed to do after this command "sudo nano /etc/apt/sources.list"?
I put ## at the beginning of line deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_....

If I type sudo apt-get install ubuntu-desktop, it would get me the same error message:
"E: Couldn't find package ubuntu-desktop"

Drive E: is my CD drive, it seems to me it looking for this file in the E: drive.

Well, it sounds like you did it right, but apparently you don't have the other repositories enabled.

I'll use my sources.list file as an example.

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse                   <-----uncomment
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse              <-----uncomment
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe                    <---------- uncomment
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

## Beryl svn
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn                      <----these are some extra repos's I have, you can ignore them unless you want the newest Beryl version.
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

```

---

### Post by Neo_XY on 2007-07-04
Do you want me to uncomment out this line "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse"?
remember I don't have internet at all at this point, at the installation it did not detect my network DHCP server.

---

### Post by eternalsword on 2007-07-04
need to get your networking set up first are you using a wireless connection?  if so can you possibly try a wired connection?

---

### Post by insane_alien on 2007-07-04
why didn't you get the desktopCD like everbody else? that has the GUI by default.

you probably do have the internet type:```
ping -c 4 http://www.google.com
``` to make sure. ubuntu is good at doing these things automatically.

---

### Post by Neo_XY on 2007-07-04
Let me ask you a question here, if I install Ubuntu Desktop version, will it goes to GUI (Desktop) after the installation?
What I am trying to do here is the iSCSI Enterprise Target (SourceForge), so I can test my SAN storage.

---

### Post by stoodleysnow on 2007-07-04
YOUR CD DRIVE IS NOT E:\ in LINUX!:mad:
it becomes hdc or hdd.
And yes, if you use the desktop CD, it goes straight to the GUI (if you have enough RAM memory in your PC)
You should have at least 256MB to be safe.
When you download the ISO image, the next stage is to burn it to CD. I suggest (if you're in Windows) installing burnatonce from [http://www.burnatonce.net](http://www.burnatonce.net) and then using that to directly burn the ISO file to a blank CD.
It will boot as a live CD when you get it going. Double click the install icon, for a nice graphical installation. At the end it will prompt you to remove the CD before rebooting. Do so. Then enjoy your Ubuntu PC.:)

Edit: and it should also have some SCSI support, SCSI, SATA and USB disks are all sda, sdb etc.

---

### Post by Neo_XY on 2007-07-04
No I have wired connection, I will wipe out the Server version and install desktop version.

---

### Post by v8YKxgHe on 2007-07-04
> **stoodleysnow said:**
> YOUR CD DRIVE IS NOT E:\ in LINUX!:mad:

I was just about to say that lol.

Neo_XY, Servers typically don't have a GUI as there is no need for one at all. You should be fine with the Desktop CD though, what made you go for the Server CD?

---

### Post by lbelloq on 2007-07-04
Eeeh, then Desktop version is better.

---

### Post by Malibu Illusion on 2007-07-04
I also have to ask, what on Earth made you download the server version, when you're looking to run it on your desktop?

---

### Post by digitza on 2007-07-06
I downloaded both, installed the server version and got to the same (doesn't even smell like DOS) command line...
The machine now has a dual-boot with MsXP, very basic, only there to help if something goes wrong.
What's wrong with a GUI for a server? MsServer has one!!!

Anyways... i learned DOS, now it's a whole bunch of DollarSigns and squiggles to input to my grey matter...

Some help with the startx would be great :)

i tried the ping for google, but the error returns: unknown host.
how would i set the gateway and IP addresses including dns'?

i'll keep an eye on this post, but will look for answers so long...

Thanks

---

### Post by walkerk on 2007-07-06
> **Neo_XY said:**
> Let me ask you a question here, if I install Ubuntu Desktop version, will it goes to GUI (Desktop) after the installation?
What I am trying to do here is the iSCSI Enterprise Target (SourceForge), so I can test my SAN storage.

Yes it will. It comes standard with gnome (ubuntu-desktop)

I suggest you download the ubuntu desktop edition .iso from [ubuntu]("http://www.ubuntu.com/getubuntu/download")..

---

