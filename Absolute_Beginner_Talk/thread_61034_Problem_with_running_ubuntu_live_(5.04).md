---
title: "Problem with running ubuntu live (5.04)"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by tengesdal on 2005-08-30
This might be in the wrong forum, please feel free to move it.
I am now sitting on a Acer Aspire 1690 series laptop.
Specs:
Intel Pentiym M processor 740 (1,73 GHz, 533 MHz FSB, 2 MB L2 cache)
ATI MOBILITY RADEON X700 PCI express with 128MB VRAM
80GB HDD
Slot-loading DVD-Dual (support DVD+R Double Layer/DVD+/-RW)
512MB DDR2 (support dual channel)
802.11b/g wireless LAN

I go and edit so that my computer boots from DVD/CD, then i get acces to the part that says something like: "Press ENTER for easy setup" or "Press F1 for advanced settings" (i dont quite remember what they say but you understand.. Like the first screen.
So then i push enter, and there are 2 lines about the computer loading certain files. After that it commes to "uncompressing (something)... OK, (then something about kernel)

And there its stuck.... NOTHING happens!

Sorry for not managing to say the stuff right, but i dont have time to enter it again to see if its right. But its something like that.

Hope you guys can help me.

---

### Post by sto6ma9ch on 2005-08-30
It sounds like you've successfully booted from the DVD drive. An easy way to tell if it worked is that, after you reboot, you'll get a cool splash screen that has the Ubuntu logo and a "BOOT:" line at the bottom. If you get that far, read on.

When the Ubuntu messages stop, what do the last few lines say? That may give us some clues as to what's failing.

You may also want to try booting Ubuntu with ACPI support turned off. When you get to the Ubuntu Live CD bootup screen "BOOT:" prompt (normally you would press Enter to get it going), try typing:
```
linux acpi=off
```
After that's typed in, press Enter. You'll have to be quick about it, because after a few seconds, the CD will accept the default boot options and continue as if you just pressed the Enter key. See if you get further in the boot process than before.

Keep us posted.

---

### Post by xmastree on 2005-08-30
Ok, it's a live CD. Where did you get it?
If you downloaded and made it yourself have you checked it with md5sum?

if not, and assuming you have Windows installed, download md5sum for Windows and check it. If you don't understand how to do this ask again and I'll explain further.

---

### Post by tengesdal on 2005-08-30
the splash screen is what i referred to as the "first screen"

---

### Post by tengesdal on 2005-08-30
The live CD is ordered from shipit, and came in the post yesterday.
When i click ENTER at the splash screen, it tryes to boot and start ubuntu right? Well i see 2 lines that are loading some files..
After they are done, it says "Uncompressing (something) OK, booting kernel" (its a normal message, i get the same on my other computer (where it works)) But on this laptop thats how far i get... Dont get farther:( I also pressed F1 at the splash screen, and saw that i could type "live-expert" or something to boot in expert version, but the same problem there. Any tips?

---

### Post by xmastree on 2005-08-30
It wouldn't hurt to md5sum it anyway, to make sure that drive can read the CD

First, download md5sum for windows and put it somewhere on the path.
[**Here**](http://www.etree.org/md5com.html) is one version.
There are others but they all do the same thing.

In the root directory of your CD is a file, md5sum.txt which lists the md5sums of all the files on the disc. What you need to do is compare what's on your disc with what this file says ought to be there.

If your CDROM drive is d: then open a command prompt (dos box) and type:```
d: <enter>
md5sum -c md5sum.txt <enter>
```Then sit back and watch while it checks every file on your disc.

If it does check out, then you might be better off asking in the laptop forum.  :-?

---

### Post by tengesdal on 2005-08-30
ok, i will try this, and get back to you and report. 
Thanks for the help

---

### Post by tengesdal on 2005-08-31
when i try to use your code i get a message like this: "md5sum: md5sum.txt: No such file or directory

Ok the problem was i had the wrong directory :p but what shall i do after doing this? I have ran md5sum.. what now?

Warning: 1 of the 1109 files could not be read
Warning: 1 of the 1108 computed checksums did NOT match

---

### Post by xmastree on 2005-08-31
> Warning: 1 of the 1109 files could not be read
Warning: 1 of the 1108 computed checksums did NOT matchThat doesn'tlook too good...

You said that disc has worked on another system?
I would suggest you run the same thing on the known good one. If it passes, there's your problem. The laptop drive is having trouble reading the disc.

Although I'd expect more than a couple of errors if that were the case.

---

### Post by tengesdal on 2005-08-31
this is a diferent disc, both from the same batch that came in the mail...
the one i used yesterday, only contained ubuntu live, now i got 2 cd, both install and live.

Maby the "real" ubuntu cd would be better? (yes installing it)
But my question is then if i can choose between windows, and ubuntu upon reboot?
So that i can choose myself what i want to use.

---

### Post by xmastree on 2005-08-31
So, you have one set of two discs, live and installer. Which did you use on the other system?

As for installing it on the laptop, I'd be wary if the live one won't run, you may run into problems.

I'd suggest asking in the laptop forum.

---

### Post by tengesdal on 2005-08-31
I got like about 40 double discs in the mail, the one i used yesterday seemed to be missing the install cd, and only contained the live one. So i grabbed a new double disc case today, that contained both discs.

But do you know if i can choose between windows/linux on reboot?

---

### Post by xmastree on 2005-08-31
Yes, you can. The option will be there after you install it. You might want to look into repartitioning, and creating a shared data area for both OSs to use. Linux can read ntfs, but if you wish to write to it then it must be FAT32.

Good luck, and don't be afraid to ask. However, it's a good idea to [look here](http://www.ubuntuguide.org) first, as that will hold most of your answers.

---

### Post by tengesdal on 2005-08-31
Fine, i now see that there will not be any linux on this laptop :( neither live, or installed. 
Get the same message when installing: Uncompressing linux, OK.. loading kernel

---

### Post by xmastree on 2005-08-31
Depends how much time you have and how much hassle you are willing to put up with. If you do persevere, you'll end up learning more about it than you expected to, and that can't be a bad thing.

If you've used it on the desktop, presumably you know if you like it or not.

Ask in the laptop forum, I'm sure you'll get better answers there.

---

### Post by tengesdal on 2005-08-31
Where is the laptop forum?

---

### Post by xmastree on 2005-08-31
[http://ubuntuforums.org/forumdisplay.php?f=63](http://ubuntuforums.org/forumdisplay.php?f=63)

---

