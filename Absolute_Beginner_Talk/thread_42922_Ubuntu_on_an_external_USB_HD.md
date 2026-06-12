---
title: "Ubuntu on an external USB HD"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by morficus on 2005-06-19
I just spent my whole weekend trying to get ubunto to run from my external USB hard drive with no success. Kept getting a 'Kernel Panic' at boot time

I found a few support pages that showed how to solve this issue, but all methods required my to mount a file using a LOOP DEVICE. When I try this... I first get this error:
"io_ctl:LOOP_CLR_FD: Device or resource is busy"
"mount: you must specify the file system"

if I try to mount right after... I get this
"mount: could not find any free loop device"

I headed over to my /dev/loop/ directory... only to find that I only have one loop device (named '0'). I was able to free the loop device, but whenI tried mounting.. I kept getting the same error:
"io_ctl:LOOP_CLR_FD: Device or resource is busy"
 ](*,) 

can somebody PLEASE help me with this issue... it's driving me crazy!  :-x 

-morficus

---

### Post by diebels on 2005-06-20
not sure, but maybe loop is missing from initrd.
Edit /etc/mkinitrd/modules and add loop
run dpkg-reconfigure linux-image-2.6.10-5-386

---

### Post by chaumurky on 2005-06-20
[QUOTE=morficus]I just spent my whole weekend trying to get ubunto to run from my external USB hard drive with no success. Kept getting a 'Kernel Panic' at boot time

I found a few support pages that showed how to solve this issue, but all methods required my to mount a file using a LOOP DEVICE. When I try this... I first get this error:
"io_ctl:LOOP_CLR_FD: Device or resource is busy"
"mount: you must specify the file system"

if I try to mount right after... I get this
"mount: could not find any free loop device"

I headed over to my /dev/loop/ directory... only to find that I only have one loop device (named '0'). I was able to free the loop device, but whenI tried mounting.. I kept getting the same error:
"io_ctl:LOOP_CLR_FD: Device or resource is busy"
 ](*,) 

can somebody PLEASE help me with this issue... it's driving me crazy!  :-x 

-morficus[/QUOTE]
 Man, that's over my head - is this really an absolute beginner topic?

---

### Post by morficus on 2005-06-20
[QUOTE=chaumurky]Man, that's over my head - is this really an absolute beginner topic?[/QUOTE]

yeah... 'cause this is the first time I'm using linux.....

---

### Post by morficus on 2005-06-20
[QUOTE=diebels]not sure, but maybe loop is missing from initrd.
Edit /etc/mkinitrd/modules and add loop
run dpkg-reconfigure linux-image-2.6.10-5-386[/QUOTE]

in my case, it's 2.6.10-5-686

but I'll give this a try

---

### Post by chaumurky on 2005-06-20
[QUOTE=morficus]yeah... 'cause this is the first time I'm using linux.....[/QUOTE]
 My hat's off to you then. I admire your courage going straight for a kernel rebuild!

---

