---
title: "Error 17, and even SGD wont work!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by tmask on 2007-10-24
Ok, I'm a newbie at linux.  I made the switch to linux at the end of summer, starting with Fedora core 7 (bad idea), but eventually found my way to Ubuntu and have been happy ever since! :)

But now i'm in a jam.

I'm dual booting Vista (shudder) and Ubuntu 7.04 Fiesty.  Until recently i've had minor problems with unmounting CDs and USBs, but now I can't boot up!  Ubuntu keeps throwing out "Error 17: Unable to mount" or something to that extent.

A whole day of searching later, I download the Super Grub Disk and go through it. Still nothing!  I've tried many different suggestions on the forums here and elsewhere, but they dont work. 

PLEASE! :confused: I need help!

Could it be something about this extra partition on my drive i found?
It was listed under "Extended" being only 2.39 GB, I didn't think anything of it and deleted it. :( 

thank you guys!

- Tom

---

### Post by LaRoza on 2007-10-25
> **tmask said:**
> 
Could it be something about this extra partition on my drive i found?
It was listed under "Extended" being only 2.39 GB, I didn't think anything of it and deleted it. :( 

thank you guys!

- Tom

Looks like you deleted swap. If you don't understand something, don't mess with it, from now on.

Fixing fstab will probably fix the probably, or reinstalling grub.

---

### Post by adrian15 on 2007-10-25
> **tmask said:**
> Ok, I'm a newbie at linux.  I made the switch to linux at the end of summer, starting with Fedora core 7 (bad idea), but eventually found my way to Ubuntu and have been happy ever since! :)

But now i'm in a jam.

I'm dual booting Vista (shudder) and Ubuntu 7.04 Fiesty.  Until recently i've had minor problems with unmounting CDs and USBs, but now I can't boot up!  Ubuntu keeps throwing out "Error 17: Unable to mount" or something to that extent.

A whole day of searching later, I download the Super Grub Disk and go through it. Still nothing!  I've tried many different suggestions on the forums here and elsewhere, but they dont work. 

PLEASE! :confused: I need help!

Could it be something about this extra partition on my drive i found?
It was listed under "Extended" being only 2.39 GB, I didn't think anything of it and deleted it. :( 

thank you guys!

- Tom


If you cannot boot Linux with GNU/LINUX -> BOOT LINUX option (in the super grub disk) because you have an error 17 then you should run the fsck from a live cd to your / linux partition.

Ask someone else about the fsck options and howt to do it.

adrian15

---

### Post by tmask on 2007-10-25
ok, so i'm not going to delete anything like that again.

Fsck i've tried before with my liveCD, I'll try it again and get back to you with the results.

Again thanks so much for helping me guys :( I know it sucks to have to answer simple questions, so thank you for willing to help me out :)

I've opend up GTparted using liveCD 7.10 and checked the drive before, but nothing happened.  Is there any way I can replace that extended drive?  Or for hat matter, could I access my home folder long enough to back everything up?

---

