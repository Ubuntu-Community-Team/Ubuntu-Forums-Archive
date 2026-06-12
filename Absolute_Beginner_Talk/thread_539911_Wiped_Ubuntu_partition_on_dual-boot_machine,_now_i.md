---
title: "Wiped Ubuntu partition on dual-boot machine, now it's still trying to use GRUB."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by LingLing1337 on 2007-08-31
I really need to get rid of Ubuntu, and I have used gParted to remove it. Now when I boot up the computer I get GRUB error 22 and apparently it is still trying to load the GRUB. What can I do to get into Vista? Thanks.

EDIT: I can't boot using the Vista DVD, as my computer didn't come with one.

---

### Post by ARandomKid on 2007-08-31
...the only thing I can think of is to reinstall Vista.

But then, I'm not much of a Linux expert at all. There's vey probably a much easier solution that doesn't involve wiping anything important. (I'd say 90% chance)

---

### Post by LingLing1337 on 2007-08-31
I can't do that since I don't have the Vista DVD. It would work if I reinstalled Ubuntu, I'm sure, but my parents are currently yelling at me to get it off. I really need help.

---

### Post by ARandomKid on 2007-08-31
Oh. Well. That sucks.

[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12)

Although I highly doubt this is what you're looking for. Just ran a google search for "uninstalling GRUB"

---

### Post by anewguy on 2007-08-31
I created a how-to for removing Linux, but once you have gotten to your stage, you either need a Windows disk or try something called super grub disk.  I have seen this mentioned many times for your situation, but I've never used it.  Perhaps someone can post back here with instructions for using it.  You may want to do a search in this form for it,:)

---

### Post by raul_ on 2007-08-31
Download Super Grub Disk. You could RTFM (no offense here of course :) ) but all you have to do is navigate through the menus (not very intuitive, i'll give you that), I think it's in Advanced->GRUB or just GRUB, and then "Remove GRUB".

It will restore your MBR and you'll be able to boot into Vista.

If by any chance your Vista hangs while booting just insert a Windows XP disk, press R for recovery console, give a wrong password 3 times and you're good to go

---

### Post by p_quarles on 2007-08-31
The only thing you can do (legally) at this point is to contact the manufacturer and pay them to send you a set of Vista recovery disks for your system. 

It will cost money, but not nearly as much as an off-the-shelf purchase of Windows.

This is the price you pay for not doing your research beforehand.

---

### Post by LingLing1337 on 2007-08-31
How can I burn a Super Grub Disk if I have the LiveCD (The only OS I can get to) in my drive?

---

### Post by Officer Dibble on 2007-08-31
It sounds like you were dual booting Vista and Ubuntu, is this correct?

If so, then all you need to do is fix your master boot record, and the way to do this is quite simple.

If you can boot from a floppy disk download a windows ME boot disk from [here]("http://pesona.mmu.edu.my/~panzheng/bootup/bootme.exe"), boot from it (after creating the disk, only takes a moment) and from the dos prompt type:

[COLOR="Blue"]**fdisk /mbr**[/COLOR]

After this Vista should fire up nicely.

**[COLOR="Red"]Alternatively[/COLOR]** if you have an XP CD lying around you can boot from that (I know you're using Vista) choosing the Repair option (R) which will take you to the Recovery Console.

At this point you'll be asked which windows installation you would like to log into, and at this point I'll assume you'll only have the one, so type 1.

Next you'll be asked for the Administrators password, type that in.

After this you'll be at the "DOS" Prompt, it will probably look something like this - "**C:\WINDOWS >**"

Type the following and press enter:

[COLOR="Blue"]**fixmbr**[/COLOR]

After you have pressed enter, then type **Exit** and your computer will restart.

If none of the above is an option let us know right away

---

### Post by LingLing1337 on 2007-08-31
I can't boot from a floppy, and I have no other Windows cd's "Lying around".

---

### Post by raul_ on 2007-08-31
I think you can burn cd's from your Live CD. If not, you can put Super Grub Disk in a floppy or in a pen. You'll have to follow the instructions on the page to do that

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by LingLing1337 on 2007-08-31
By removing the LiveCD? Won't that make Ubuntu crash?

---

### Post by LingLing1337 on 2007-08-31
Bump. I really need some help.

---

### Post by raul_ on 2007-08-31
It should be loaded to RAM, but I never tried, since I actually have 2 drives (silly me). If you have a new PC you can probably boot from USB, just put SGD in a pen

---

### Post by LingLing1337 on 2007-08-31
I don't have a USB drive, and pushing the eject button won't do anything for me.

---

### Post by Officer Dibble on 2007-08-31
> **LingLing1337 said:**
> I can't boot from a floppy, and I have no other Windows cd's "Lying around".

Can you write CD's? Honestly, once you can either use "fdisk /mbr" or "fixmbr" then you're problems are over.

If you can write CD's then download a disc called Hirens Boot CD. It's only about 70MB, boot from that.

Does your neighbour have a XP CD?

Why can't you boot from a floppy?

---

### Post by raul_ on 2007-08-31
Well, if you don't have eggs, you can't make an omolette. I guess you'll have to burn your super grub disk somewhere else, or borrow a windows xp or vista disk from a friend. 

Sorry

---

### Post by LingLing1337 on 2007-08-31
I have no floppy drive. If I just put Hiren's onto a general USB drive with other files like schoolwork, etc then I could boot from it, right? Or would I have to take other steps. I have no neighbors with any technical knowledge.

---

### Post by raul_ on 2007-08-31
> 1 - Installation of SGD in a USB device from a Linux with grub installed


Mount your usb hd 
untar file in your usb hd (or copy contents of it to usb hd)
umount your usb hd 
open grub as root 
device (hd3) /dev/ubb # my usb device in linux is called /dev/ubb 
root (hd3,0) 
setup (hd3) 
quit 
reboot 


from "USB_README" included in the USB version of super grub disk

your neighbors don't ned technical knowledge, they just need to have a CD lying around :P

---

### Post by LingLing1337 on 2007-08-31
"Can you write CD's? Honestly, once you can either use "fdisk /mbr" or "fixmbr" then you're problems are over.

If you can write CD's then download a disc called Hirens Boot CD. It's only about 70MB, boot from that.

Does your neighbour have a XP CD?

Why can't you boot from a floppy?
__________________"

I can't write CD's, I only have 1 drive, and the LiveCD is in it.

---

### Post by Officer Dibble on 2007-08-31
> **LingLing1337 said:**
> I have no floppy drive. If I just put Hiren's onto a general USB drive with other files like schoolwork, etc then I could boot from it, right? Or would I have to take other steps. I have no neighbors with any technical knowledge.

They don't need any technical knowledge at all... they just need to possess an XP CD you can borrow for all of ten minutes. :)

---

