---
title: "Unable to resize partition"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by DrunkPeanut on 2007-04-27
I've decided to resize my Windows partition to make room for Ubuntu. So, I defragmented my hard drive because I read somewhere that you're supposed to do that before partitioning. I also used Windows' CHKDSK application to repair errors just to be on the safe side.
However, when I started installing I found out that I couldn't resize my partition, and the error message offered no explanation. I saved the "details" file to find out what had happened, but that didn't help either. I also tried to use Gparted, but got the same results.
I would like to point out that I'm not willing to format my hard drive for Ubuntu- I'm installing it more out of curiosity than anything else.
I've tried all this several times and searched the net before I realized It was hopeless to continue on my own... I'd appreciate any help you can offer (even if it's only telling me to give up :P).
Thanks!

---

### Post by Bachstelze on 2007-04-27
Try resizing your partition using GParted's official live CD instead of Ubuntu's.

[http://gparted.sf.net](http://gparted.sf.net)

---

### Post by DrunkPeanut on 2007-04-27
Thanks, I'll try it :)
I'll post again to say if it worked or not.

---

### Post by freebird54 on 2007-04-27
I Suspect that the problem is your copy of the Windows equivalent of a swap file, called the page file.  If you turn that off, along with hibernation if you have that, and THEN run the defrag, empty space will be created.  Unfortunately Win usually puts the page file at the end of the partition - which blocks a resize operation.

Don't forget to turn it on again after you have resized the Win partition (when you go back to Win for a look again - whenever that is) :)

Hope this helps!

---

### Post by DrunkPeanut on 2007-04-27
Seeing as the HymnToLife's idea didn't work, I think you might be right. 
I have no idea how to turn the page file on/off though... I'll need some extra help for that.

---

### Post by whee on 2007-04-27
> **DrunkPeanut said:**
> Seeing as the HymnToLife's idea didn't work, I think you might be right. 
I have no idea how to turn the page file on/off though... I'll need some extra help for that.

Try these tutorials at your own risk:

[http://www.codinghorror.com/blog/archives/000422.html](http://www.codinghorror.com/blog/archives/000422.html)
 
and

[http://www.blackviper.com/WinXP/supertweaks.htm](http://www.blackviper.com/WinXP/supertweaks.htm)   (scroll down)




PS: What application did you use to resize the Windows partition with?
I did this some time ago with Partition Magic for Windows, it went smoothly.

---

### Post by DrunkPeanut on 2007-04-27
My god, this forum is so helpfull... I might end up formatting and installing Ubuntu just to hang out here :) Thanks!

---

### Post by marco123 on 2007-04-27
on XP?

Go to - Control Panel, System, Advanced.  There will be an option to turn off page file for that drive.

As for hibernation - Power Options, Advanced,  and uncheck the box.

Edit: Oops beaten to it, lol

---

### Post by dptxp on 2007-04-27
I could resize my Primary partition (where I have XP) with no problems.
While installing Kubuntu 7.04 Feisty Fawn.

---

### Post by DrunkPeanut on 2007-04-27
Thanks! After disabling the page file I was able to resize the partition.
You guys are great :D

---

