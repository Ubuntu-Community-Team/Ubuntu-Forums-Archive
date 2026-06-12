---
title: "Really worried that my Windows drive is gone....."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Valnorsith on 2007-12-08
My friend installed Ubuntu on my laptop, halving the hard drive with the original Vista that was on it. She had done the same to her computer, though it had XP, and assured me that all my files would be safe.

However, I've been attempting to mount my Windows half of the hard drive and things aren't going right and I am afraid that possibly my Windows system was completely wiped off the laptop, though my friend did everything exactly like on hers and hers was fine.

First of all is that on GRUB, or whatever the page is that allows you to chose what system to boot up on, Vista doesn't show up there at all. Only Ubuntu.

When I attempted to mount Windows via the terminal, following walkthroughs online, I need to obviously find the correct code to do so, so I input fdisk -l. This is what comes up.

xxx@xxx-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9730    76613632   83  Linux


Does this mean that Vista is completely gone and, since I stupidly don't have up to date backups of my files on disk, so are they?

---

### Post by nikoPSK on 2007-12-08
pretty sure it's dead. Sorry, but windows deserved it:p

---

### Post by PmDematagoda on 2007-12-08
Sadly it does seem that Windows and all your backups are gone, but just to make sure, install Gparted using:-
```

sudo apt-get install gparted
```

Then start Gparted in System>Administration>GNOME Partition Editor, after it starts post a screenshot of what you see using Alt+PrntScrn.

---

### Post by nikoPSK on 2007-12-08
Sorry, I shoul've mentioned that. But Im 99.9% sure it's gone.

---

### Post by Valnorsith on 2007-12-08
*sigh* Well, thank you anyways. This isn't the first time I lost my stuff and probably won't be the last. I just feel stupid for not making back-ups for everything first.

At least the most important few files I do have on disk, though not completely up to date. The major one I feared for is a story me and my friend have been working on for long over a year now and is well over 300 pages total. At least THAT I know I have on disk somewhere in my room. And some of the other stories I have printed out and randomly all over my room.

All my other documents and stories I've been writing, I'll just have to redo if I can. At least those I never actually could seem to get finished, though it'll be a pain rewriting what I already had done since I spent a lot of time on those, trying to get them to sound good. (Yes, I am a writer by hobby)

Fortunately, none of the pictures on it were that important, just ones I found online and liked for the most part. I can find them all again... just will take time.

Anyways, you're all tired of hearing me ramble if you even decide to completely read this thing so I'll stop now and start digging out my cds and start searching online.


-------------------------------------


Here is the screenshot:

---

### Post by PmDematagoda on 2007-12-08
Yep, Windows is gone, sorry.

But there is a problem, why are you using ext2 instead of ext3?

---

### Post by -grubby on 2007-12-08
you can always use some kind of file recovery program as long as you haven't overwritten a lot

install one by:

```
sudo apt-get install testdisk
```

---

### Post by Valnorsith on 2007-12-08
> **PmDematagoda said:**
> Yep, Windows is gone, sorry.

But there is a problem, why are you using ext2 instead of ext3?

I really have no idea. I'm a complete noob with all of this and in some ways, wish I stuck with Vista, though it is a piece of crap. I SOMEWHAT knew what I was doing with that.

As for Ubuntu, I'm relying on my friend who knows more about it than me and the forums really.

---

### Post by Valnorsith on 2007-12-08
> **nathangrubb said:**
> you can always use some kind of file recovery program as long as you haven't overwritten a lot

install one by:

```
sudo apt-get install testdisk
```

I'll attempt that to see if it will work at all.

---

### Post by PmDematagoda on 2007-12-08
Hmm, but I would recommend ext3 as opposed to ext2 especially since ext3 has more data consistency as it has a journal file as opposed to ext2 which does not have such a system.

But anyway, what is done is done, but as it is, it is recommended to use ext3 as opposed to ext2, so I suggest that the next time you install Ubuntu that you select ext3 as the File System.

---

### Post by Valnorsith on 2007-12-08
Okay, nathangrubb, I did as you said and used that command. This is what I got back:

xxx@xxx-laptop:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs9
The following NEW packages will be installed:
  libntfs9 testdisk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 818kB of archives.
After unpacking 3006kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libntfs9 1.13.1-6 [133kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe testdisk 6.6-1 [685kB]
Fetched 818kB in 2s (377kB/s)    
Selecting previously deselected package libntfs9.
(Reading database ... 94137 files and directories currently installed.)
Unpacking libntfs9 (from .../libntfs9_1.13.1-6_i386.deb) ...
Selecting previously deselected package testdisk.
Unpacking testdisk (from .../testdisk_6.6-1_i386.deb) ...
Setting up libntfs9 (1.13.1-6) ...

Setting up testdisk (6.6-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
xxx@xxx-laptop:~$

Now, what do I do? (Don't want to do something stupid and screw more stuff up)

---

### Post by akiratheoni on 2007-12-08
> **Valnorsith said:**
> Okay, nathangrubb, I did as you said and used that command. This is what I got back:

xxx@xxx-laptop:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs9
The following NEW packages will be installed:
  libntfs9 testdisk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 818kB of archives.
After unpacking 3006kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libntfs9 1.13.1-6 [133kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe testdisk 6.6-1 [685kB]
Fetched 818kB in 2s (377kB/s)    
Selecting previously deselected package libntfs9.
(Reading database ... 94137 files and directories currently installed.)
Unpacking libntfs9 (from .../libntfs9_1.13.1-6_i386.deb) ...
Selecting previously deselected package testdisk.
Unpacking testdisk (from .../testdisk_6.6-1_i386.deb) ...
Setting up libntfs9 (1.13.1-6) ...

Setting up testdisk (6.6-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
xxx@xxx-laptop:~$

Now, what do I do? (Don't want to do something stupid and screw more stuff up)

That means it installed. Try this command:

```
testdisk
```

and it will open up.

---

### Post by Valnorsith on 2007-12-08
Okay. I have done so, now what? I'm afraid you're going to need to walk me through this.

---

### Post by akiratheoni on 2007-12-08
> **Valnorsith said:**
> Okay. I have done so, now what? I'm afraid you're going to need to walk me through this.

Unfortunately that's all I know (I just installed the program to help you open it up :P)

Maybe this will help:

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

---

### Post by Valnorsith on 2007-12-08
Okay. Thank you very much for your help. *gives a hug and gives you a cookie*

---

### Post by SunnyRabbiera on 2007-12-08
well if you need guides to linux they are easy to look up if you dont feel like going back to vista

---

