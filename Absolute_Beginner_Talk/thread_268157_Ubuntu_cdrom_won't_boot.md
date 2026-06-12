---
title: "Ubuntu cdrom won't boot"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Roger at CCCC on 2006-09-29
I'm an absolute beginner and just received my ubuntu cdrom in the mail.  My computer reads the cdrom ok and the initial splash screen comes up.  However, when I reboot, ubuntu does NOT boot.  I went to the computer boot options and changed the order so that the cdrom is first but that didn't help.  I am using a Dell computer several years old with Windows ME. If more information is needed, please let me know what it is.   

If I should ask this question elsewhere, or it is already answered (I expect that it IS answered somewhere but I don't know where), please direct me to the right spot.  

Thanks !!!!

---

### Post by bulldog on 2006-09-29
Well if you want Ubuntu to run you have to start it by booting from the cd.

What are the spec's of your computer?

If you don't have to much RAM it could be a good thing to use the alternate cd,which uses less resources,so the install will be smoother.

---

### Post by slibuntu on 2006-09-29
EDIT, didnt read your problem right, sorry!

---

### Post by Roger at CCCC on 2006-10-07
Well, nobody replied, so I guess I will give up.  I tried to get Linux running a year or two ago and didn't make a lot of progress.  I had hoped that Ubuntu was more user friendly but I guess not.  I realize that I could probably figure it out if I had time and energy to do so.  But that's the problem - if Ubuntu takes a lot of effort to run, then it's not worth the effort to me at this point.  If anybody DOES have any suggestions about how to get Ubuntu to boot from the CDROM off my plain vanilla Dell computer bought in the year 2000, please let me know.  Thanks !!

---

### Post by Bloch on 2006-10-07
> Well, nobody replied, so I guess I will give up.

Don't be such a quitter!!

Firstly, reading the data on your CD and booting from that CD are two completely different operations. Many computers and CD drives that have no problems doing the first cannot do the second. When you computer screen shows 

. . . . booting from CD-rom
. . . boot failed
(or whatever) then this is a problem with your system. Figuring out how to boot from a CD-rom is a matter of figuring out your computer's BIOS, and not ubuntu.

So now tell us, do you get a message like the above or any indication that a boot process began from the CD?

> My computer reads the cdrom ok and the initial splash screen comes up. 
Do you mean when you look at the disk in MS Windows? OK so the CD looks OK, but that does not mean your system can boot from it. Do you have another bootable CD to test your system's ability to boot from a CD?

---

### Post by CatKiller on 2006-10-07
> **Roger at CCCC said:**
> I'm an absolute beginner and just received my ubuntu cdrom in the mail.  My computer reads the cdrom ok and the initial splash screen comes up.  However, when I reboot, ubuntu does NOT boot.  I went to the computer boot options and changed the order so that the cdrom is first but that didn't help.  I am using a Dell computer several years old with Windows ME. If more information is needed, please let me know what it is.   

If I should ask this question elsewhere, or it is already answered (I expect that it IS answered somewhere but I don't know where), please direct me to the right spot.  

Thanks !!!!

Do you mean that the Ubuntu splash screen comes up, or that of your computer manufacturer? What are the contents of the cd? If it's one file that ends .iso, then you burned it incorrectly. You need to burn it as an image. [This page on the Wiki]("https://help.ubuntu.com/community/BurningIsoHowto") might fill you in.

If the Ubuntu disc is booting, but doesn't get very far, then the problem will be something else. Post back with more information, and someone will be able to help further.

---

### Post by jem7v on 2006-10-08
I've had a similar situation. Ubuntu runs fine on MY computer, but when I tried to install it on my sister's old beast, well...

Simply, it won't boot from the Ubuntu Live CD OR the Xubuntu Alternate CD. I Know that it can boot from a CD because I've done it before with the "System Restore" CD that originally came with the computer, but it won't recognise the Ubuntu discs as valid boot discs. (Also, I've checked the BIOS, and it IS set to boot from the CD-ROM. Do you think the issue might be that although it can read the CD-Rs it can't boot from them, because it isn't a cheerful new CD drive?)

Surely there must be some way to restart into DOS and use something like, oh, say, loadlin.exe to boot up ye olde Linux kernel and proceed from there, but... well... I don't know. Maybe that's not really what loadlin is for, and maybe that has nothing to do with installing it.

It would be So Swell if you could install off your hard drive in Win98, but the only instructions I've found for installing Ubuntu with the CD copied to your hard drive were for NT/2000/XP. Does anybody know how to do this?

---

### Post by handy on 2006-10-08
Whenever I strike this problem I cable up another CD-ROM drive & use it for as long as it takes.

It is usually old drives that give the problem.  More modern ones aren't quite as finicky thankfully...

---

### Post by MiXor on 2006-10-08
Hey Roger,
the way you wrote your question is a little ambiguous. Do you mean that you see the splash screen when you run the live CD and that after things then stop working? (i.e. that you cannot install, that everything looks dead slow, clock stops running...) If it is the case I suggest that you run the CD in safe graphics mode. 
Hope this is relevant to your problem.

Aline

P.S. Don't quit, Ubuntu is a very good OS, there is also a nice community to help you. I had several problems and all of them got solved thanks to the community and how to's.

---

### Post by jem7v on 2006-10-08
I assume that he means the splashscreen that comes up in Windows when you pop  the LiveCD in... the one that says to reboot and boot from the CD to try Ubuntu without changing system settings, etc, etc.

---

### Post by jem7v on 2006-10-08
Okedoke. I went ahead and tried again with my less old CD burner in that computer (compared to its flaky old 52x good-for-naught) and it worked immediately, even though the rest of the computer is an aging AMD-K6 450mhz 64MB RAM clunker. The only thing I had to set up manually was the ethernet card (ie, I had to click the Enable button under Networking because the cable wasn't plugged into the computer when I installed Xubuntu and it couldn't find a network connection, so it didn't turn it on).

But it runs fine now.

---

### Post by bulldog on 2006-10-08
Don't bother,he's gone already.

---

### Post by Roger at CCCC on 2006-11-01
Thanks to all those who replied.  I didn't check for several weeks because I had given up, like I said.  Then today, I tried once more and "bingo" I found the problem, which was of course absurdly simple.  My PC has TWO optical drives - a CDROM and a DVD-ROM drive.  I had always assumed that the CDROM drive was the boot drive and had never tried the DVD-ROM drive.  The CDROM drive never worked so I had assumed some obscure problem that I couldn't figure out.  Well, today, I tried the DVD-ROM drive and my old PC DID boot from the DVD-ROM drive.  So that was my problem.  Thanks, again, for those who responded, and sorry that I did not try this sooner, but then when you don't know what's wrong, you don't know what to try.  
Now after the boot DID work, my only comment is that UBUNTU seems to take forever to come up.  In contrast DSL-Damn Small Linux comes up in a a minute or two.  So I may experiment with DSL for the time being.  Thanks again.

---

