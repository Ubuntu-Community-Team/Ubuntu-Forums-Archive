---
title: "Help with Virtualbox"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by XopherLorenz on 2008-01-31
I wasn't sure where this thread should go.  I thought about putting it in the virtualization section, but I was afraid of getting answers that went way over my head.  Please remember that I am a complete novice.

I'm trying to use Virtualbox to run Vista on Gutsy and to be perfectly honest, I haven't a clue where to begin.  I got Virtualbox software up and running and I went though various wizards that it puts me through to try and set it up but for some reason it's not working.  I can only assume that I need the vista setup CD (which I have), but when I try to power my vista VM on (with the boot cd in my drive) I get this:

FATAL:  Could not read from the boot medium! System halted.
_

I'm not really sure what that means, and any help would be much appreciated.

---

### Post by raydeen on 2008-01-31
Check your settings for the virtual machine you created. Make sure that the CD rom is activated and mounted  and set to read from the drive you're putting the Vista disc in (click the CD-Rom label on the right of the main VBox screen). Also check the boot order of your machine. Sounds like it's trying to read the virtual hard drive first and not the CD drive. Click the Settings button at the top of the VBox window and then under the General tab, click the Advanced button and make the boot order so that the CD drive is above the hard drive.

---

### Post by XopherLorenz on 2008-01-31
Thanks.  I tried that, and Vista is currently installing without a hitch

---

