---
title: "Checking file systems at every boot - why?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-10-25
Hi community!

In a different thread, I tried to find out why my boot time to Ubuntu was always over 3 minutes, compared with about 40 seconds to XP.

Applying the fstab fix to avoid checking the Windows file from [http://ubuntuforums.org/showthread.php?t=447996](http://ubuntuforums.org/showthread.php?t=447996) then I got my Ubuntu boot time down to about 42 seconds, which is OK for me.

What confuses me now is - why do I go through the "Checking file systems" routine at every boot?
I understood it should only happen every 30 boots?
I have not had any obviously "dirty" shut-downs.
I ran Checkdisc in XP with no comments.
I tried AutoFsck which seemed to work one time but had no effect after that.
Even forcing the 30-boot target with their optional script did not work.

Is there somewhere I can find a marker for whatever is triggering this check every boot?

Thanks!

---

### Post by Joeb454 on 2007-10-25
Do you shut down XP properly, instead of just holding the power button until it goes off I mean.

If you don't use the proper XP shutdown buttons, then it'll probably be that. I know if you don't shut down Windows properly it won't mount the drive correctly for Read/Write access.

---

### Post by 2CV67 on 2007-10-25
Yes (I was going to say "of course", but on an absolute beginners forum I won't) I shut down Windows properly by clicking on the usual sequence of buttons, then waiting till it dies fully before turning power off.

---

### Post by candtalan on 2007-10-25
The reason which first comes to my mind is that somehow the bios has the date wrong. If this is true, then the bios battery is flat maybe?
I am not sure here, but it is worth a check

---

### Post by shae on 2007-10-25
If you are referring to why the computer wanted to check your fat32 partition every day (and hence disabled it) involves some random problem that comes up in certain configurations.  Since your fat32 partition does not need to be disk-checked in linux (you can let windows handle it), it should be fine that way.  If it is one of your linux partitions that needs to be checked over and over, then you might have a serious problem and could even be a sign of hardware failure.

---

### Post by 2CV67 on 2007-10-25
Thanks for those 2 comments.

For the BIOS battery - the clock & date information on the screen is always exactly correct.
Does that eliminate the BIOS battery?

For finding which partition is causing the problem - that is exactly my question:
Is there not a marker in a log somewhere which would show me which partition or what problem is calling for a check?

Thanks!

---

