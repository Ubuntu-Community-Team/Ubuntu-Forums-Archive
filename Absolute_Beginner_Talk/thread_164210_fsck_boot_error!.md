---
title: "fsck boot error?!"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-22
THis is the second time this has happened to me, and i'm getting pissed.  

I normally start up ubuntu, but it goes to the black and white screen and says something about "fsck error"

Then it says exactly:

"Error reading block 1924652 (or some random number) (Attempt to read block from filesystem resulted in short read) while doing inode scan. Ignore error<y>?"
then i type "yes" and i get this:
"Force overwrite<y>?"
so i type in yes again and all of this is repeated for different "blocks"
after about 10 of these or so, (and some start with "[4295595.608000] Buffer I/O error on device hda1, logical block 8724585 (or some other number)" before the "error reading block" part) it says "root@ubuntu:~$"
so i type in reboot and then it reboots normally.
This has happened twice to me, and each time i have just typed yes and yes as many times as i have to, and then typed reboot.
What is this?

---

### Post by Mustard on 2006-04-22
It's saying you have errors on your hard drive that need to be fixed I would think, or it could just be saying that it is having trouble reading the drive.  Is this when you first start up in the morning?

If it is when you first start up from a cold boot after the computer has been sitting idle for many hours, then its probably related to the hardware not being ready to go when the kernel springs into action.  I've noticed this on my system anyway.  When I get to my computer in the morning, I boot up, and then just move the cursor down on the grub menu, so that it doesn't automatically start up.  Then I walk off and make a cup of tea, and when I get back I make a selection from the grub menu.

As long as I give the system time to 'warm up' everything works fine. :)

---

### Post by user1397 on 2006-04-22
[quote=Mustard]It's saying you have errors on your hard drive that need to be fixed.  Is this when you first start up in the morning?[/quote]
Yes! but I can't stress enough that it has only happened twice evr. It usually boots up normally, anytime of day.

---

### Post by user1397 on 2006-04-22
oops! double post

---

### Post by user1397 on 2006-04-22
[quote=Mustard]It's saying you have errors on your hard drive that need to be fixed.  Is this when you first start up in the morning?[/quote]
Yes! but I can't stress enough that it has only happened twice evr. It usually boots up normally, anytime of day.

---

### Post by Mustard on 2006-04-22
Yeah, the connection to the forum went a bit haywire for a while.  I edited my above post if you want to read the edit. :)

---

### Post by user1397 on 2006-04-22
Can I avoid it completely just by hibernating instead of sutting down?

---

### Post by Mustard on 2006-04-22
[QUOTE=erik1397]Can I avoid it completely just by hibernating instead of sutting down?[/QUOTE]

Well, I don't know whether your issue is exactly the same as mine, so I couldn't definitively give an answer to that.  The only way to know, is to try it out.

Did you have shutdown problems prior to these errors occuring?

---

### Post by user1397 on 2006-04-22
[quote=Mustard]Well, I don't know whether your issue is exactly the same as mine, so I couldn't definitively give an answer to that.  The only way to know, is to try it out.

Did you have shutdown problems prior to these errors occuring?[/quote]
No, all of my shutdowns were normal. I guess i'll just try hibernating from now on and see what happens.

---

