---
title: "Installation Difficulty"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Tb0ned on 2007-06-27
I've attempted to install 7.0.4 a handfull of times but always get stuck at step 5 out of 7 where it asks me to transfer over a windows profile. I do have an X800GTO that I read has some problems but was confused by it and couldn't find a installer other than the normal one as the tutorial referred to a text installer which I couldn't find. I have my hard drives all partitioned for the swap and mine install spots but the installation won't go through. Current setup is as follows.

AMD 2600+
ATI X800GTO
Audigy 4
ASUS A7-V8X-X Motherboard
2 Gigs PC3200 Ram
40 Gig & 160 Gig 7200 RPM Parallel ATA
XP Home OEM

---

### Post by Golyadkin on 2007-06-27
Okay, I think you are mixing some things up here. The migration of a WIndows profile has nothing to do with your graphics card. What it does for you is copy your "My Documents" folder and some other settings from your Windows partition for the users you select. This makes it easy for you to use your files, without having to copy them by hand. If you want an empty home directory in Ubuntu and no settings migrated, then just click Next, otherwise, select the users you want to copy the data from and then click Next.

The text installer referred to is probably the Xubuntu installation. That is not a live-cd and it will install a textmode. Later you can add GNOME or KDE or Xfce with a few simple commands.

---

### Post by Tb0ned on 2007-06-27
I think I just made my post horribly unclear. Anyway for clarification: My installation problem is that when I hit next on the 5th Installation step (The import a Windows Profile one) it just sits there and spins for seemingly no reason at all, quits thinking and then does nothing. I've tried it both with importing my profile, and with not. I was just unsure of 1) How to fix the problem and get past this point and 2) Whether or not this error was tied to the ATI X*** error or something more unique and local than that. Thanks for the help.

---

### Post by tarek on 2007-06-27
Hi, if you don't want your windows profile, use the alternative cd, it doesn't ask for anything, very simple and quick.

TK

---

### Post by Tb0ned on 2007-06-27
I realize what this part of the installation does. It's pretty straight forward. My question revolves around the fact that when I hit next at this portion of the installation it sits there and does nothing so I can't install.

---

### Post by tarek on 2007-06-27
> **Tb0ned said:**
> I realize what this part of the installation does. It's pretty straight forward. My question revolves around the fact that when I hit next at this portion of the installation it sits there and does nothing so I can't install.

Don't know why, cannot help there :( 

But I would give the alternative CD a try, I like to copy my docs, bookmarks, etc. from win to ubuntu myself, but that's just me.

---

### Post by Tb0ned on 2007-06-27
Alrighty, is the alternative CD Kubuntu or am I totally off here, or I'm a tard and can't find the alternative cd download which may very well be the case.

---

### Post by bodhi.zazen on 2007-06-27
> **Tb0ned said:**
> I realize what this part of the installation does. It's pretty straight forward. My question revolves around the fact that when I hit next at this portion of the installation it sits there and does nothing so I can't install.

Yea, it is aggriavating. 

Basically you need to just wait ... and wait ...

It is worse with gutsy (7.10). Gutsy not only searches windows, but all your partitions for windows and linux ... for all your users on each partition ... Just so you can see 'em all and then "Just say no"

Well, I have 10 so  ....

The need a "Skip this step" for sure, let alone "This next step might take a while ... a long while ..."

Edit: [Alternate CD](http://releases.ubuntu.com/feisty/)

---

### Post by Tb0ned on 2007-06-27
I do wait for the computer to fully finish processing but it just kinda fails and goes back to the Step 5 screen, and then I click on it again and the same thing happens. I think my computer is just retarded for some reason which I can't dig up. I'll try the alternate install CD and see how things work out.

---

### Post by tarek on 2007-06-27
> **Tb0ned said:**
> Alrighty, is the alternative CD Kubuntu or am I totally off here, or I'm a tard and can't find the alternative cd download which may very well be the case.

Don't be hard on yourself  ... You can get K/X/Ubuntu on Live CD or alternative CD.

Ubuntu:
Go to [http://releases.ubuntu.com/7.04/]("http://releases.ubuntu.com/7.04/")
You'll find there the alternative cd. You can download an ISO copy or torrent.

Kubuntu:
[http://www.kubuntu.com/download.php#latest]("http://www.kubuntu.com/download.php#latest")
Choose a one of the servers according to your location and then choose the alternative cd.

Xubuntu:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release")/

If you use torrent to download the ISO, check this out:
[http://cdimages.ubuntu.com/]("http://cdimages.ubuntu.com/")
You can find everything here

tarek

---

