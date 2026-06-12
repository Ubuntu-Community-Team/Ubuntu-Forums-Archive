---
title: "Failed to start session &amp; password incorrect -- mac book pro with rEFInd boot manager"
date: 2015-11-09
forum: Apple Hardware Users
---

### Post by stefan36 on 2015-11-09
Hello,

I'm relatively new with ubuntu, and I will appreciate if someone can advice me to resolve my issue. The problem is that I cannot log in ubuntu again.
It started when I tried to reinstall the battery indicator on ubuntu. After that logged out and I've tried to log in, but did't succeded.
The system prompt me a message "Fail to start session". After that I tried to reset my password through opening the terminal window, but there I get "incorrect password", nevertheless I'm 100% sure about the password accuracy.

Thank you in advance!

Stefan

---

### Post by ajgreeny on 2015-11-09
If macs work like "normal" machines for recovery mode and the password setting, try the instructions at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This way you don't even need to remember the old password; you just make a new one, which can, of course, still be the original that you used.

Worth a try, I think.

---

### Post by stefan36 on 2015-11-10
I'm using rEFInd boot manager with triple OS (ubuntu/mac os X/windows 7) and such GRUB menu cannot be called/entered which provides option to ubuntu recovery mode menu choice. I've tried unsuccessfully some another workaround (not sure it will helps) -- via USB stick, by booting the ubuntu, and after that, using the terminal to mount the partition. The returned message was for read only partition.

---

### Post by este.el.paz on 2015-11-10
> **stefan36 said:**
> I'm using rEFInd boot manager with triple OS (ubuntu/mac os X/windows 7) and such GRUB menu cannot be called/entered which provides option to ubuntu recovery mode menu choice. I've tried unsuccessfully some another workaround (not sure it will helps) -- via USB stick, by booting the ubuntu, and after that, using the terminal to mount the partition. The returned message was for read only partition.

@stefan36:

On my triple boot/rEFInd set-up MBPro now running LM 17.2 . . . I believe that if I run "automatic" install in ubuntu the install maybe does OK, but, if I choose "Manual" and I only set up "Home" and "swap" partitions, the installer says "installation successful" but, will not boot the linux system.  If I use SuperGRUB2 CD I can boot the system, but it won't "repair" . . . .  Therefore, I have to set up a small 10 MB partition flagged as "bios_grub" in front of the other two partitions . . . run the install again, shut the computer down, and then on reboot--it works . . . .  The OSX boot manager window opens showing the two (for me) OSX partitions, on the one that has rEFInd on, when I pick that one the rEFInd window opens and I can pick "linux" OR from OSX Boot manager the "windows" icon will go directly to linux GRUB window and will select linux . . . .  I'd suggest trying to run the install again, either trying "automatic" into "largest free space" OR manual, but with at least 3 partitions, one named "bios_grub" (or whatever is closest).

e.e.p.

---

