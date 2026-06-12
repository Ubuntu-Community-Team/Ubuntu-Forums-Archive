---
title: "GRUB boot problems"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Nightmist on 2007-04-20
Hello,

I installed Ubuntu on a fairly slow system (Pentium 3 something, 400 MB RAM, 80 GB HD or so) with Windows 98 already installed. Everything seemed to go fine. 

hda1 FAT32 (win) -  hda2 ext3 -  hda3 swap

It has one physical hard drive, so this should be no problem. Then it was time to restart.

GRUB Error 17.

It means GRUB doesn't recognise the file system or something like that. But where, exactly, can GRUB be looking? Shouldn't it recognise both FAT and ext3 (and swap) ? How can it miss the mark with just one drive?

Now, if I have to get my hands dirty... how do I use the Live CD to look in the GRUB menu and try different things? Can it, for some reason, be pointing at the CD-ROM? I've installed Ubuntu on computers with more complicated systems, like multiple HDs with a lot of different partitions, and I never had problems with GRUB.

Thanks if anyone can help!

---

### Post by Nightmist on 2007-04-20
Oh, and I tried with a Xubuntu CD as well, with the same result. Since the Ubuntu disc has been used to install on different computers that now have a working installation, the disc itself should be working, if that helps any.

---

### Post by Nightmist on 2007-04-20
Wow... this forum is really active. My thread is gone from the front page as soon as I post it. I hope it's okay if I bump it up, 'cause I really need some help...

---

### Post by Lightarrow on 2007-04-20
Hello, had the same problem,

just highlight the ubuntu line in grub you want to modify, press E , then change the line root (hd0,0) to the right one .. for me it was root (hd1,0), then boot it. Hope it hepls ..

after that go modify the config file for grub in ubuntu for your windows partition and the ubuntu one.. hope this helps a bit. I know im not that clear but im new to explaining all this

Jp

---

### Post by louieb on 2007-04-20
Gentoo's great GRUB error page on error 17.
[http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5](http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5)

---

### Post by antoz on 2007-04-20
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Nightmist on 2007-04-21
Thanks for the replies. I can't test right now as I don't have the PC at home, so I will have to say if it worked at a later time. But I was wondering... do I need a password for sudo while using the Live CD?

---

### Post by Nightmist on 2007-04-22
I've done some testing to fix the Error 17. First I tried the following...

sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)

...and (hd0,1) is the only option that worked. Everything was successful, and then I rebooted. But I still got Error 17.

The computer has got only one HD, with 3 partitions (hda1 windows, hda2 linux, hda3 swap), and menu.lst seems to be properly set up, as well as the setup of grub (see above). So how come Grub can't find itself when I only have one HD?

Booting a Windows CD and running "fdisk /mbr" reset the mbr so I can get into windows when I need to use the computer, but Grub is stuck with Error 17 when I install it again. Any tip to get Grub to work would be appreciated.

---

### Post by vacation on 2007-07-25
sudo grub
find /boot/grub/stage1

i get an 

"error 15:File not found"

what to do?

1 80GB PATA HDD with only Xubuntu. using a live cd.

---

### Post by MQMike on 2007-07-25
Nightmist,

Looks like you’ve done it right, at the grub>, you did the root – setup – quit  (do you need the quit?).

You didn’t say exactly what happens when you turn on the PC.  After the POST, up comes . . . what?  Do you get the GRUB menu, make a selection, and then get Error 17, or what?

Wild one:  In /boot/grub/menu.lst, your boot entry for Windows 98:

title     Windows 98
rootnoverify (hd0, 0)     # or did you use root?
makeactive          # this *may* be optional or not?
chainloader +1

Maybe try the rootnoverify vs just root?
Or, if you have rootnoverify already, try it with just root.

Wild shot:
You are * positive * that your Ubuntu actually was installed to (hd0, 1) (=hda2), right?  I've seen crazier things happen (by accident) after getting through the steps of the Ubuntu installer process.

I’m racking my brain here, too.  You DID re-install GRUB correctly as far as I can tell.  I’ll keep thinking on it; maybe you can give more feedback on what I suggested so far.

---

