---
title: "Cannot Boot From USB using Grub"
date: 2016-10-11
forum: Apple Hardware Users
---

### Post by PMackie1 on 2016-10-11
Hello everyone,

I have installed 16.04 on my 2008 Macbook and it's much zipper after the install 4gb Ram and SSD. I have read that i should ideally have Trusty Tahr installed as my OS to prevent any bottlenecks. 

I have copied the OS (16.04) over no problem now I am having a hard time getting Grub 2 to boot from USB (14 ish - whatever Trusty Tahr is).

There is no system BIOS present so I must use Grub.

I am trying to get this going with this tutorial: [http://blog.viktorpetersson.com/post/93191892924/how-to-boot-from-usb-with-grub2](http://blog.viktorpetersson.com/post/93191892924/how-to-boot-from-usb-with-grub2)
[LIST]
[*]Getting Specific here, i tried locating the vmlinuz & initrd files. 
[*]can you help me with the above tutorial instructions if my filepath is: /casper/vmlinuz & /casper/initrd 
[/LIST]
                

Really struggling and it's frustrating because I am 9/10 of having a really nice machine.

Have you experience this before? Any assistance would be appreciated. 

Thanks in advance

---

### Post by yancek on 2016-10-11
You have Ubuntu 16.04 installed on your Mac and it boots, correct?
How did you copy 16.04 and where did you copy it to?
Did you install 14.04 on the usb?  What software did you use?
It isn't really clear to me what you are trying to do.  Do you want to boot an Ubuntu on a usb drive from the internal Ubuntu?  You can do that with an entry in the grub.cfg file on the main drive, just chainload it.  You don't need Grub on the usb.

---

### Post by howefield on 2016-10-11
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by PMackie1 on 2016-10-13
Thanks for your reply Yancek.

Let me give you more info on what I am running and what I want to do:

Currently have 16.04 on mac and it boots just fine. No worries there. 

I forked the OS from my old HD to my SSD using some terminal commands (gddrescue / ddrescue). Then I installed the SSD in the Mac and viola! it works so far. 

Unetbootin was used to create a bootable USB. 

I really want to install 14.04 on this system and not dual boot. Any way i can boot the USB and begin the install. 

Very interested in any solutions!

Thanks again

---

