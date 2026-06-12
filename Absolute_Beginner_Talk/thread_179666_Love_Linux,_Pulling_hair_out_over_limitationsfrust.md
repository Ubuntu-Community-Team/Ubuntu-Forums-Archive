---
title: "Love Linux, Pulling hair out over limitations/frustrations..."
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Bleachedbluejeans on 2006-05-20
I am writing this from my wifes system. (I am actaully Papa-san) I have win XP up and as functional as it can be for her. I have Ubuntu installed, but could never get the GRUB issues sorted out, so am in the 'Live' environment right now trying to make things work... My wife hates all the time it takes for me to print a pagemaker document, and I have to admit it is frustrating to have to fight so hard to configure everything. (Then some things just don't cross over without the $...) LOL....Sorry, just venting. I LOVE linux, and if (when) I get her used to using it, I'm going to take my XP cd and use it for target practice!

---

### Post by S{yndrom}e on 2006-05-20
... so what do you need help with?

---

### Post by adamkane on 2006-05-20
Yeah, there are some great posts about how to persuade/cajole/threaten the spouse to accept Ubuntu.

You may have unresolvable issues with Pagemaker.

I got my Mom to use OpenOffice. She also uses Pinnacle Studio though, and there won't be an Ubuntu replacement until next year.

---

### Post by scooper on 2006-05-20
Just be careful with the XP CD.  They have a tendence to messily shatter when hit with projectiles. :)

Have you checked out Scribus?  I'm not sure what import formats they support, but I think it's the best current Linux alternative for desktop publishing.

Since Pagemaker is an expensive piece of software, have you considered VMware?  It's well worth the investment to give you perfect access under Linux to irreplaceable Windows apps.  VMware has gotten a bit more affordable, I think.

---

### Post by Papa-san on 2006-05-21
Hi... I am the OP, but now on my laptop... lol
The XP cd would be used to see if my aim is sure enough with a deer rifle to see if I can make it through the little hole in the middle from a hundred yards, so when I pull it a bit, the glorious shards wouldn't hit me!

What I need help with... lol... Way to much!

My laptop cant print to the canoni550 printer that is hooked up to my wifes machine. Ive been through the how to pages I was able to find, but my printer doesn't show up in the list, no matter how many drivers I download... Someone sent me a link to a page that looks comprehensive enough, but I am not sure how to actually go about following the instructions... (Don't know enough about command lines, and the language isn't clear enough for a nOOb like me.) The link is here: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus22.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus22.html)

My wife's system has both Win XP and Ubuntu installed. The XP boots fine, but the grub (I think) is gone. (MBR shows nothing, and boots into XP automatically) If I fix this issue, I need to have it boot XP automatically if no-one does anything to go to Ubuntu. 

Then I need to get the laptop to be able to locate, read, and write to the fat32 partitions of the XP partition of her machine, so we can work on things together, or she can use the laptop for her work. 

Also need to get ruby on rails up and running... (actually just find where it installed, so I can see if it will work to build a new website...)

That's the short list... I'll leave out the quirky stuff for now...
:rolleyes: 

(Papa-san isn't the brightest Crayon in the box...)

---

### Post by Ecthelion on 2006-05-22
To reinstall grub, i've found this the easiest way:

[http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")

Next, to make Windows boot when no-one interfere, type:
```
gedit /boot/grub/menu.lst
```

You will get something that starts with

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3


Only thing you need to do is changing the number of default entry to the number of the windows boot (you can find that lower in the document)
(0 is the number of the first entry, so just count till you find the windows entry)
Even easier is just to write instead of a number "saved"
But before you do that check if the windows line of grub says:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
**savedefault**
makeactive
chainloader	+1


If savedefault isn't there, you can add it, but be sure that there is no other enrty with savedefault before doing so.

As you see i've changed the timeout time so that the grub only shows up 3 seconds... makes booting 7 seconds faster ;):p 

Hope that this helps with at least 1 of your problems.

---

### Post by Ecthelion on 2006-05-22
Now for mounting your fat32 an for writing reading on it.

first, type
```
sudo gedit /etc/fstab
```

That will open a document where all of your partitions that are detected are written in

you will have to change the line of tha partition that is recognised as FAT32
yours should look like this i think:

> /dev/hda5 /media/hda5 vfat defaults 0 0

You change the line to this, except that you leave your own /dev/hda* and /media/hda*
> /dev/hda5 /media/hda5 vfat users,rw,uid=1000,gid=100 0 0

Once you have done this, save the document, and type in the command-line
```
sudo mount -a
```

Normally you should be able to read and write to your fat32 now.
If you can't find the disk anymore, just reboot and then he'll be back there.

---

### Post by Ecthelion on 2006-05-22
i'm afraid I can't help you with your printer problems.

And i don't know ruby so i can't help there either.

Hope you get everything working,
Ecthelion

---

### Post by Papa-san on 2006-05-22
Thank you... I'll post my results!

---

### Post by dmizer on 2006-05-22
printing to your printer from your laptop to a printer connected to xp.

first of all, you will need to make sure that file and printer sharing is enabled on your xp machine.  if it is, then you need to make sure that your printer is marked as shared.

after that, then it will likely help (but i don't believe it is necessary) to install and configure samba to be able to mount shares on the xp machine. (lots of threads around here on samba).

once you do that, you should be able to get your ubuntu laptop to see your printer, and that's half the battle.  once you can see the printer, just configure it in cups and see if you can print.  if so, then good ... if not, post back.

happy ubunting.

---

### Post by Sef on 2006-05-22
Here's some info about your printer.

[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2806]("http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2806")

Here's a driver for your canon.

[http://www.linuxquestions.org/hcl/showproduct.php?product=702&cat=myprod]("http://www.linuxquestions.org/hcl/showproduct.php?product=702&cat=myprod")

---

