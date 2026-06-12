---
title: "Installation... is this working?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by TimChang on 2006-11-05
Hi,

I'm a newb at this Ubuntu stuff, and I'm not sure if I'm going about this correctly. I downloaded Ubuntu 6.10, burned it to a CD, and tried to install it on my Dell Dimension 4700 Desktop over (to try to erase) my Windows XP Pro.

I have 1 GB Ram, and 2 CD-ROM drives, and I'm loading from the main CD-ROM drive into RAM (I think).

The CD boots up to the installation menu. I changed the video to 1024 x 768 x 32 and then changed the boot options to be:

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw acpi=off splash --

We hit return, and the we see two green "Loading" messages, one on the top-left corner, and one at the top-middle of the screen. The CD is spinning, the hard disk is not, and nothing changes...we've been waiting for about an hour.

Anyone know if this is working, or am I supposed to see something?  Is there something I'm missing?

Help!

--TC

---

### Post by bollix47 on 2006-11-05
Did you try loading the install cd without making any of those changes?

---

### Post by podunk on 2006-11-05
An hour for a 20 minute install with no hard disk activity - I'd say it's not working. :-)

Can I ask a question (and understand I'm new at this to and not being a smart ***) why did you pass all those arguments to the boot up? Why don't you just load it in once and see if it will boot up and do it's thing?

---

### Post by TimChang on 2006-11-06
Oh, yes, I actually tried to run it at first just by clicking the regular install button.  The same thing happened.  So I went into the "Advanced settings" and basically saw the line you see there, except I changed it by removing a "quiet" parameter.  I thought that would let me see what it was doing.  =/

--TC

---

### Post by SunnyRabbiera on 2006-11-06
Try Dapper instead?
Dapper might work better for you, as "latest" doesnt always mean "greatest"

---

### Post by rsambuca on 2006-11-06
try adding ide=nodma as a boot option.  This turns off the direct memory access and has worked for some of us to get the live CD to boot up.  If you want to install the system onto your hard drive, you will want to re-activate the dma prior to doing the install, or it will take you quite a long time.

---

### Post by bollix47 on 2006-11-06
If you have onboard video try going into the bios setup during boot and look for video memory. If it's set to 1meg change it to 8meg.

I had a problem with a Dell once and the install CD wouldn't work because of that.

---

