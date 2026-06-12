---
title: "First Ubuntu Install.....issue"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Hooly on 2006-08-27
Hi all,

I'm new to Linux and I could use some help. If I come across as a complete noob, it's because I am.  I have the 6.06 disc and I am dual booting with windows.  When I boot the disc and choose install, it goes through some steps like mounting root files etc.  When it gets to "Adding Live CD User", it stalls, then eventually comes up with "Buffer I/O error on device sr0, logical block sector xxxxxx" problems.  What exactly is this?  I just reformatted my laptop but I have used the Live CD before.  Now it doens't even start.  I have done a "Check CD for Defects" and everythingn was fine, except when it go to "./filesystem/squash.rs" or something like that.  

I'm wondering if all this is common or if someone can shed some light on the issues for me.  I have a fresh hard drive just waiting for an OS.

Thanhks all

:confused: :confused: :confused:

---

### Post by GuitarHero on 2006-08-27
What speed did you burn it at?

---

### Post by bodhi.zazen on 2006-08-27
> **Hooly said:**
> Hi all,

I'm new to Linux and I could use some help. If I come across as a complete noob, it's because I am.  I have the 6.06 disc and I am dual booting with windows.  When I boot the disc and choose install, it goes through some steps like mounting root files etc.  When it gets to "Adding Live CD User", it stalls, then eventually comes up with "Buffer I/O error on device sr0, logical block sector xxxxxx" problems.  What exactly is this?  I just reformatted my laptop but I have used the Live CD before.  Now it doens't even start.  I have done a "Check CD for Defects" and everythingn was fine, except when it go to "./filesystem/squash.rs" or something like that.  

I'm wondering if all this is common or if someone can shed some light on the issues for me.  I have a fresh hard drive just waiting for an OS.

Thanhks all

:confused: :confused: :confused:

Sounds like a bad burn. Check the md5sum of your iso. If OK re burn.

---

### Post by Shadyman on 2006-08-28
Does your CD have any kind of scratches or blemishes on it? :|

---

### Post by Hooly on 2006-08-28
No scratches or blemishes.  The CD runs fine if I have booted windows and use it to view ubuntu programs through xp.  I didn't burn it, it's from shipit I had sent to me.  I'll try downloading the iso and burning it myself at a slow speed.

Thanks for the input!

:D

---

### Post by daou on 2006-08-28
There is a CD check tool when you boot the computer with the Ubuntu CD. Instead of choosing "Start or install Ubuntu", run the CD check instead. That will tell you if you have errors.

---

### Post by Hooly on 2006-08-28
I did run the CD check.  It had a problem at "/filesystem/squash.rs" (or something like that).  It said it had a mismatch.  I have installed XP on a partition so I don't know if there is confusion as far as file systems go (NTFS on that partition) but I have a 20 gig unformatted partition waiting for ubuntu.  Going to downlaod and burn it tonight to check that.

---

### Post by blent07 on 2006-08-28
It very well could just be a defective CD. Even if it was sent to you, life happens and things break. An error in a specific file would sound to me like it was bad to begin with, not related directly to your computer or the windows partition. 

but i'm certainly not speaking from experience.

---

### Post by bodhi.zazen on 2006-08-28
Sounds like a bad CD. You can always download the ubuntu iso and burn a new CD.

---

