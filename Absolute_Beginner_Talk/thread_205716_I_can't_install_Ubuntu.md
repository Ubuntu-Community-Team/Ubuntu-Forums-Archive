---
title: "I can't install Ubuntu"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Resslerdylan on 2006-06-28
I just recently got Breezy and I can't install it...i dont know whats going on.  I put the CD in the drive and it does absolutely nothing.  I restarted my computer with the disk in and it still did nothing.....SOMEBODY HELP ME#-o

---

### Post by underworld288 on 2006-06-28
make sure that in your BIOS you have it set up to where your cd-rom drive boots up first.

---

### Post by Resslerdylan on 2006-06-28
ummmmmmmm, what?
I dont know how to get to my BIOS

---

### Post by underworld288 on 2006-06-28
when your computer first starts up there will be a sortof loading screen before the Windows loading screen (this is when you computer is doing POST) you pressthe Delete button at this screen.

---

### Post by Maggot on 2006-06-28
Do you recall ever being able to boot off a CD before?

---

### Post by jrd on 2006-06-28
> you press the Delete button at this screen.
It's not always delete that gets you into bios. What type of computer do you have?

---

### Post by Resslerdylan on 2006-06-28
I have a Dell Dimension 2400...when I press delete, I get a screen that says "safe mode   -   safe mode with command prompt   -   last known good configuration   -   start windows normally"

My windows is messed up, no windows commands work eg:windows-r for run, I have to run through the task manager.  My start bar is gone completely, also.  This may be the problem?

---

### Post by underworld288 on 2006-06-28
try F1 then.

---

### Post by jrd on 2006-06-28
I think it's F2 for a Dell (maby I'm wrong). Just keep tapping it after you boot the computer till it enters bios. I guess the best thing to do is tap F1 and F2 that way either way it will work.

---

### Post by confused57 on 2006-06-28
Try pressing F12 when Dell logo screen comes up, this should present you with the option of booting from the CD drive.

That's what I have to do with my Dell Dimension 4550...

[quote=underworld288]not all the time because on my computer I have to press F10 to do that![/quote]

You might have worded it differently, for example:  "on my computer, I have to press F10 to enter the boot options!", which might have been good advice earlier, when you were mentioning pressing del, F1, etc. to enter bios.

---

### Post by underworld288 on 2006-06-28
not all the time because on my computer i have to press F10 to do that!

---

### Post by catlett on 2006-06-28
[QUOTE=underworld288]not all the time because on my computer i have to press F10 to do that![/QUOTE]
Aren't you the guy who started by just saying delete? So don't post a reply like that when you started off with > you pressthe Delete button at this screen.  The forums are for helping new people get their systems running. It is not a place to play "I am smarter than you". 

If you are on this site it means you have internet access, go to Dell's site. Go to support and look for technical information etc. Somewhere it will let you know about getting into bios.

Bios is the software that is running your motherboard. It is seperate from windows. 

Once you find out how to get in (with my old Dell I had to press delete or something TWICE to get in the bios) you will be shown a text based menu. You move around the menu with the arrow keys on your keyboard and press enter to get into sub-menus.

Get to boot. In the boot section is the order which your motherboard starts the boot process. There will usually be 4 options (but they are not all exactly alike) floppy, cd drive, hard drive and removable devices. Like I said some are different. It could say hard drive 1 and 2 then flopy etc.

The point is they will be in an order. If the hard drive is set to boot before the cd drive then you won't be able to boot from a cd because the computer will boot to your hard drive and your hard drive is bootable.

You want a floppy, cd drive, hard drive setup. The 4th can be what's left. 

So set the boot order in your bios to floopy, cd then hard drive. 
Usually you press F10 to save and exit bios. Then your computer will boot to a cd.

The next question is "Did you "burn" the iso to disk or did you "write" the data to disk" You have to burn the image of the iso file to disk. Writing or copying the iso to a disk will not make a bootable cd. If your computer doesn't boot to the cd after you fix the bios this may be the issue.

In my signature is a very thorough how to about installing from the live cd. It describes how to burn an iso.

Good luck.

---

### Post by jrd on 2006-06-29
> The forums are for helping new people get their systems running. It is not a place to play "I am smarter than you". 
Well said.

---

