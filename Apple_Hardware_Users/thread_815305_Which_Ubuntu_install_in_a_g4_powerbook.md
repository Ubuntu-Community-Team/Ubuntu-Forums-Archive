---
title: "Which Ubuntu install in a g4 powerbook?"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-01
Hi,

I've succesfully installed Ubuntu in several vaio and Toshiba laptops. I also use 7.04 in my desktop pc.

I now got a 12", g4, 1.33mhz, 512ram, 60gb powerbook. I'm fairly new to macs.

I want to install Ubuntu as my main OS, since that's what I mostly use. Some questions:

Which version should I use with this laptop? I hear only dapper is supported, is this an issue?

Will everything work?
Do I need the OSX disks to install?
How many partitions should I put to share files between the 2 OS? Which file system?

Is there anything else I should be aware of?

Many thanks for any help.

---

### Post by stream303 on 2008-06-01
Versions beyond Dapper are supported, it's just that support is no longer commercially available - it is up to the community of interested devs and users.

You can get these versions here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

If you are totally new to the scene, perhaps Feisty 7.04 "alternate" would be your best bet, although you could just jump right in and try Hardy 8.04.

You don't need the osx installation disks to install.  If you don't want to preserve anything of your old OSX installation, you just let Ubuntu's guided partitioning "use the whole disk".  It will automatically create the necessary partitions for you.  Of course this means that you should have backups of any data you wanted to retain.

The thing is, you may have to go in and manually edit some configuration files, so for some, Ubuntu PPC is not just a drop-in installation.  In any case, I'd always advise having OSX reinstall disks, and evaluate your own risk/comfort level.

Be aware that 3D and flash are not really natively supported, although there are alternatives like gnash for flash.  If this is a big issue, perhaps reconsider.

Many who want to dual boot, usually end up repartitioning and reinstalling OSX to a smaller portion of the disk, and then install Ubuntu later onto the "free space".  Another option is to install OSX to an external firewire drive, and put Ubuntu on the internal drive.

There are many options, but most require a little bit of forethought and perhaps some hand-holding along with perusing the stickies and forum archives.

I'm not trying to put you off to the installation, but just being honest about the reality, especially if you are very new to the whole apple scene.

That being said, my 12" ibook ran just fine with Feisty - I was just prepared to lose it all if something unforeseen was to happen.

---

### Post by frog_pilot on 2008-06-01
> **ruialexbarbosa said:**
> I want to install Ubuntu as my main OS, since that's what I mostly use.
There is a huge difference between ubuntu on PC and Ubuntu on MAC. It can run out of the box but mostly you need some tweaks.
[e.g. ibook g4 install tip (maybe its working for you too)]("http://ubuntuforums.org/showthread.php?t=798974")
Look here [https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC) in the "More Info" Section for all your questions.

> **ruialexbarbosa said:**
> Which version should I use with this laptop? I hear only dapper is supported, is this an issue?
You can use any version you want. The most recent could usally the best bet. Every ubuntu-powerpc-port release is supported. They only skipped commercial support from canonical.

> **ruialexbarbosa said:**
> Will everything work?
[Adobe FlashPlayer & others don't run on PowerPC, but there are replacements]("http://ubuntuforums.org/showthread.php?t=806987")

> **ruialexbarbosa said:**
> Do I need the OSX disks to install?
No, you dont.

> **ruialexbarbosa said:**
> How many partitions should I put to share files between the 2 OS?
At least one. The best should be HFSplus with journaling turned off.

> **ruialexbarbosa said:**
> Is there anything else I should be aware of?
[PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ")


I hope that helped... :)

---

### Post by ruialexbarbosa on 2008-06-01
Hummm... Very helpful guys... Thanks.

I just downloaded the latest version and it seems ok in the live version, most of it out of the box. I just don't seem to be able to control screen brightness. Maybe this will go when I install it? Do you know anything about this?

Sound and image are fine.

---

### Post by frog_pilot on 2008-06-01
> **ruialexbarbosa said:**
>  I just don't seem to be able to control screen brightness. Maybe this will go when I install it? Do you know anything about this?

Look at the ibookG4 thread I suggested in my last post. There is also information about this issue.

---

### Post by mfox on 2008-06-02
As noted in previous posts, if you need to run Mac software on the Linux side of your dual boot, the Mac-on-Linux program may not work on 8.04 but it apparently does on 7.10.  There is a way to recompile it from the binaries, but some people have had success and others not (I'm in the latter category).  One thing I have not tried is to install 7.10 including MOL and then upgrade to 8.04.  That would require more HD space, but you might get the best of both if you do it.

---

