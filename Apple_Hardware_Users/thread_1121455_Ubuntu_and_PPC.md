---
title: "Ubuntu and PPC"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by Davirus on 2009-04-10
I know this have been discussed before since I have saw a lot of threads about it here but nothing have solved yet my problem.

Im a linux lover my self (I use OSX anyway so Im not really a linux experienced user) and my roommate its experiencing some performance problems with his iBook so I suggested him to install ubuntu since is a nice system and a really easy one to use for him.

So I searched around the site for the PPC distro and downloaded "ubuntu-8.10-alternate-powerpc.iso" and burned it into a 700mb CD.

Now, here is where all the hell began.

--------------------------------------

The iBook is unable to read the CD.
It sometimes does... it sometimes not (mostly time it doesn't).

Now, when the system is booting and I set the system to let me chose what drive I want to boot, the Ubuntu CD do not show up.

Actually the iBook can read any CD, but not the Ubuntu CD.
I have already the Desktop-LiveCD but it dont work either.

So, the PPC version and the normal-desktop are not working.

I remember I was able to boot once the PPC (alternative) version but it showed an error Im not able to remember now and Im not able to repeat the error since it dont want to read the CD again.

This is kinda confusing and Im not sure if it is the hardware or there is something Im doing wrong.

- David

--------------------------------------

[B]iBook specs:
[/B]PPC / G3 500mhz
640mb SDRAM
8mb ATI video card
10GB HD / SATA
Actual OS : 10.3.9 panther
Sony CD-RW drive

---

### Post by ubonetu on 2009-04-10
Hey,

I had the same problem.  You need to (sorry) re-install os x, burn a 8.04.1 LTS live install CD and then upgrade to 8.10.  It's the only thing I could get to work.  And, you need this file:

[http://members.cox.net/koistone/libpixman-1-0_0.12.0-1_powerpc.deb](http://members.cox.net/koistone/libpixman-1-0_0.12.0-1_powerpc.deb)

do a ctl alt F2 to get to a terminal and install it, kill the x-server or log out and back in and you should be golden.  Before you do that, just do a regular pkg-update and see if it works, mine won't allow any apps to run in the x-server w/o the older version of pixman.

ubonetu

---

### Post by mkvnmtr on 2009-04-10
On my G4 Ibook I found it easier to upgrade from my 8.04 to 8.10 than boot the live disk. 
Some things to remember:
To boot the 8.04 disk you need to press the tab key at the yaboot prompt and use one of the options listed. I think it was live linux-nosplash- powerpc or something like that.
If you don't want to download 8.04 there are some threads about booting 8.10 that work.
On my Ibook it takes at least 512Mb of ram to use the live disk. It came with 256Mb so a ram upgrade was in order.

---

### Post by cyberdork33 on 2009-04-10
> **ubonetu said:**
> Hey,

I had the same problem.  You need to (sorry) re-install os x, burn a 8.04.1 LTS live install CD and then upgrade to 8.10.  It's the only thing I could get to work.  And, you need this file:

[http://members.cox.net/koistone/libpixman-1-0_0.12.0-1_powerpc.deb](http://members.cox.net/koistone/libpixman-1-0_0.12.0-1_powerpc.deb)

do a ctl alt F2 to get to a terminal and install it, kill the x-server or log out and back in and you should be golden.  Before you do that, just do a regular pkg-update and see if it works, mine won't allow any apps to run in the x-server w/o the older version of pixman.

ubonetu
why would you need to reinstall OSX?

Be sure to burn your discs VERY SLOWLY. This will increase your odds of getting a bootable disc.

---

### Post by Davirus on 2009-04-10
> **cyberdork33 said:**
> why would you need to reinstall OSX?

Be sure to burn your discs VERY SLOWLY. This will increase your odds of getting a bootable disc.

Ya, I was about to ask the same, why re-install osx?
Anyway I burned both CDs at 4x.
OSX let me burn it at 1x, but not sure if it will make any difference.

Im going to try my luck with 8.04 and see if it works.

---

### Post by cyberdork33 on 2009-04-10
> **Davirus said:**
>  OSX let me burn it at 1x, but not sure if it will make any difference.
It always has for me :)

---

### Post by ubonetu on 2009-04-10
Sorry Davarius, I made a wrong assumtion that you didn't have an os running anymore (my experience was just getting to the point of drive format before things went buggy).  Sorry, my bad.

---

### Post by Davirus on 2009-04-11
-------------

---

### Post by Davirus on 2009-04-11
Ok folks, I have a new problem facing me.
I was able to run the setup (alternative version - PPC - ubuntu 8.10 intrepid) now it cant find my CD-ROM... when I just ran it on a CD-Drive......

it pop up this window:

"In order to access your CD-ROM drive, please enter the device file that should be used. Non-Standard CD-ROM drives use non-standard device files (such as /dev/mcdx).

You may switch to the shell on the second terminal (alt+f2) to check available devies in /dev with "1s /dev, You can return to this screen by pressing alt+f1.

Device file for accessing the CD-ROM:

----------------------------------------------------
"

I dont know what to do =/

[IMG]http://www.filesavr.com/second/c4a5b2e786e1a97dbdf753e4d429bd2c.jpg[/IMG]

---

### Post by mkvnmtr on 2009-04-11
I have not done a 8.10 install but you have a common problem. There is a thread on a work around. It should be on the first or second page of this forum. It a pretty easy fix. It is just a bug with the installer that has not been fixed.

---

### Post by Davirus on 2009-04-11
> **mkvnmtr said:**
> I have not done a 8.10 install but you have a common problem. There is a thread on a work around. It should be on the first or second page of this forum. It a pretty easy fix. It is just a bug with the installer that has not been fixed.


I hope this is not the thread you are talking about.
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

if so, then I have already tried all what is told there and nothing works for me.

I have already posted my situation there, no reply yet =/
Im not in a rush actually but I would love to see how ubuntu will run on his iBook and make his life easier xD

---

### Post by mkvnmtr on 2009-04-11
Yes that is the thread and the only one I have seen on this problem. I do kind of keep up on the powerpc stuff. The instructions aare pretty simple so if it didn't work for you I would try 8.04. I have installed that one several times from the live disk and I think once from the alt disk.

---

