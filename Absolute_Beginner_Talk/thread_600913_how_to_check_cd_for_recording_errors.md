---
title: "how to check cd for recording errors?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by tomot on 2007-11-02
I have Gutsy installed on 2 computer systems, and both hang
under various circumstances.

First system hangs each time I try the Update manager.
I have 11 updates to download. Gutsy hangs each time
I'm 25% through the download stage.

Second system hangs each time the Update manager
tried to install the updates.

But there are other instances as well, I was opening the
Synapatic Package Manager once when the system .....froze!

never had that happen with the 7.4 OS

I'm starting to wonder if there is are some corrupted files that got transferred 
to the cd when I burned it. 

Is there a way to do a checksum of the files on the cd against the Downloaded ISO files?

---

### Post by Pumalite on 2007-11-02
Boot off the Live CD and check for corruption. 3rd or 4rth in the menu.

---

### Post by tomot on 2007-11-02
what exactly is supposed to happen, after I do that?

I get the following:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter "help" for list of built in commands.

(initramfs)_   

and a blinking underscore, what command do I type to check the CD?

TIA!

---

### Post by rsambuca on 2007-11-02
> **tomot said:**
> what exactly is supposed to happen, after I do that?

I get the following:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter "help" for list of built in commands.

(initramfs)_   

and a blinking underscore, what command do I type to check the CD?

TIA!

Something must be messed up.  When you run the CD integrity check it should either tell you about corrupted files, or tell you that the CD is fine.  I would re-burn the iso at a lower burn rate.

---

### Post by tomot on 2007-11-02
thanks for the input.

can someone confirm that the following:

My copy of:  ubuntu-7.10-desktop-i386.iso  contains 729,608,192 bytes 
(this is what XP tell me)

TIA!

---

### Post by rsambuca on 2007-11-02
If you still have the original iso, then just run an md5sum check to make sure it is error free.  [Instructions are here]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by Pumalite on 2007-11-02
You have to do md5sum on iso.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by tomot on 2007-11-02
1) the checksums did match when I did the compare.
2) I made another CD copy of the ISO 
this time I used InfraRecorder.
2x cd speed, session at once
3) so now when I boot from the new live CD
I get the same screen:
 BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter "help" for list of built in commands.

(initramfs)_ 

Is there anything else I can do, apart from doing a new install?

---

### Post by Pumalite on 2007-11-02
Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit
You will now boot into the LiveCD normally.(hopefully)

---

### Post by tomot on 2007-11-02
tried your suggestion several times
and in the end, I still end up with:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter "help" for list of built in commands.

(initramfs)_

---

### Post by Pumalite on 2007-11-02
Try Alternate CD

---

### Post by tomot on 2007-11-02
the Alternate cd was the first install of 7.10 I tried.
I used the "Install in Text mode" feature from the menu

After the install was complete, the OS rebooted to a blank vga screen.
I think I will forgo anymore 7.10 installs for now.

thanks for your help.

---

