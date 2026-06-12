---
title: "Ubuntu won't boot, not sure how to even summarize this"
date: 2011-07-18
forum: Apple Hardware Users
---

### Post by micseydel on 2011-07-18
I run triple boot Ubuntu Natty Narwhal on a Macbook Pro 5,5 and have mostly had great success.

Today everything, was fine, I don't believe I had upgraded or done anything unusual too recently, although I did install the newest version of the kernel whenever that came out. I closed the lid and it was supposed to go to standby (can't verify if it did) and several hours later I went to open the lid and got no response even when I hit the power button, keyboard keys, and fiddled with the mouse, and tried closing the lid and reopening it too. Closing it caused the white light on the front to turn on, but nothing really helped, even though I think I heard the hard drive a little bit. I held the power button to turn it off, and heard the harddrive head click to a resting position.

I then tried to reboot, and EFI, the Mac bootloader, seemed fine. I later realized I can still boot into OS X and assume Windows works as well. However, when I tried Ubuntu (which I still have to go through GRUB from EFI to get to), it hung at a purple screen. I tried again with no more success, and then tried recovery mode and it hung twice at the screen with the attached image that I took with my phone.

After seeing this, I booted from an Ubuntu boot disk and used VirtualBox to try and boot my installed Ubuntu partition. I used
$sudo VBoxManage internalcommands createrawvmdk -filename godihopethisworks.vmdk -rawdisk /dev/sda5 -register

to create the virtual harddisk for VirtualBox, which I then ran with sudo and got this error -- "FATAL: No bootable medium found! System halted." I don't have an easy way to test that I'm doing the VirtualBox part correctly, but I believe I've done that before to repair corrupted Ubuntu installs. When I Googled that error, I didn't find anything useful.

Does anyone have any suggestions? I must have a working Ubuntu install, so I'll probably backup and do a fresh install as soon as I can. If someone in the mean time happens to know of a simpler solution though, that would be FANTASTIC!

Thank you for even reading my post,
Michael Seydel

---

### Post by conundrumx on 2011-07-19
Looks like pretty standard output.

It's possible the new kernel isn't handling power management on your Macbook properly, try booting the old one.

---

### Post by micseydel on 2011-07-19
Thank you for the response!

I forgot to include this, but I thought I did try booting the one old kernel I had, having it not work. I did try again though, and it seems magically be working after I backed up everything in preparation of a full format.

I'm afraid it has something to do with standby, which I'll probably avoid, but if I accidentally do it and replicate this problem I'll post by.

---

### Post by conundrumx on 2011-07-19
A better solution might be exploring how many of the tools you use in Ubuntu work fine in OSX, and perhaps exploring virtualization as a solution instead, but to each his own.

---

### Post by micseydel on 2011-07-19
I used OS X for about a year but I do a lot of programming Python, and while installing third party modules with Ubuntu has been a snap, I've had numerous difficulties with OS X.

Regarding virtualization, do you mean running Ubuntu from within OS X all the time?

---

### Post by conundrumx on 2011-07-20
> **micseydel said:**
> I used OS X for about a year but I do a lot of programming Python, and while installing third party modules with Ubuntu has been a snap, I've had numerous difficulties with OS X.

Regarding virtualization, do you mean running Ubuntu from within OS X all the time?

I don't have any particular advice for python on OS X, unfortunately.

And yes, I was suggesting using Ubuntu within OS X, but if you're only booting into Ubuntu (or the vast majority of the time) that's pretty moot.  If you were using OS X as your primary OS it would make more sense.

---

### Post by teejmya on 2011-07-20
I had a lot of random issues with this on my Macbook (White plastic, 6,1) and they all seemed to vanish when I installed the proprietary drivers for my nvidia card. Try that.

---

