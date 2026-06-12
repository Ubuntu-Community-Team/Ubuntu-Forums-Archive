---
title: "Kubuntu noob"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by thesunscreen on 2007-09-23
I started looking for a good distro to replace windows in my little world I started with a test laptop and mandrake, then I went to suse, finally ubuntu, and then kubuntu. I like KDE and couldn't figure out how to change ubuntu to KDE until I found Kubuntu. I wanted a system as close to Windows as I could get, well I got it. Kubuntu makes sense to me, however it crashes, has unexplained failure points and in short is windows, at last I'm home. I need this, I need the unexplained crashes, and constant trips to console. I liked kubutu so much I started switching my server over to it, a simple file server with a few added perks its a Dell server dual 700 mhz PIII's 1 ide hd 160 maxtor that only wants to show up as 30 gb. It runs on windows 2000, so I cloned the 2000 drive from a 30 gb to the 160 then installed kubuntu on it then it rebooted and grub loaded and I got an error code 17. After some searching I tried a few things and then my windows partition crashed with bsod, and kubuntu wouldn't even load. Oh I almost forgot the key to this server is the 1.5 TB raid 5 array of Sata 2 drives on a PCI card. On my windows partition they are a seperate drive, I wanted to do the same thing. I re cloned the drive with windows so now I'm starting fresh, is there something I should be doing differently on the next install? I'm alergic to working with console, I'll do it when I have to, but not happy about it.

---

### Post by LaRoza on 2007-09-24
Could you please list the problems in a reasonable manner? I can't really tell what the problems are.

It seems your computer is having trouble with Kubuntu. Kubuntu is a modern OS, and installing it on old hardware will result in strange behavior sometimes, like all OS's. (Try installing Vista on this machine)

What are the specs of this computer, and what version of Kubuntu are you using.

If you already have Ubuntu installed, you can get KDE with this:

```

sudo aptitude install kde-core

```
Give it time, and when you log on, you can select the session to be KDE, and if you want, you can make it the default.

---

### Post by shearn89 on 2007-09-24
After a bit of work deciphering your post (please try to puncutate, and put in new lines when suitable), I think i get the jist of your problem.

> its a Dell server dual 700 mhz PIII's 1 ide hd 160 maxtor that only wants to show up as 30 gb.

This is probably due to partitioning - make sure if you want to be able to use 160GB that you partition the whole drive as ext3 (with perhaps a small bit for /swap). The automatic partition configuration should work fine.

> It runs on windows 2000, so I cloned the 2000 drive from a 30 gb to the 160 then installed kubuntu on it then it rebooted and grub loaded and I got an error code 17. 

Not sure whats going on here.

> Oh I almost forgot the key to this server is the 1.5 TB raid 5 array of Sata 2 drives on a PCI card. On my windows partition they are a seperate drive, I wanted to do the same thing. 

Not too knowledgeable about RAID arrays, but I know they're not automatically detected as 1 drive/whatever in Ubuntu. 
I did find [this]("http://ubuntuforums.org/showthread.php?p=1348441"), although it sounds like a totally different language to me...

---

### Post by adamklempner on 2007-09-24
> **thesunscreen said:**
> After some searching I tried a few things and then my windows partition crashed with bsod, and kubuntu wouldn't even load. 

This sounds like it could be a potential hardware failure.  A windows crash shouldn't affect a linux partition.  Instability across multiple OS's on the same computer is often an indication of a hardware failure.  Maybe that hard drive is dying.  It also sounds like you have a lot of stuff in the box, maybe your power supply is insufficient?

---

### Post by agntsmyth on 2007-09-25
> **LaRoza said:**
> Could you please list the problems in a reasonable manner? I can't really tell what the problems are.

It seems your computer is having trouble with Kubuntu. Kubuntu is a modern OS, and installing it on old hardware will result in strange behavior sometimes, like all OS's. (Try installing Vista on this machine)

What are the specs of this computer, and what version of Kubuntu are you using.

If you already have Ubuntu installed, you can get KDE with this:

```

sudo aptitude install kde-core

```
Give it time, and when you log on, you can select the session to be KDE, and if you want, you can make it the default.

Tried this and recieved

Couldn't find any package whose name or description matched "kde-core"
No packages will be installed, upgraded, or removed.

I am trying to install kde as an alternate window manager because many people who I respect feel it is better and i want to see for myself.

---

### Post by LaRoza on 2007-09-25
> **agntsmyth said:**
> Tried this and recieved

Couldn't find any package whose name or description matched "kde-core"
No packages will be installed, upgraded, or removed.

I am trying to install kde as an alternate window manager because many people who I respect feel it is better and i want to see for myself.

If you just want to see it, use a Live CD, like Kubuntu, Knoppix, or Sidux.

It is not better, it is different.

I use Fluxbox, which is better than KDE or GNOME **for what I want**.

If apt can't get the package, try again, just in case, or try using apt-get.

---

### Post by Maestro23 on 2007-09-25
> **agntsmyth said:**
> Tried this and recieved

Couldn't find any package whose name or description matched "kde-core"
No packages will be installed, upgraded, or removed.

I am trying to install kde as an alternate window manager because many people who I respect feel it is better and i want to see for myself.

Do you have all your repos enabled?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Enable all repos, then check for kde-core again.

---

