---
title: "Can't boot - mounting problem"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by somersetsimon on 2006-10-16
Hi - I'm a complete novice to Linux, so I'd appreciate any help...

I installed Ubuntu a couple of days ago and everything seemed fine. Today I'd tried to boot, it got to the mounting bit then jumped to a new page...

Mounting root filesystem

mount: Mounting /dev/hdd1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such drive or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init

I originally had a single hard disk with XP installed. I installed a second hard disk and installed Ubuntu on this drive.

Last time I used Ubuntu, I plugged in a USB and was able to access it ok. When I booted up today, the USB stick was still in. WOuld this make a difference?

Any clues? Thanks

---

### Post by Kateikyoushi on 2006-10-16
Try to reboot after the USB stick is removed.

---

### Post by somersetsimon on 2006-10-16
I tried rebooting with and without the USB stick attached. I don't have anything worth keeping, so it's no big deal to reinstall Ubuntu. However, I don't think I did anything unusual, so I want to know what caused the problem :confused: 

If it's of any interest, I followed all the default settings when I installed - I erased the entire second hard disk to install Ubuntu. 

The worrying thing is that it worked fine, then stopped working without me doing anything wrong (hopefully). That's what I hoped Linux would save me from :-k

---

### Post by somersetsimon on 2006-10-16
I'll probably reinstall Ubuntu tomorrow. Are there any special tips to make sure this problem (whatever it is) doesn't happen again?

---

### Post by somersetsimon on 2006-11-05
> **somersetsimon said:**
> Hi - I'm a complete novice to Linux, so I'd appreciate any help...

I installed Ubuntu a couple of days ago and everything seemed fine. Today I'd tried to boot, it got to the mounting bit then jumped to a new page...

Mounting root filesystem

mount: Mounting /dev/hdd1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such drive or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init

I originally had a single hard disk with XP installed. I installed a second hard disk and installed Ubuntu on this drive.

Last time I used Ubuntu, I plugged in a USB and was able to access it ok. When I booted up today, the USB stick was still in. WOuld this make a difference?

Any clues? Thanks

Well, it's happened again :( 

I've been running Dapper for a week or so and even got my wireless network and network printer working.

This morning, all my ubuntu applications stopped working. I couldn't even bring up a terminal window to sort the problem out. I remembered that Ctrl-Alt-F2 did something, so I pressed those keys. It then jumped out of X windows, back to something that looked like recovery mode with a login prompt. I then rebooted, but the boot failed with the same messages as in my original post. How can I recover from this?

---

