---
title: "Can't even boot the installation CD!! HELP!"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by kchukchukchu on 2006-04-12
Hello, everyone,

I am desperately trying to install the server version of Ubuntu on my 466MHz 128M RAM machine to do a mathematica/java project that is very important to me.

I am new to any OS installation and I haven't even been able to boot the installation CD:

I think I am supposed to just put the CD in the computer and start it so that it would boot from it.  But I checked the BIOS menu (finally figured out where that is after reading many text/readme files in the machine) and I think my computer doesn't support CD-boot.

So I followed this link, [https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386), and went and downloaded on a floppy the SmartBootManager by using RawriteNT 
(This program seems to by default copy .img file, but the one that I am need has a .dsk extension, so I dont' know if it worked), but the old Windows 98 just keeps booting up as if the floppy or the CD wasn't there.

What do I need to do?  Should I just try a few floppies? What did I do wrong?

 And I don't need to uninstall the old OS (Windows 98) before I do everything right?

Thank you for your help in advance.  I am totally new and would greatly appreciate it.

kay

---

### Post by therunnyman on 2006-04-12
Whatcha got in  your BIOS for boot options?  To get to your BIOS, you usually press F8, ESC, or F12 during the inital boot cycle, before the OS starts loading.

Gallo, we will sell no wine before its time,

therunnyman

---

### Post by nemequ on 2006-04-12
What happens if you boot with a blank disk in the floppy drive? If you don't get something like 'Non system disk error, replace and strike any key' (probably not verbatim--that was from memory), it would seem like your computer doesn't attempt to boot from the floppy either. If that's the case, get into the BIOS and convince it to.

---

### Post by therunnyman on 2006-04-12
[QUOTE=nemequ]What happens if you boot with a blank disk in the floppy drive? If you don't get something like 'Non system disk error, replace and strike any key' (probably not verbatim--that was from memory), it would seem like your computer doesn't attempt to boot from the floppy either. If that's the case, get into the BIOS and convince it to.[/QUOTE]


We're racing nemequ!  Last one to the terminal that nobody can find is the rotten egg!

therunnyman

---

### Post by kchukchukchu on 2006-04-12
hello, the runnyman,
thanks for your quick reply!

My boot menu: it says floppy check [enabled], and under it, indented, is a list of drives starting from 1. CD 2. Harddisk, and then (unindented) it says Harddrive (and explained that the computer tries to find the first OS in this list).

So, that's how I gathered that it can check a floppy but not boot from a CD.
 

Kay

---

### Post by kchukchukchu on 2006-04-12
hello, nemequ,
Thanks for your quick reply!!

I have not tried to insert a blank floppy (can I can't do that right now because I'm not at home)  so I dont' know.

Do you (or any of you other people too) know how to copy the .dsk smartbbootmanager disk image to a blank disk? I think I may have done that part not properly because the software (rawwrite) seems to want to copy .img file rather than a .dsk file.

THANKS in advance again.

Kay

---

### Post by therunnyman on 2006-04-12
Good news!  You can boot from disc, if you want (I'm of no help when it comes to floppies).

Is that option checked in your BIOS, the CD one I mean?  If so, good.  If not, check it.

When burning the image furnished by Ubuntu, make sure you burn it as an image, not as a "data disc" or whatever the heck the wizards are calling it these days.  That's vital.  Someone suggested, a magnificent suggestion, using CD-RW so you don't blow any media.  Just erase it if something's not working, and try again.

therunnyman

---

### Post by kchukchukchu on 2006-04-12
[QUOTE=therunnyman]Good news!  You can boot from disc, if you want (I'm of no help when it comes to floppies).

Is that option checked in your BIOS, the CD one I mean?  If so, good.  If not, check it.

When burning the image furnished by Ubuntu, make sure you burn it as an image, not as a "data disc" or whatever the heck the wizards are calling it these days.  That's vital.  Someone suggested, a magnificent suggestion, using CD-RW so you don't blow any media.  Just erase it if something's not working, and try again.

therunnyman[/QUOTE]
Hello, the runnyman,

Thanks again!

Thanks for mentioning that I need to write the Ubuntu CD as an image, I did burn it as a data disk!!  but I don't know what CD-RW is (I assume it's a software?) and I am on a Mac laptop right now, so I will check how to burn it as an image. Can I use CD-RW on this Mac? maybe the CD was actually the problem.

BUT:  I don't think there is any thing that I can check for the CD-rom (on the list) the only thing I can do was to reorder the items on the list (eg move harddisk above CD)  I dont' know if that means it would automatically boot from CD first, although it did look like that at first.

So, I'll try to rewrite the CD as an image and see what it goes. THANK YOU SO MUCH.

Kay

---

### Post by aktiwers on 2006-04-12
Writing as image is the only way you are going to get it boot :)

If you have windows, and use Nero, its very easy to write an image. Simply pick it from the wizard.

Good luck :)

---

### Post by kchukchukchu on 2006-04-12
Thanks! and thanks for the good luck!  :)

I am going to try, but I am on a Mac,  so I'll see! I am redownloading the iso file right now.

K

---

### Post by therunnyman on 2006-04-12
Okay cool, your BIOS's boot order looks 5x5 - do make sure CD is at the top.

CD-RW is a type of media that didn't get much attention in the optical storage world.  It functions something like a floppy: you can erase, rewrite, append whatever info you like to it.  The only thing it won't do is play in older Audio CD players, for lack of what's known as "reflectivity."  The audio market was where it was at, I'm sure you noticed that, so, since CD-RW was virtually useless where audio was concerned, no paid no nevermind to it.

So, yeah, CD-RW is CD-R media you can erase and start over again with.  Like a cassette tape, as opposed to an LP.

therunnyman

---

### Post by kchukchukchu on 2006-04-12
Oh, cool, so this is not "urgent" anymore, but just out of curiosity:  so is this Cd-R media does it look like a CD as well? (This sounds sort of funny, but I don't really get how it is different from a CD.  Is it just the way it is set up, but still uses the same "disk'?)

I am really hoping that this CD image burn will work.  Is it usually a risky thing? should I try burning a few CD's just in case?

Thank you so much, I actually have hope now!:)

---

### Post by therunnyman on 2006-04-12
No risk involved, none at all, so long as you burn the image as an image.  Here's another thread with all the CD writing goody-two-shoe knowledge I've got in it:

[http://www.ubuntuforums.org/showthread.php?t=158655](http://www.ubuntuforums.org/showthread.php?t=158655)

CD-RW is identical to CD-R; it's a disc.  The only visible difference is the dye on the write side: where CD-R is, these days, either blue (that's metal azo dye, Verbatim) or greenish (advaced phthalocyanine, Mitsui), CD-RW is gray (I dunno what that is).

I battled the NYT over the spelling of "Compact Disc" one day.  Their stylebook says "Compact Disk," but, if you look at a drive or anything else CD, it's spelled "Disc."  Sony and Philips, inventors of the technology, decided that a long time ago.  They changed their stylebook.  Baby steps...

therunnyman

---

### Post by kchukchukchu on 2006-04-12
OK, I get it, a CD-RW is the a Compact Disc/k (:P)  that is rewritable...  but does that mean we normally use CD-R? how come mine doesn't have that dye ?..hmmm.   i just read the other thread that you just referred me to here, thanks.

So, I dont' need to do anything to the windows before I install this right?   I just put the CD in, and restart the computer, right?

Thanks tonnes again:)

---

### Post by kchukchukchu on 2006-04-12
OK, I just looked at my CD again and I think i can see a light green rather than just silver.  I think that's what you meant. ok, good.

[QUOTE=kchukchukchu]OK, I get it, a CD-RW is the a Compact Disc/k (:P)  that is rewritable...  but does that mean we normally use CD-R? how come mine doesn't have that dye ?..hmmm.   i just read the other thread that you just referred me to here, thanks.

So, I dont' need to do anything to the windows before I install this right?   I just put the CD in, and restart the computer, right?

Thanks tonnes again:)[/QUOTE]

---

### Post by therunnyman on 2006-04-12
You up and running?  Hope so.  Gotta log out.  Cocktail hour, then work.  Then cocktail hour again.

Rock over London, Rock on Chicago,

therunnyman

---

### Post by kchukchukchu on 2006-04-12
hey, thanks for checking on me.

So, I am using a Mac to burn the installation CD, but I am not given a choice to burn a data disc or image..  I don't know how to get there.  

But the file does show up as a disk icon with no .iso extension.  Does that mean I should just burn that then?

Thanks in advance again,
Kay.

---

### Post by 3rdalbum on 2006-04-13
Do you have Roxio Toast on the Mac? I'm not sure if you can burn a disc image correctly onto a CD using the inbuilt Mac OS burning software.

Just occurred to me: Try looking on the Mac for a program called Disk Copy. It might have an option for burning a disk image to CD.

---

### Post by kchukchukchu on 2006-04-13
Hello 3rdalbum, 

Thanks for your reply and your suggestion!   I successfully burned a CD that would load using the Disk Utility, but I don't know what's up with it because when it was loading the CD after either the language selection (before the paritioning) or after when it was actually installing the system (after partitioning) I tried many times to install and somehow the error of looading happens at these different places.

I am going to post a new post about this, so I'll look for your reply there:) should you have time to help me more.  thanks a lot!

K

---

