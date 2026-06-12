---
title: "Ubuntu disk will not boot"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by actionheights on 2007-08-11
Hi all, 

First time posting , hopefully it will be my last in the "Absolute Beginner Talk"

So I've read all the common pitfalls with Burning ISO / Setting Boot Order etc. and none seem to help.  I'm wondering if there's something wrong with my disk or files.

Here's what I've done so far.

Burn the ISO with CDBurnerXP.  It completes fine.  I can open the disk in Windows.  ie that "Browser" menu thing with firefox, thunderbird, etc.  
There are 11 folders and 8 files on the base level of the disk.  (I've looked at a screenshot in the how-to's and it looks correct ) 
When I reboot it skips to Windows, after a delayed blinking underscore thingy in the top left.
I've set the CD drive as the primary boot device, gone to the boot menu (f12) ( I have a dell d610 , although this probably isn't an issue) , removed the HDD as a boot device in bios(prompting a no boot devices recognized hit f1 to retry , f2 to enter bios)

I installed XP w/sp2 off a disk so I know the booting works , which leads me to believe it's my disk

I know some have mentioned the md5sum text file.  I open it and there's ... a lot of hex and files (about 50 lines extending into almost infinity)

If I've burned the ISO wrong, that's embarassing , but it would be helpful if someone could specify a program (if cdburnerxp works that's great) , and step by step so I don't burn the ISO wrong again.  Something along the lines of settings, max burn speed , finalize or not, make disk bootable or not, etc.

It's Ubuntu 7.04.

Thanks for the guidance.

---

### Post by erfahren on 2007-08-11
for burning ISOs in Windows I always used this: [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
it's small and freeware. I've never had any problems with it. Once installed you just stick a CD in, right-click on the .iso and "Burn to CD"

> 
I know some have mentioned the md5sum text file. I open it and there's ... a lot of hex and files (about 50 lines extending into almost infinity)

that shouldn't be. Checksums aren't *that* long. MD5 sums are here: [http://releases.ubuntu.com/7.04/MD5SUMS](http://releases.ubuntu.com/7.04/MD5SUMS)

This app should work well to check it in Windows (again, once installed right-click on .iso and "Hash file": [http://www.whitsoftdev.com/md5/](http://www.whitsoftdev.com/md5/)

I'd definitely try burning it again just to make sure.

---

### Post by actionheights on 2007-08-11
thanks so much for the help

I used your iso program to burn it this time, and did so at 8x this time.

Installation went off without a hitch.

Wireless drivers\ network detected perfectly.

On to greater things.

---

### Post by erfahren on 2007-08-11
cool ! 

a few helpful links that may come in handy:
[Documentation for Ubuntu 7.04](https://help.ubuntu.com/7.04/)
[ubuntuguide.org wiki](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

for resolved problems they like it if you edit your original post and put [SOLVED] in the subject line. It helps people searching later on.

have fun!

---

