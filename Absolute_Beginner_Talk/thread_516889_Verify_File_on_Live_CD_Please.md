---
title: "Verify File on Live CD Please ?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by ddavenpo on 2007-08-03
Hi - I am trying to try out UBUNTU Live CD for the first time but having an issue that I can not get either of my PCs to boot from it.  As far as I can tell I downloaded it and burned the CD properly but neither PC will boot to it, even when I set their boot path to the CD drive and I can see it is trying to boot from it (both PCs happily boot into XP if I let them).  I was wondering if there is any way to verify the CD or the file on it.  I have a single file type WinRAR, called  ubuntu-6.06.1-desktop-i386 with size showing as 715,172KB.
Does this look correct please ?
Many thanks,
ddavenpo

---

### Post by Rocket2DMn on 2007-08-03
You should check the md5sum of the iso image
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against

Assuming that checks out, you should burn the image to a cd at a slow speed, like 4x, to prevent write errors, and use quality media if you can.
Following these steps help ensure that the cd comes out correctly.

If you have problems with the live cd after trying these steps and are planning to install, you should use the alternate cd which provides a text based install (no live session).
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box for alternate cd at the bottom.

---

### Post by overdrank on 2007-08-03
> **ddavenpo said:**
> Hi - I am trying to try out UBUNTU Live CD for the first time but having an issue that I can not get either of my PCs to boot from it.  As far as I can tell I downloaded it and burned the CD properly but neither PC will boot to it, even when I set their boot path to the CD drive and I can see it is trying to boot from it (both PCs happily boot into XP if I let them).  I was wondering if there is any way to verify the CD or the file on it.  I have a single file type WinRAR, called  ubuntu-6.06.1-desktop-i386 with size showing as 715,172KB.
Does this look correct please ?
Many thanks,
ddavenpo

Hi it should be a iso file. Have you tried the "how to " in burning the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And you can get the iso file here 
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Good luck and welcome. :popcorn:

---

### Post by az on 2007-08-03
> **overdrank said:**
> Hi it should be a iso file. Have you tried the "how to " in burning the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And you can get the iso file here 
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Good luck and welcome. :popcorn:

To be more precise, the cd should not contain one file.  It should be *made out of* the iso file.  Once that iso image is burned to the disk (not just copied onto the disk) you should see a bunch of files and directories on the disk when you browse it before booting from it.  See the howto mentioned above.

---

### Post by ddavenpo on 2007-08-10
Thanks to everyone for their suggestions so far -  having read the appreopriate links I now know more, but still can't burn my disk properly  :-(

My downloads are fine - v6.06 and v7.04 both download and pass MD5 checksum check (using suggested check program).  My trouble is still disk burning I think.

I have tried using the suggested InfraRecorder but I have been unable to get it to register any of my drives.  I have tried it on a Win98/Me and an XP machine - neither installs can see any disk, evem afyter doing a regostry change suggested on the InfraRecorder help site (I see others have similar disk visibility issues too).

So I gave up on InfraRecorder and went back to my existing IBM RecordNow on the XP Machine and Roxio on the WIn98/Me machine.  Both contiunue to 'copy' the iso file as a single file, even if I use the Roxio option 'Create a Bootable Disk'  :-(

So can someone please confirm what I should be doing exactly - should I be supplying the single iso file to the burner and the burner program should somehow know it should uncompress it before burning it ?  If so how does it know to do this ?  Am I supposed to uncompress first ?  How ?  If burner decompresses it how does it fit it onto the CD after doing so as the iso file is almost 700MB itself ?  Sorry if these are stupid questions but this is the bit confusing me (and going wrong !)

Many thanks,
ddavenpo

---

### Post by jgrabham on 2007-08-10
Theres a program called ISOrecorder for windows xp

It works for me

EDIT-heres the link - [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

use this and it should work fine, burn at 8x and use high quality CDrs

---

### Post by overdrank on 2007-08-10
> **ddavenpo said:**
> Thanks to everyone for their suggestions so far -  having read the appreopriate links I now know more, but still can't burn my disk properly  :-(

My downloads are fine - v6.06 and v7.04 both download and pass MD5 checksum check (using suggested check program).  My trouble is still disk burning I think.

I have tried using the suggested InfraRecorder but I have been unable to get it to register any of my drives.  I have tried it on a Win98/Me and an XP machine - neither installs can see any disk, evem afyter doing a regostry change suggested on the InfraRecorder help site (I see others have similar disk visibility issues too).

So I gave up on InfraRecorder and went back to my existing IBM RecordNow on the XP Machine and Roxio on the WIn98/Me machine.  Both contiunue to 'copy' the iso file as a single file, even if I use the Roxio option 'Create a Bootable Disk'  :-(

So can someone please confirm what I should be doing exactly - should I be supplying the single iso file to the burner and the burner program should somehow know it should uncompress it before burning it ?  If so how does it know to do this ?  Am I supposed to uncompress first ?  How ?  If burner decompresses it how does it fit it onto the CD after doing so as the iso file is almost 700MB itself ?  Sorry if these are stupid questions but this is the bit confusing me (and going wrong !)

Many thanks,
ddavenpo

HI then maybe you can take a look at this thread and maybe try Wubi or the other links to install Ubuntu. Good luck! :)

[http://ubuntuforums.org/showthread.php?t=522470](http://ubuntuforums.org/showthread.php?t=522470)

---

### Post by ddavenpo on 2007-08-11
Thanks to all for their responses - I have at last managed to burn a proper CD.  I realised where I was going wrong with IBM RecordNow! - I was just making data disks not bootable images, - the process for which was slightlydifferent.

I am typing this from Ubuntu - at last !

I'm still running live though - next step wil be to install it for dual boot - ideally Microsfot as defaul, as alI the other memebrs of the family (who use this PC) have no idea what Linux/Ubuntu is and so need to default boot into MS, oterwise they will not have a clue what to do if presented with a choice and Ubuntu gets a mention.

Thanks again - I hope to not have to bother you all again, but have this feeling I might :-)
ddavenpo

---

