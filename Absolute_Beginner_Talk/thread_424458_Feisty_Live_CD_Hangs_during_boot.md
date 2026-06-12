---
title: "Feisty Live CD Hangs during boot"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by sfmcinm0 on 2007-04-26
I'm having a problem with the Feisty live CD.  The boot screen appears, I make my choice, then it goes to the screen with the Orange progress bar.  The hard drive activity light and the DVD drive activity light both go out, and the floppy drive light goes on and stays on.  

Here is my hardware specs:

Core 2 Duo E6600
Asus P5B Deluxe w/Wifi
2 GB DDR2-800 Ram
Evga Nvidia 8800GTS 320MB Video card
Samsung Eide DVD-RW Drive
Maxtor Eide 300GB HD
Mitsumi Floppy Drive w/card reader

Could the card reader built into the floppy drive be causing problems?

Or am I still being bit by the JMicron Eide bug?  I have added the "all-generic-ide" parameter, but the CD still hangs.

System boots just fine into XP, Sabayon Linux, and Mepis (text only on Mepis, though).

Any help out there? I really liked Ubuntu on my previous system, but none of the versions I have tried have worked on my new system.:confused:

---

### Post by Quickened on 2007-04-26
I was advised to use the Fiesty Alternate Install Disk and it solved my install woes!

---

### Post by Skidpad on 2007-04-26
When you say none of the Ubuntu versions you've tried work on your new system (nice system by the way :)  ) - do mean they all hang at the floppy drive access and fail to boot?

Many LiveCD boot problems are caused by error-prone cd's, but I do find it curious yours hangs at the floppy.  Have you tried unplugging the drive or burning the disc at a slower speed?

---

### Post by sfmcinm0 on 2007-04-26
They had a different problem  - error messages without booting to desktop.  Researched this forum and found that the Jmicron eide controller wasn't supported by the kernel version.  I decided to wait until the final version of Feisty came out.

Oh well.  I'd really prefer to use the live cd until I can gets some hd space cleared to install.

---

### Post by sfmcinm0 on 2007-05-09
Ok, this post can be considered Solved.  I tried to boot again, hit alt-F1 to get Verbose, and I was greeted with several error messages relating to the floppy drive.  I waitied a little while longer, and it booted to the Ubuntu desktop.

For some reason, my floppy drive has failed.  It's brand new, never been used before.  That's what was causing the messages - Ubuntu was doing what it is supposed to do.

Now I have to decide if I should bother to replace it or not...

---

### Post by hyper_ch on 2007-05-09
Floppies are still being produced? ^^

Good to have that issure sorted out... if you encounter more problems or have questions --> then you know already how to get an answer :)

enjoy!

---

