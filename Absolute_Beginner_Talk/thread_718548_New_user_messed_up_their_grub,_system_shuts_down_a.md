---
title: "New user messed up their grub, system shuts down at login screen now?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-08
I was browsing Techguy.org and came across this post.  Thought I would forward on some suggestions from you guys.  He's having a problem with grub....  I don't think he's provided enough details... so you'll have to figure out the problem based on computer symptoms (unexpected shutting down).

Original Post:  [http://forums.techguy.org/unix-linux/690918-ubuntu-crashes-personal-injuries-pending.html](http://forums.techguy.org/unix-linux/690918-ubuntu-crashes-personal-injuries-pending.html)

> I don't know anything about Ubuntu/Linux. My gal pal has this laptop with Ubuntu on it and she forgets her password so I tried to help. I found this how to on the Ubuntu forum and followed the directions:

Turn your computer on.
Press ESC at the grub prompt.
Press e for edit.
Highlight the line that begins kernel ........., press e
Go to the very end of the line, add rw init=/bin/bash
press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
Type in passwd <username>. Set your password.
Type in reboot.

When I typed reboot and hit enter, it said that a connection couldnt be made and gave me a prompt again. So I turned the computer off and back on.

When left alone, grub loads, the splash screen comes up and then the log on screen tries to come up but the computer shuts down.

I tried removing the the splash and quiet commands to see where it was failing in the boot process and each time it is in a different spot.

Any suggestions? Thanks in advance.

---

### Post by insineratehymn on 2008-03-08
Yeah, that doesn't sound like a very good idea to begin with.

Why do that anyway?

If you can get to the Grub screen again, go back in and delete the line you just added and all should be well.

---

### Post by diablo75 on 2008-03-08
Their reply:

> Thanks for the reply, but the added line is no longer there. It just allows you to change the password on the next boot. When I go to edit the kernel line now, it looks like normal.

---

