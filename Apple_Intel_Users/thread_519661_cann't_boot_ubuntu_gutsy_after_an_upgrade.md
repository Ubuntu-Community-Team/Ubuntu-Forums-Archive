---
title: "cann't boot ubuntu gutsy after an upgrade"
date: 2007-08-07
forum: Apple Intel Users
---

### Post by epaulin on 2007-08-07
my laotop is MacBook Pro 3rd with updated ubuntu gutsy AMD64 version.

I upgraded my ubuntu gutsy today, removed the old kernel which came from Install CD(2.6.20?),  and then the system cannot boot again.

Then I press the shutdown button then boot again, there was a "GRUB" on the screen, nothing else, keyboard doesn't work I can't input words.

Then I boot from a Install CD, running into resume mode, starting a shell, remove the old grub dir, grub-install & update-grub & remove the splash changed the default to old kernel, then reboot again, nothing was changing, 

It will running into a dark screen when I reinstalled grub, reboot then will running into a screen with "GRUB".

press "esc" didn't bring the grub menu list.

I did look into the system, the kernel was there, menu.lst looks fine too, I don't know what the hell is going on.

---

### Post by epaulin on 2007-08-07
I just start from Install CD to resume mode again, reinstaled the old kernel 2.6.20-15 from fesity install CD, then reboot again, nothing changes, even wired, sometimes it will reboot if there is a CD  in the cdrom.
And I checked the aptitude log, grub didn't upgrade recently, so, what is the problem could it be?

---

### Post by cyberdork33 on 2007-08-07
boot from a live cd, mount your ubuntu partition to a folder, and use chroot to the folder you mounted the system on.

Then you can can run apt-get and hopefully fix the damage by running things such as 'sudo aptitude reinstall grub' and the like, of course I would run updates first to make sure. How did you remove the old kernel? I believe that is where your problems came from.

---

### Post by epaulin on 2007-08-07
I reinstall grub to /dev/sda (before I installed to /dev/hda3), then problem solved magically.

I'm still don't known what going on here, maybe is cause by the virtual MBR or my MBR already corrupted.

But it works, then I'm happy.

cyberdork33:
>>I believe that is where your problems came from.
I don't think so, if it was the problem, then it should work after I reinstalled the old kernel from install CD.
Besides, I got another kernel 2.6.22-8 which is what I'm using before.

---

### Post by cyberdork33 on 2007-08-07
Glad you got it working.

If you edit your menu.lst file, you can set the number of kernels you want to keep on your machine, then when there is a kernel update, it will automatically remove older kernels.

---

### Post by epaulin on 2007-08-07
Wow, didn't know it before.
I'll looking into it, tnx.

---

