---
title: "Installing Kubuntu over Ubuntu"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-07
I'm not sure how to this

I'm trying to install Kubuntu over ubuntu, I have kubuntu in my disk drive, but instead of autorun it just  opens the folder wth all the programs that were in the iSO. How do I use it to install it? I decided to install Kubuntu because it has a cleaner interface and everything.


I know, I'm pretty much gong in circles but, the title basically says all.

---

### Post by GrumpyBob on 2007-10-07
You should be able to install  KDE on top of Ubuntu via synaptic.  You would then be able to choose between both Gnome and KDE.  I've done this in the past, though I actually prefer Gnome these days.

Robert

---

### Post by por100pre1 on 2007-10-07
If you have enough disk space you can do this instead:

```
sudo aptitude install kubuntu-desktop
```

---

### Post by Majorix on 2007-10-07
> **por100pre1 said:**
> If you have enough disk space you can do this instead:

```
sudo aptitude install kubuntu-desktop
```

What is the difference with that and the Synaptic method described? :confused:

---

### Post by TaiQui on 2007-10-07
How do I open synaptic? and I want to use Kubuntu 7.10, and I have it on a CD, and will KDE install everything in Kubuntu? I dunno,  its probably the same thing, I'm just confused

Edit: I did what por said, heres what I got

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

---

### Post by gigaferz on 2007-10-07
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

i dont know if you can get it from your cd.. i understand what you are trying to do.

and actually it'll be a little different than the Kubuntu installation.... why dont you back up your files to a cd and give it a try??

---

### Post by stevebakerj on 2007-10-07
Do you have Ubuntu 7.10 (Gutsy) installed, if not you will need to do a complete install of Kubuntu 7.10. So Boot from the Live CD (Kubuntu 7.10) and do a manual install over your existing Ubuntu.

---

### Post by TaiQui on 2007-10-07
Did what it says and got this.

EDIT:  have Ubuntu 7.04 , so I'll listen to steve

EDIT2: Steve, how do I do a manual install?
ev
```
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]  
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/universe Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
```

---

### Post by equal on 2007-10-07
> **TaiQui said:**
> How do I open synaptic? and I want to use Kubuntu 7.10, and I have it on a CD, and will KDE install everything in Kubuntu? I dunno,  its probably the same thing, I'm just confused

Edit: I did what por said, heres what I got

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Well it's fairly easy to fix that, simply do exactly what it says. In the Terminal, type out:

```
sudo dpkg --configure -a
```

You say you want to install Kubuntu 7.10. I'll assume that you currently have Ubuntu 7.04 installed then? If that's the case, you would probably be better off installing the system fresh, to save a bit of time. While it's true that you can install Kubuntu over Ubuntu, I never liked doing this. It doesn't work exactly the same afterwards.

So, first question, did you make your /home directory a separate partition? If you did, this will be a breeze. Simply put the CD in your CD drive and restart your computer, and let the auto installation take over. Make sure you don't format the partition you use for /home though, just remount it as /home during the drive selection segment. 

Hope this works for you!

---

### Post by Wiebelhaus on 2007-10-07
I'll forewarn you, It sucks , NOT the OS or DE but that method adds both DE's programs and makes it very confusing and buggy.

---

### Post by gigaferz on 2007-10-07
why dont you wait until the official release, ???

is just a week or so...

what is the hurry??

---

### Post by aysiu on 2007-10-07
There are a few ways to accomplish this:

1. **Install Kubuntu 7.10 over Ubuntu 7.04 with a fresh install**
I'd *highly* recommend this method, as it'll take only a half hour or so.

2. **Remove Ubuntu 7.04, install Kubuntu 7.04, and then upgrade to 7.10**
I'd recommend *against* this method, as it'll take hours to do, even on a high-speed connection.

3. **Install Kubuntu 7.04 in addition to Ubuntu 7.04, and then upgrade to 7.10**
I'd also recommend against this method, but it may take slightly less time than method #2, since you won't have to remove Ubuntu first.

In the meantime, paste this command into the terminal: ```
sudo dpkg --configure -a
```

---

### Post by TaiQui on 2007-10-07
I choose, one, because theres really no use to dual boot ubuntu and kubuntu

---

### Post by bodhi.zazen on 2007-10-07
I am not sure what you want exactly, so here are your options.

1. Install kubuntu. Just like Ubuntu, you need to boot to the CD and follow the installation instructions. Go ahead and install to the old Ubuntu partitions, format them as part of the install.

This will be a fresh install and has the advantage of reducing the number of duplicate applications.

2. Install kubuntu-desktop onto Ubuntu. This will not harm anything, you can choose to run either gnome or KDE at the log in screen. It will use more hard drive space and there will be some duplication of applications ...

The advantage is you do not need to re-install.

First, however you need to fix apt-get.

Run this command :

```
sudo dpkg --configure -a
```

Then install kubuntu-desktop :)

---

### Post by aysiu on 2007-10-07
> **TaiQui said:**
> I choose, one, because theres really no use to dual boot ubuntu and kubuntu
Well, technically, it's not dual-booting.

It's a single boot with the option of two different sessions, but that's only #3.

Both #1 and #2 would leave you with only Kubuntu (not Ubuntu also). The big difference is that method #1 would take a half hour and method #2 would take three or four hours.

---

### Post by TaiQui on 2007-10-07
Does it need 2 heard drives? Probably not, but, with a fresh install do I get to preview Kubuntu too?

---

### Post by aysiu on 2007-10-07
No. None of the methods described above require two hard drives. Even if you have both Ubuntu and Kubuntu installed, it is one installation with two available sessions you can log into (Gnome or KDE).

With a fresh install, you don't get to preview Kubuntu--you are *installing* Kubuntu. Kubuntu is all that will be there. It won't be previewing it. It will be experiencing it.

If you want to preview Kubuntu, just pop the Kubuntu 7.10 CD in and boot off it. It'll create a live session that won't affect your hard drive. When you're ready to install after the preview, just click the *Install* button on the desktop.

---

### Post by TaiQui on 2007-10-07
Hey, thakns, I'll try the CD one.

---

### Post by por100pre1 on 2007-10-07
> **TaiQui said:**
> How do I open synaptic? and I want to use Kubuntu 7.10, and I have it on a CD, and will KDE install everything in Kubuntu? I dunno,  its probably the same thing, I'm just confused

Edit: I did what por said, heres what I got

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

```
sudo dpkg --configure -a
```

> **Majorix said:**
> What is the difference with that and the Synaptic method described? :confused:

Just one command. :-k

---

### Post by Tripletaco on 2007-10-08
The other day I installed Kubuntu 7.04 over ubuntu 7.04 through Synaptics.  I read some where you could just change the Session to go back and forth between the two.  Was that ever a mistake!  My Linux Partition on a Dual boot with windows XP is just a mix of both Kubuntu and Ubuntu now. My wireless won't work.  It worked good before.

So then I thought I'd fix it by downloading Kubuntu 7.10.  can't remember what tribe.  Think 4.  I don't like what I have now.  Wish I could just go back to Gnome 7.04.

---

### Post by bodhi.zazen on 2007-10-08
> **Tripletaco said:**
> The other day I installed Kubuntu 7.04 over ubuntu 7.04 through Synaptics.  I read some where you could just change the Session to go back and forth between the two.  Was that ever a mistake!  My Linux Partition on a Dual boot with windows XP is just a mix of both Kubuntu and Ubuntu now. My wireless won't work.  It worked good before.

So then I thought I'd fix it by downloading Kubuntu 7.10.  can't remember what tribe.  Think 4.  I don't like what I have now.  Wish I could just go back to Gnome 7.04.

You could re-install Ubuntu 7.04 ...

---

### Post by Tripletaco on 2007-10-08
How do I do that and replace what I have on my Ubuntu partition of my dual boot?

---

### Post by bodhi.zazen on 2007-10-08
Boot 7.04 

Select install ...

On the partitioning screen choose "manual"

select your current Ubuntu partition as the new root partition ( / ) in which to install, format the partition.

continue with the installation.

---

