---
title: "True Absolute Beginner"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by ajsadler on 2005-06-02
I finally decided to give an open soruce OS a try after hearing that they are getting easier to use and finally getting fed up of W*nd*ws. I've tried to make my explanation and problem as simple to read as possible.

I've downloaded Ubuntu504.iso
Written it to CD via my CD-RW drive
Restarted my computer
Accessed BIOS and set Primary Boot to CD-ROM
Inserted my newly Burned disc into my DVD-ROM drive and didnt boot Ubuntu
Restarted again and inserted the disc into my CD-RW drive and didnt boot
Unpacked Ubuntu504.iso into the individual files
Written the individual files to CD via my CD-RW drive
Restarted my computer and checked Primary Boot
Inserted my second disc into my DVD-ROM drive and didnt boot
Restarted again and inserted it into my CD-RW drive and didnt boot

How might I get it to boot Ubuntu from this LiveCD?

There's no option in my BIOS to boot from CD-RW or DVD-ROM.


-AJ

---

### Post by felipe on 2005-06-02
1) you have to burn the iso img "as is", without unpacking, else it won't boot (unless you give specific non-trivial options). there usually is a command to explicitly doing this: "Burn ISO Image" or similar

2) re-check you BIOS settings, there should be some options in the Boot tab/section of its configuration. It's usually something like "change order of boot device". i generally put them in this order: floppy, cdrom, hd

have fun

---

### Post by az on 2005-06-02
Please state exactly how you burned the iso to cd.

What software did you use, and what settings (which way you went about it).


When you put your cd into the drive, what do you get when you click on the icon.

What kind of computer are you using (pc, mac...)

---

### Post by code_08 on 2005-06-02
Usually in the cd burning software there is an option to burn/copy an image to a disc. this will fix your problem. if you just write that file to the disc it does nothing other then store the file and if you unpack it it is the same thing

---

### Post by ajsadler on 2005-06-02
I'm on a PC.
Using WinXP.
I wrote the ISO file firstly using the inbuilt software in Windows.
And just tried writing the image using MagicISO

What writing software do you suggest?

---

### Post by bored2k on 2005-06-02
[QUOTE=ajsadler]I'm on a PC.
Using WinXP.
I wrote the ISO file firstly using the inbuilt software in Windows.
And just tried writing the image using MagicISO

What writing software do you suggest?[/QUOTE]
 Nero or Alcohol 120%

You can get a demo of Nero > [http://www.nero.com/en/nero-prog.php](http://www.nero.com/en/nero-prog.php) and Alcohol 120% > [http://www.alcohol-soft.com/](http://www.alcohol-soft.com/)

I'd go with Nero, it's user friendlier.

Open it up select burn image to disc, and select the .iso. I suggest you burn at a slow speed like 12x.

---

### Post by ajsadler on 2005-06-02
I will try that.
I'm currently also downloading the InstallCD version of Ubuntu504-i1386 which I might try on an empty partition on my computer.

---

