---
title: "Live CD Won't Boot - iMac Intel"
date: 2006-07-03
forum: Apple PPC Users
---

### Post by Greywhind on 2006-07-03
I previously downloaded the latest x86 Live CD ISO from this site and burned it to disc - but when I restart on my 17-inch Intel iMac (with latest firmware, bootcamp, and rEFIt) and hold "C" down, it just boots normally, not to the CD (both with and without rEFIt configured). Also, when I use rEFIt to try to boot to the CD, it tells me that it failed to load the loader.

Anyone know why? Is it a corrupted CD? Should I download a different version? Please help.

Also, I used diskutil to resize my volume to have 3 parts (mac, linux, windows in that order), as outlined on [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) --- is this a problem for installing Ubuntu?

If so, what should I do instead and how do I reverse it so that I only have one partition for Mac and no others?

---

### Post by Greywhind on 2006-07-04
I downloaded the Live CD from [http://www.mactel-linux.org/wiki/Main_Page/](http://www.mactel-linux.org/wiki/Main_Page/), and it successfully booted.

But when I used startx to show the Ubuntu desktop, there was no install shortcut as shown here: [http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/](http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/).

I couldn't figure out any way to install from the LiveCD without that shortcut, since I can't find the file itself...

Any tips? Should I just burn a third CD, this time straight from Ubuntu? Or is there a way to install from the current one even without the shortcut there?

---

### Post by chasisaac on 2006-07-04
I just finished writing a detailed install guide for a mactel computer. I had lots of headaches getting it to boot correctly. 

Check out

[http://www.planetisaac.com/articles/ubuntuinstall.html](http://www.planetisaac.com/articles/ubuntuinstall.html)

ci

---

### Post by grilla on 2006-07-04
i have the exact same problem on my 1.83ghz macbook pro. i have burned 3 cd's and one dvd without success. i cannot get them to boot. please contact me at [email]gary.conrad@gmail.com[/email] if you have any success.

---

### Post by Greywhind on 2006-07-04
Those instructions look very good - but I don't have that install icon on the desktop when booting from the LiveCD. I'll probably just download another one, this time from Ubuntu officially.

Also, I'm not clear on the requirements for the Ubuntu partition - should it be as large as possible so that programs can be installed? Or is it just for the OS itself and programs/files can be read from other partitions? If the 2nd is the case, am I correct that it should be 9.5 gb?

---

### Post by chasisaac on 2006-07-04
[QUOTE=Greywhind]Those instructions look very good - but I don't have that install icon on the desktop when booting from the LiveCD. I'll probably just download another one, this time from Ubuntu officially.

Also, I'm not clear on the requirements for the Ubuntu partition - should it be as large as possible so that programs can be installed? Or is it just for the OS itself and programs/files can be read from other partitions? If the 2nd is the case, am I correct that it should be 9.5 gb?[/QUOTE]


If you have acess to another Mac (or go to Apple Store) and burn from another Macintosh. 

IF the other one does work . . . then complain to Apple and get a new superdrive drive. 

Also what are you using to burn?

---

### Post by Greywhind on 2006-07-04
The first time I burned a CD, which didn't work, I was using a G4 Cube (prior to buying this iMac) and an external burner. The 2nd time, the burning worked just fine - I was using this Intel iMac. I think the source of the disk image, however, was missing the installer shortcut.

---

### Post by Greywhind on 2006-07-05
I successfully installed linux after the third CD burning, and it's working really well. :grin:

---

### Post by st-grendae on 2008-01-05
im using the new imac intel. when i boot ubuntu  from the live cd it gets to the installation page but when i press enter to select the option nothing happens???? it is really annoying me so please tell me what to do.

---

