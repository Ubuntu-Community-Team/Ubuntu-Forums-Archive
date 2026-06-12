---
title: "Easiest md5 utility for Windows?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Bartender on 2006-02-03
I thought I'd found a simple md5 check utility for Windows - md5summer.  I used it to compare a Kubuntu download against the checksum listed on the download website and they matched.  NTI (the burner utility that came with the Sony DVD drive) recognized the download as an .iso and seemed to know what to do with it.  Kubuntu installed successfully from the CD.
A few weeks later, I decided to try md5summer on the CD.  This is in Windows...put it in the tray, pointed md5summer at D:\ drive, but it saw several files, not the one big file like in the download folder.  Just for the heck of it, I asked it to checksum everything.  Of course none of them matched the original.  
I'm assuming NTI did the right thing with the data, but the CD doesn't look like one big file in md5summer or in Explorer, so I don't know what I'm doing wrong.
Any ideas, please?

---

### Post by Adrian on 2006-02-03
You are supposed to check the integrity of the large ISO you download, **before** you burn it (to see if the transfer was correct). If I understand you correctly, you tried to verify the integrity of the contents of the CD? That will not work, since the ISO file is not on the CD (it has transformed into an entire distribution :) ).

hkSFV is nice, by the way:
[http://www.big-o-software.com/products/hksfv/](http://www.big-o-software.com/products/hksfv/)

---

### Post by 5-HT on 2006-02-03
Hi, 

The .iso you downloaded is disc image of the ubuntu install cd. As a simplistic explanation, this single file contains all the data on the cd.

When you burned the .iso it was as a disc image, which is necessary to have a functional install cd, not as a data cd containing one file (the .iso).

The md5sums you created and compared were those of the .iso.

When you are now trying to check the md5sum of the cd however, the data on the cd is not stored in that single .iso. Instead, the cd has many files which are an exact copy of those contained within the .iso.


If you would like to check the cd integrity, what is needed is to recreate that disc image from the cd.


Do do so using Ubuntu is quite easy:

```
 dd if=<cdrom device> of=<path_to_new_iso.iso> 
```

For example: 

If your cdrom is /dev/hdc, the following will create the disk image (called ubuntu_burn_check.iso) in your home folder:

```
 dd if=/dev/hdc of=~/ubuntu_burn_check.iso 
```


After you've recreated the .iso, then you can check it's md5sum and if the burn went correctly, the sums should match those of the iso you originally downloaded.


If you'd like to do the same from windows, I wouldn't know the best route offhand but one way would probably be to use a burning suite to burn the contents of the cd to a disc image(making sure it does so as an iso).

*EDIT: Didn't notice Adrian beat me to it until posted.

HTH

---

### Post by Bartender on 2006-02-04
Hi, guys -
Thanks for the responses.  Turns out this is one of the things that works better in Linux.  
I wrote to Luke Pascoe, who invented Md5Summer.  He confirmed that the .iso and the CD are not the same, a distinction I didn't understand until he spelled it out to me.  He added that while Linux provides a method of looking at the burned CD and comparing it to the original md5 checksum, he doesn't know of a workaround for Windows users.  His only suggestion - websites supplying downloads should supply two sets of md5 checksums, one for the download and another group of checksums for the files that appear on the CD.
Does Ubuntu/Kubuntu do this?  I went to a US Ubuntu download site and only found the six .iso checksums.
When Windows users get on these forums and ask for help with their downloads it isn't at all helpful to give them Linux-based instructions.  That's what happens too often.  I'd like to write up a "How-To for Windows Users" on this but need to assemble the best info I can.  Any ideas would be appreciated.

---

### Post by Adrian on 2006-02-04
[QUOTE=Bartender]When Windows users get on these forums and ask for help with their downloads it isn't at all helpful to give them Linux-based instructions.  That's what happens too often.  I'd like to write up a "How-To for Windows Users" on this but need to assemble the best info I can.  Any ideas would be appreciated.[/QUOTE]

Check out the Windows program i linked to in my post above.
0. Install the program
1. Put the md5 file and the ISO in the same directory
2. Double click on the md5 file (from Windows Explorer), and hkSFV will start and check the integrity of the ISO.

That is how I do it when I'm on Windows.

---

### Post by GTvulse on 2006-02-04
> **Bartender]
Does Ubuntu/Kubuntu do this? I went to a US Ubuntu download site and only found the six .iso checksums.[/quote]

Why yes. Look at the root of the CD. (Or disc image if that's what you want to deal with. [Daemon Tools]("http://www.daemon-tools.cc/") is a wonderful MS Windows tool, and "mount -o loop" is your friend in GNU/Linux said:**
> . ;-)).

[quote=Bartender]
When Windows users get on these forums and ask for help with their downloads it isn't at all helpful to give them Linux-based instructions. That's what happens too often. I'd like to write up a "How-To for Windows Users" on this but need to assemble the best info I can. Any ideas would be appreciated.


The installer CD is **self-checking** That is, have you noticed that it takes a lot of time going through all the directories contained in the cd at some point during the installation process? ***The installer is checking the MD5 checksums of all files contained within it***. If the actual files are damaged in the CD, it will refuse to install. 

Now, CD **burning** can fail if you write the image data at speeds higher than 8x (I would say 4x to be *very* conservative) because the directory structure within the disc images is more complex than the usual stuff you throw at the el-cheapo burners we all buy nowadays. The laser head inside those widgets can only move so fast to do an accurate etching of the optical disc. The manufacturer may say that it burns CDs as 56x, but be certain that the heads will start to wobble if going faster than, say 16x, resulting in layout and filesystem- structure defects in the disc that are impossible to detect until you try to read the data out, even if the data is there and passes the integrity checks. On the other hand, if your burner is a Plextor or a Nakamichi, I would be very worried...

---

### Post by Bartender on 2006-02-04
[QUOTE=dradul]The installer CD is **self-checking** That is, have you noticed that it takes a lot of time going through all the directories contained in the cd at some point during the installation process? ***The installer is checking the MD5 checksums of all files contained within it***. If the actual files are damaged in the CD, it will refuse to install. [/QUOTE]

dradul -
Not sure I followed everything in your post.  Are you saying there's no need to check the burned CD's md5's because if it's not right the installer will stop?  I didn't know the installer was self-checking.  
It'd still be nice for a beginner to be able to verify the CD.  Let's say he or she's downloaded the .iso, checked the md5, burned to a CD, the installer's doing its thing, then suddenly it stops.  How do we know whether it's the CD or hardware incompatibility?
You lost me when you said to look at the root of the CD.  What's that?  That's the first level, right?  Before you Open or Explore or left-click on the file/folder?

adrian -
I'll try out hksfv.  Actually, I've got about eight different md5 checkers to try out, but md5summer works good and is easy for Windows mouse jockeys.

The fact that I'm not sure I understand what you guys are saying illustrates my initial point...I think there's a need for a guide that the "Average Windows User" (AWU) can follow.  

If the CD md5's aren't available from the download sites, what about getting the md5's that I need from the Ubuntu community?
There are six different versions of each release (AMD64, Mac, i-386, then installs and LiveCD's) and three different releases (Ubuntu, Kubuntu, and Xubuntu).  So that makes eighteen sets of CD md5's (there are about eight or nine files per CD if I remember correctly) that I'd need to collect for a guide.  Of course all of them would change when Dapper comes out, but still.

If a guide existed for 1) installing & using a Windows-based md5 checker, 2) checking the download, and 3) checking the CD there would be less confusion.  I wish I'd had something like that a coupla months ago during my first go-round.
I'm getting way off course for this forum.  My apologies.  Any moderators cruising past, I'd appreciate a PM with some guidance on how to proceed.  I'm on a mission

---

### Post by GTvulse on 2006-02-04
> **Bartender]
Not sure I followed everything in your post. Are you saying there's no need to check the burned CD's md5's because if it's not right the installer will stop? I didn't know the installer was self-checking.
[/quote]

No, not at all said:**
> 
It'd still be nice for a beginner to be able to verify the CD. Let's say he or she's downloaded the .iso, checked the md5, burned to a CD, the installer's doing its thing, then suddenly it stops. How do we know whether it's the CD or hardware incompatibility?


All those graphical tools to check MD5 hashes under MS Windows are braindead; they default to checking files in text mode while they should be using binary mode (in POSIX  OSs such as GNU/Linux, everything is a file and everything is binary). You best bet is using a win32 version of md5sum, a part of GNU coreutils[1]. Make sure to use the "-b" flag when checking md5 hashes. 

Any CD mastering software worth the money you paid for it should have a recording verification option. If the CD verification done immediately after burning the disc is successful then you may have a hardware problem (and btw older ASUS mainboards are particularly nasty with Linux, can you update your BIOS?).

And yes, the root is the top node of a filesystem.

[1] There are native win32 versions at [http://gnuwin32.sourceforge.net/](http://gnuwin32.sourceforge.net/) and [http://unxutils.sourceforge.net/](http://unxutils.sourceforge.net/)

---

### Post by Bartender on 2006-02-04
I've always asked the burn utilities (have only used Nero and NTI so far) to verify after writing, but never knew what that really meant, how dependable the process was, etc.
Do the burn utilities use some form of md5?

The machine described in my sig is my "learn-as-I-screw-up" Linux machine.  The BIOS was updated using the tried-and-true floppy method.  That was a little scary for me but went well.  It's running W2K/Ubuntu.  So I'm not having a problem right now (except for my near-total Linux ignorance).  The impetus behind the post was my desire to help other newbs get to the point of having a viable CD without each one of them having to re-invent the wheel.  So far my quest for answers has only generated more questions ;)

---

### Post by GTvulse on 2006-02-05
[QUOTE=Bartender]I've always asked the burn utilities (have only used Nero and NTI so far) to verify after writing, but never knew what that really meant, how dependable the process was, etc.
Do the burn utilities use some form of md5?
[/quote]

No, no md5, but they do someting as important. They verify that the data in the disc is the same data as in the disc image and that the pysical layout of the data in the disc is correct.

> 
The machine described in my sig is my "learn-as-I-screw-up" Linux machine.  The BIOS was updated using the tried-and-true floppy method.  That was a little scary for me but went well.  It's running W2K/Ubuntu.  So I'm not having a problem right now (except for my near-total Linux ignorance).  The impetus behind the post was my desire to help other newbs get to the point of having a viable CD without each one of them having to re-invent the wheel.  So far my quest for answers has only generated more questions ;)


Aha! Then, as you have verified the discs after burning them with Nero or NTI, we can write off physical problems in the disc due to a bad burn. If the disc image MD5 passes, then the data within it is correct as well and this is confirmed by the self-verification routines in the installer. Sooo, I think the problem is a conflict with your BIOS even if already updated. Try installing Ubuntu with the following command line at the "boot:" prompt:
```

linux noapic nolapic irqdebug=no

```

---

### Post by BoyOfDestiny on 2006-02-05
the checksum for the iso, think of the iso as the blue print for your cd.

If the iso has a bad checksum, all the cds you make from it will be bad.

The md5 file on the cd, checks the files on the disc. This is to verify nothing went wrong during the burning process.

In the next version of ubuntu (dapper) they have a nice option for "verify this disc" with the installer options.

---

### Post by Bartender on 2006-02-07
[QUOTE=BoyOfDestiny]In the next version of ubuntu (dapper) they have a nice option for "verify this disc" with the installer options.[/QUOTE]

Thanks for that news flash!  I need to learn more about md5's but maybe won't worry so much about writing a guide for other neophytes.

---

