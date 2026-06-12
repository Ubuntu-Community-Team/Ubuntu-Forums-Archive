---
title: "install fails with both 6.06 and 6.10"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Mulenga on 2007-02-22
Hi,

I've been trying to install Ubuntu on my laptop for some months now, and I'm getting quit desperate
I've tried several sugested solutions from different forums but I'm still where I started

the problem using the live-cd 6.06 and 6.10
cd starts, I choose start or install Ubuntu
it seems to start, bun then I get
/bin/sh: can't acces tty; job control turned off
(initramfs)
ALT+F1 gives:
cp: unable to open '/root/var/log/': No such file or directory
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
and the only thing still  working at that point is the reset-button

so I tried the alternate 6.10 cd
I choose Install in text mode
Installation starts, I choose language and country, keyboard
Everything seems to go fine untill this window pops up

'Detect and mount CD-ROM
No common CD-ROM drive was detected.
You may need to load additional CD-ROM drivers from a driver floppy.
If you have such a floppy available now, put it in the drive, and continue. Otherwise, you will be given the option to manually select CD-ROM modules.
Load CD-ROM drivers from a driver floppy?'

Problem here is, it's a pre-installed laptop (Medion MD97600) and I have no floppy with drivers, so I choose manually select.
Next window:

No common CD-ROM drive was detected.
Your CD-ROM drive may be an old Mitsumi or another non-IDE , non-SCSI CD-ROM drive.  In that case you should choose which module and device are needed, look for some documentation or try a network installation instead of a CD-ROM installation.
Manually select a CD-ROM module and device?

Windows says it is an IDE-device, the only information that I can find is that it is this (HL-DT-ST DVDRAM GMA-4082N) model, and I have absolutly no clue on how to do a network installation, so i click Yes

The modules I can choose from: none :) , aztcd, cdrom, cdu31a, cm206, gscd, isp16, mcdx, optcd, sbpcd, sjcd, sonycd535

I have no idea on what to choose, but no matter which I pick, the next window is

In order to acces your CD-ROM drive, please enter the device file that should be used. Non-standard CD-ROM drives use non-standard device files (such as /dev/mcdx).
You may switch to the shell on the second terminal (ALT+F2) to check the available devices in /dev with "ls /dev". You can return to this screen by pressing ALT+F1
Device file for accessing the CD-ROM
_ _ _ _ _ _ _ _ _

And here I again have no clue on what to type
so I'm stuck here

If you have a clue please let me know, if you need extra information, please tell me where I can most likely find it and I'll go search it :)

---

### Post by go2dell on 2007-02-23
First off, welcome to Ubuntu!  Glad you're giving it a try.

Now for your problem:  it appears that Suse 10.1 also has [problems]("http://forums.suselinuxsupport.de/index.php?showtopic=43745&st=60#") on your laptop.  There's also mention in a thread on ubuntuusers.de ([in German]("http://forum.ubuntuusers.de/post/536443/")) ([poorly translated to English]("http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/536443/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3DMedion%2BMD97600%2Bubuntu%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3Df6R%26sa%3DG")) that Knoppix works, and the current testing version of Ubuntu, named Feisty Fawn, does install.

Looks like you have two options if you want to run Ubuntu on this machine:
[LIST=1]
[*] download and install the current Feisty Fawn testing release ([Herd 4]("http://www.ubuntu.com/testing/herd4") as I type this); or
[*] wait until Feisty Fawn becomes Ubuntu 7.04 upon its release in April and install it then.
[/LIST]

If you do decide to try Feisty and it doesn't work, then you can help out other users -- as well as yourself -- by [filing a bug report]("https://help.ubuntu.com/community/ReportingBugs") so the problem can possibly be fixed before release.

In the meantime, you can download [Knoppix]("http://www.knopper.net/knoppix/index-en.html"), which is also based on [Debian]("http://www.debian.org"), and give it a try.  I'm sorry to have to make you do work just to get Ubuntu to run, but you'll find it was all worth it once you get it running. :-D

---

### Post by Mulenga on 2007-02-23
Hi, thanks for your answer!

I noticed that there were posts in German about this, but my German is very basic, so thank you very much for resuming them for me :) 
I'm downloading Feisty now
I'll post results here

---

### Post by Mulenga on 2007-02-23
Wow! It works! :) now running ubuntu from cd
thank you verry much!

---

### Post by go2dell on 2007-02-23
Good to know.  Just remember that Feisty is still in testing, so things could (and probably will) break between now and April.  Just be patient; the fixes don't usually take long.

You won't necessarily need to download a new Herd CD every time one is released, unless you just want to help out with testing the install process.  Just remember to keep your system updated and enjoy the Ubuntu goodness.

---

### Post by bingoUV on 2007-02-24
Mulenga, did it work on Fiesty , or the same Ubuntu 6.10? I am also facing the same problem (Asus P5B-VM, Intel 965G chipset). In my case, Ubuntu 6.10 runs fine from CD, but when I try to install it and then boot from it, I face identical errors to yours. KNoppix, Fedora Core 6, also work fine. 
Have you filed the bug? I could not find it so asking.

thanks
Bingo

---

