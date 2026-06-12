---
title: "First time installing Ubuntu [Resolved]"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Blankstare on 2007-05-30
Hi, I should admit from the start that I am virtually computer illiterate so please don't shout. Here is my little problem. 

I downloaded the Ubuntu file and burned it onto a disk. I then went through all the set up stages and I thought I was doing fine until I took the cd out of the tray and restarted the computer. It got to the bit where the orange bar starts moving across the screen and then it just froze. The orange bar had moved about a millimeter and could only be cajoled into moving further by putting  the cd back in the tray. 

As soon as the orange bar started moving again I could take the cd out and everything loaded okay.  Now, I suppose that I could just stick the cd in the tray every time I load Ubuntu but I'd rather sort it.

Any help appreciated.

---

### Post by meborc on 2007-05-30
try booting into the recovery mode (the 2. line in the grub menu)... now you are able to see the output of an error or the line where the boot stops... report back here and maybe it is something simple we can help you fix

---

### Post by aysiu on 2007-05-30
I have a suggestion that isn't difficult but may appear intimidating at first. It may not solve the problem, but even if it doesn't, it'll help diagnose the problem better. As I said before, it looks intimidating at first, but if you follow the steps one by one, it isn't difficult.

Reboot into recovery mode (see attached screenshot for an example).

This will boot you in as system administrator (also known as root) at a command prompt that looks like MS-DOS a little bit.

You're going to back up a file called /boot/grub/menu.lst by typing this command: ```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``` Then, you're going to edit the file you just backed up: ```
nano /boot/grub/menu.lst
``` Scroll down a few pages (the Page Down key will work fine for this. You can also use the Down arrow) past all the # sign lines until you get to something that looks like this: ```
## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
**kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=79c25616-bc10-40f8-8932-92af404a76c2 ro quiet splash**
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` Remove the word *splash* from that kernel line. Then save the file (Control-X, Y, Enter). And type ```
reboot
``` Instead of seeing an orange bar, you should see a bunch of text that tells you what's going on during boot-up. If the boot-up freezes again, make a note of what text displays on the screen during the freeze-up and then post that back here.

If the situation is worse after editing the file, you can restore the original file by booting into recovery mode and typing ```
cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
reboot
```

---

### Post by Cypher on 2007-05-30
That's an interesting issue and I promise to speak softly. :)

So let's start with the basics, I'm going to assume that you got the latest version of Ubuntu, i.e., Feisty Fawn and the Desktop version. That being the case, you got the LiveCD version, which means you should have gotten the full GNOME Desktop the first time you had inserted the CD into the drive.

Did you then click on the "Install Ubuntu" icon on the desktop to actually install Ubuntu to the HD? If all that went well, there should be no depedence on the CD to make things boot.

Is it possible that you putting your CD and the booting progress moving along was sheer co-incidence? Have you let the computer bootup in it's own time and seen if it ever completes?

The other thing you could do is at the initial GRUB Menu, choose to the [E]dit the first option and remove the  words "quiet splash" from the options and boot up. This will now give you a text version showing all that is happening behind the scenes. Here you can clearly see what is causing your computer to stall/not-boot..

---

### Post by Blankstare on 2007-05-30
Aysiu:

I have tried doing what you said and I got the following after rebooting:
[  48.331512] ata 2.00:failed to set xfermode
[  83.604760] ata 2.00:failed to set sfermode

and then a third
[  118.8780 etc and then eventually it started to load.  I don't know if this means anything to you but I thought I'd let you know.

---

### Post by aysiu on 2007-05-30
Apparently, [there is a fix for that](http://ubuntuforums.org/showpost.php?p=2525651&postcount=27)

---

### Post by Blankstare on 2007-05-30
Thanks for the help guys. It seems it was a problem with my cdrw. I don't profess to understand it but I'm very grateful that it is fixed. Aysui, you are a top man. Cheers.

---

### Post by aysiu on 2007-05-30
Glad you got it sorted.

---

