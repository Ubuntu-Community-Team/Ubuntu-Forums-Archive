---
title: "Returning back w/ Installation Problem"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by mrwonx on 2007-08-30
I was using Ubuntu back a few months ago, but due to some problems with a project I was working on, I was tricked into thinking it would be easier on Windoze. It wasn't, but I muddled through and finished. I'm now ready to come back and pick up were I left off. Only problem is after my installation, I get an "Operating System not Found" error (not sure the exact text - it's at home, I'm at work). I checked my boot order, and it has the right HD first (My Sata Drive), and if I boot from the cd, I can choose the option to boot the first hard drive, and it will boot up fine. 

What do you guys think my problem is? I downloaded the updates last night before going to bed. I havn't checked back and rebooted yet, so for all I know it could have been fixed with an update.

---

### Post by avidnameddavid on 2007-08-30
Try reinstalling GRUB: [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

---

### Post by s26c.sayan on 2007-08-30
Did you install windows *after* Ubuntu?
In that case , [this ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")might be of help.

---

### Post by mrwonx on 2007-08-30
I did what the links said, and so far I've gotten it to load grub (which is good), just now my kernal selections don't get me anywhere

Still looking and playing with it. Let me know if you find anything else that might be helpful.

---

### Post by mrwonx on 2007-08-31
Ok, I'm getting an error 17. It's trying to mount hd2,0. that's what it came up as when I did the find on it. Didn't tell the install to do it, though.

I have 2 Sata and 2 IDE hard drives, and the first Sata is were this is being installed.

---

### Post by mrwonx on 2007-08-31
Would it matter that the grub installed to hd0 and is pointing to hd2? Grub loads, but can't mount. Should I re-install and point it to install it on hd2?

---

