---
title: "Cannot switch back to Mac"
date: 2010-02-24
forum: Apple Hardware Users
---

### Post by pheonix7856 on 2010-02-24
I installed ubuntu 9.1 today, my friend also installed it using a disc which I borrowed
Everything seemed to go fine.  I used boot camp to make a partition after going through the installation process I found out that, that was a bad idea and i just made a ubuntu partition of 18gb.  I was able to get rid of the bootcamp partition so now i Just have free disk space left out of that.  

I wanted to switch back to my Mac to get to work on somethings after I had installed ubuntu.  However a after the GRUB and clicking on Mac
A black screen with words and numbers I haven't seen before popped up.
Here is some of what it said

panic (cpu 0 caller 0x2ad0d5): Incompatible boot args version 1 revision

Debugger called <panic>
Backtrace (cpu 0) frame return ad. 4 potential args on stack
 ** alota numbers here**


BSD process name corresponding to current thread: unknown

Mac os version: not yet set
**some other stuff here*

I really just want to use my mac again.  It doesn't matter to me if I still have ubuntu or not.  If someone could please help me resolve this in the easiest possible manner.
Thank you

---

### Post by linuxopjemac on 2010-02-24
can you boot with the option command (Alt) pressed during boot after the startup boing. It should give you an option to boot OSX.

---

### Post by wheeeler on 2010-02-25
Try booting from your Mac OS X install CD (hold 'C' during boot).
 
After you pick your language, click the Utilities menu and launch Startup Disk
 
Choose your OS X partition and reboot with your fingers crossed.
 
If that doesn't work, you can use your Ubuntu live CD to mount your OS X partition and copy any essential files to another disk (external, flash media, etc), and then use your OS X install CD to reformat and install OS X.
 
There may be a less destructive method to accomplish this task, but this is how I would handle a screwy hard drive.

---

