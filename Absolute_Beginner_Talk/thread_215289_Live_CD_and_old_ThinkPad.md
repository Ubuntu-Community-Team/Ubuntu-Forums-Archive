---
title: "Live CD and old ThinkPad"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by SeriousTom on 2006-07-13
I've dowloaded and burned the Ubuntu Live CD.
It runs on my everyday PC but I want to install it on a old IBM ThinkPad. 
The ThinkPad does boot from the CD drive but of ALL the Live CD's I have downloaded, only Damn Small Linux has booted. 
The only reason it booted is because after the initial failure of the iso image I noticed the had a download for older machines.
This was called syslinux. This works on the old machine and I was wondering if Ubuntu had anything similar.
I've tried Mepsis, Knoppix, Linspire, PCLinuxOS, SLAX and Damn Small Linux, the only one that worked was the DSL that said it was for older machines.
Oh, and Hi !:)

---

### Post by djsroknrol on 2006-07-13
Hi and welcome...

What kind of Thinkpad is it? I've got a T21 800Mhz 128MB ram running Dapper...not the fastest thing in the world, but it gets it done....Not much is impossible....

---

### Post by SeriousTom on 2006-07-13
It's a ThinkPad 770ED and not the screaming meanie yours is. Mine is 266 Mhz with 64 Mb of Ram.

---

### Post by SeriousTom on 2006-07-13
I've found this "What To Do When Nothing Works" bottom of page
[http://syslinux.zytor.com/sbm.php](http://syslinux.zytor.com/sbm.php) that might help me. They refer me here
[http://btmgr.webframhttp://syslinux.zytor.com/sbm.phpe.org/index.php3?body=download.html](http://btmgr.webframhttp://syslinux.zytor.com/sbm.phpe.org/index.php3?body=download.html)
but every time I click a link it stays on the same page. Do you think this would work.
Put this on a floppy and then boot from the Live CD, Am I reading this right ?
Also which one of these would I use, kinda looks like gobbly gook, glibc,static,support file,executable ?
[http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)

---

### Post by djsroknrol on 2006-07-14
I would think that Puppy or Damm small would work on that 770ED of yours...

---

### Post by crispy_420 on 2006-07-14
There is an Ubuntu Lite version. You can get it [here]("www.ubuntulite.org").

I have not tried it myself yet. It was a small download, about 328MB if I remember correctly.

Or you can try Xubuntu. It uses XFCE as it's desktop and is quicker on older hardware.

---

### Post by dmizer on 2006-07-14
there was a discussion about this a little while ago.  i think xfce would be a bit large for your machine.  i have a 500mhz machine that doesn't quite cut the mustard for xfce.  but i am admittedly a bit shy on ram.

something wrong with dsl that's making you look for something else?

don't know if it'll be slow enough, but you could try ubuntu lite (i'm a huge fan): [http://www.ubuntuforums.org/showthread.php?t=98233&highlight=howto+ubuntu+lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=howto+ubuntu+lite)

the directions above are for breezy, but they also work just fine for dapper.

---

### Post by w_r_cromwell on 2006-07-14
Hi,

I have some older machines in the same category as your old thinkpad. It won't help with your live DC problem but I use fvwm2 on those. Its different and you'll have to do some typing to get your "menu" the way you want it. But with limited speed and memory it speeds things up considerably when you want to get to work. In fact I installed Red Hat 7.3 on a thinkpad like yours with fvwm2 and it made the difference between night and day. Fvwm2 is available via synaptic and works well on my Ubuntu installs. It might be worth a try.

Bill

---

### Post by SeriousTom on 2006-07-15
Thanks for all the help and suggestions and for anyone else having trouble booting with isolinux and need to boot using syslinux instead, this worked for me :
I found this "What To Do When Nothing Works" bottom of page
[http://syslinux.zytor.com/sbm.php](http://syslinux.zytor.com/sbm.php)  They refer me here
[http://btmgr.webframhttp://syslinux....=download.html](http://btmgr.webframhttp://syslinux....=download.html)
but every time I click a link it stays on the same page.
The files can be found here though :
[http://btmgr.sourceforge.net/download.html](http://btmgr.sourceforge.net/download.html)
The file I used was sbminst.exe and put it on a floopy.
When I booted with the floppy and CD installed, first I heard the floppy being accessed and then a black screen that said something like remove the floppy and press any key to continue.
I thought it wasn't going to work but I pressed the spacebar and the CD loaded.
So I tried the other versions of Live CD's I had made, they all boot now with this floppy in the drive, most of them won't run, they start to run but have to many apps or something for 64 MB of memory.

---

