---
title: "Not able to boot from CD/floppy;  uninstalling ubuntu"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by smokey1234 on 2007-12-31
OK guys, I have a friends computer that currently has Ubuntu loaded on it.  Said friend wants me to remove Ubuntu and put XP pro on it.  

Yea, OK easy enough, right?  

No such luck.

For some reason I can not boot from the CD drive or the floppy.  (yes, I went into the BIOs and changed the boot order).

When linux is loaded up I am unable to even mount the CD drive or the floppy.

I even tried using a USB DVD/CD-RW external to boot (USB CDROM was an option) but no avail.  This external drive will mount in linux but doesnt get picked up on boot.

So what can I do?

---

### Post by gn2 on 2007-12-31
Does the internal CD drive work normally once the system is booted?

If it doesn't then it could be time for a new CD drive.....

---

### Post by Herman on 2007-12-31
I think the same as gn2. 
I'm guessing that probably this computer you're talking about has a few hardware problems. You should try to find out for sure. 
Run some tests and experiments to find out if the CD-ROM drive and the floppy disk drive are working okay or if it's the motherboard that needs to be replaced.

The only real way I know of to test is to try with a new or known-good CD/DVD drive and floppy disk drive, or remove the hard drive and put it in a computer that's working okay.

Whether or not a computer can boot an external USB drive doesn't really mean much. I have some new computers and some old computers and it seems to me that only some computers are able to boot an external USB, regardless of whether they are new or old. You'd probably have a better chance of booting a USB device in a relatively new computer though. 
Does it offer you the external drive as a bootable device when you press F8 or F12 during boot-up? But when you select it it's unable to boot?
Has it been able to boot from the USB drive before? Have you tried it with a bootable USB flash memory stick with an operating system in it?

If there are known good machines available, and providing you know what you are doing, it would be  quicker to take the hard drive out and  put it in a known good machine until you get the new operating system installed.
I don't know if that;s legal or not with a proprietary operating system, but probably it is illegal and if there are built-in software traps that  can detect such a thing. If so then the operating system will probably  work for one month and then automatically time out and fail without telling you why. Read the licence that comes with the operating system and decide again if you really want that operating system in any computer at all. (Even an old one?)

Regards, Herman :)

---

### Post by Paulmd on 2007-12-31
> **Herman said:**
> I think the same as gn2. 
I'm guessing that probably this computer you're talking about has a few hardware problems. You should try to find out for sure. 
Run some tests and experiments to find out if the CD-ROM drive and the floppy disk drive are working okay or if it's the motherboard that needs to be replaced.

The only real way I know of to test is to try with a new or known-good CD/DVD drive and floppy disk drive, or remove the hard drive and put it in a computer that's working okay.

Whether or not a computer can boot an external USB drive doesn't really mean much. I have some new computers and some old computers and it seems to me that only some computers are able to boot an external USB, regardless of whether they are new or old. You'd probably have a better chance of booting a USB device in a relatively new computer though. 
Does it offer you the external drive as a bootable device when you press F8 or F12 during boot-up? But when you select it it's unable to boot?
Has it been able to boot from the USB drive before? Have you tried it with a bootable USB flash memory stick with an operating system in it?

If there are known good machines available, and providing you know what you are doing, it would be  quicker to take the hard drive out and  put it in a known good machine until you get the new operating system installed.
I don't know if that;s legal or not with a proprietary operating system, but probably it is illegal and if there are built-in software traps that  can detect such a thing. If so then the operating system will probably  work for one month and then automatically time out and fail without telling you why. Read the licence that comes with the operating system and decide again if you really want that operating system in any computer at all. (Even an old one?)

Regards, Herman :)

Cloning XP is legal, PROVIDED you have licences for all copies.

There is one major gotcha.  Ideally, cloning should be done on absolutely identical machines. The less similar, the greater the chances of issues with drivers. There's also the  INACCESSIBLE_BOOT_DEVICE  blue screen you sometimes get, when the hard drive controller changes. 

The other issue is activation, curing this may mean a 5 minute call to microsoft. Tell the computer voice that your motherboard died and you are replacing it. (it asks you this in the form of yes/no questions).

---

### Post by smokey1234 on 2007-12-31
> **Herman said:**
> I think the same as gn2. 
I'm guessing that probably this computer you're talking about has a few hardware problems. You should try to find out for sure. 
Run some tests and experiments to find out if the CD-ROM drive and the floppy disk drive are working okay or if it's the motherboard that needs to be replaced.

Just called the friend I'm doing this for.  He stated that he used  the internal CD-ROM to install Ubuntu (with a brand new hard drive)....this was a year ago. 

I guess after ubuntu installed he never really had a use for the onboard CD-ROM and it was never used.  Although he stated that upon trying to play a music CD from it a 'could not mount error' would come up (same thing its telling me).  

> 
The only real way I know of to test is to try with a new or known-good CD/DVD drive and floppy disk drive, or remove the hard drive and put it in a computer that's working okay.

I have an extra internal CD-Rom that I'm about the to try out.  Will Ubuntu recognize the switch or is there some sort of manual step I should take?

>  
Does it offer you the external drive as a bootable device when you press F8 or F12 during boot-up? But when you select it it's unable to boot?

Yes, the BIOS offers several USB options for boot up.  None of them seem to work or for some reason GRUB still loads up first. 

> 
Has it been able to boot from the USB drive before? Have you tried it with a bootable USB flash memory stick with an operating system in it?

Never tried a USB boot before this.  That may be a last resort thing for me to try, should I not be able to get CD ROM to boot.

> If there are known good machines available, and providing you know what you are doing, it would be  quicker to take the hard drive out and  put it in a known good machine until you get the new operating system installed.

Actually, that's a great idea :)  If I can't get any other options to work, I can switch out the hard drive tomarrow at my shop.........

---

### Post by Herman on 2007-12-31
:)  Okay, Switching the CD-ROM drive would be my first choice of things to do, that would be the easiest and the quickest, and there's a good chance that should work.
> I have an extra internal CD-Rom that I'm about the to try out. Will Ubuntu recognize the switch or is there some sort of manual step I should take? Everything should just work, and you won't have to do anything. Just watch the PATA jumper settings though. Make sure your have those jumpers set appropriately according to the sticker on top of the drive and different from the way the other PATA drives are plugged in and jumpered.
> Yes, the BIOS offers several USB options for boot up.  None of them seem to work or for some reason GRUB still loads up first.  Some computers can boot a USB and others can't, it seems. It's easier if you have a USB that you know normally boots or a computer that you know normally boots a USB. If both things are uncertain it makes things difficult. You would only be relying on luck.
> Actually, that's a great idea :)  If I can't get any other options to work, I can switch out the hard drive tomarrow at my shop.........
 Yes, and Paulmd says it should be okay, that looks convincing enough for me.

About CD-ROM drives, I have had problems with them having a dirty optical lense and the CD/DVD lense cleaning CD didn't seem to make any difference and not even compressed air seemed to do any good from the outside either.
I got one working again by dismantling it and cleaning it out with compressed air and a vacuum cleaner, then I swabbed the optical lens with a cotton bud (Qtip), dipped in methylated spirits, (denatured alcohol). 
That saved me around $100 for a new CD/DVD drive. That drive has been working well ever since. It doesn't seem to take much to upset an optical drive,  so if your lucky, and that's all that's wrong, you might be able to fix it easily too. (Without having to spend any money).
Regards, Herman :)

---

### Post by gn2 on 2007-12-31
Price of CD drives nowadays, a new one would cost roughly the same or less than a cleaning kit!

Happy New Year to all

---

### Post by Herman on 2007-12-31
> Price of CD drives nowadays, a new one would cost roughly the same or less than a cleaning kit! Yes, that's right, and if we counted the time we spend it's probably  more sensible for most  people to just go and buy a new one (upgrade). :lolflag:
The problem for me is, I'm a bit isolated, I live in a small town and although we do have an electrical & computer shop, it doesn't pay them to keep a lot of money's worth of stock. 
We don't have the population base, and prices keep going down for computer parts rather than up, so anything they don't sell pretty quickly they lose money on. 
So very often  I have to order what I need and wait a couple of weeks, and often a lot longer than that, before a needed item turns up. 

The time I had to clean an optical drive lens, I was under some pressure to get the job done quickly. 
You see, it was my wife's computer I was working on at the time, and the dirt in the CD/DVD drive caused her partition table to be corrupted. 
I wanted to get things back to normal by the time she got home. 
She has a big boomerang she keeps by her computer and she's quite skilled with it too! :lolflag:
Luckily we had all her data backed up already, so all I had to do was re-install some operating systems, which was what I was planning on doing anyway. 

She had Windows XP and two installs of Dapper Drake, I was replacing the Dapper Drake install with Feisty at the time.
By the time she got home I had it all done, so everything turned out fine. 
That was a while ago now, she has Windows XP and two installations of Gutsy now. (She never uses Windows XP anymore at all. Next time I'll just leave it out).

Happy New Year to you too, gn2, and everyone else! :)
Regards, Herman :)

---

