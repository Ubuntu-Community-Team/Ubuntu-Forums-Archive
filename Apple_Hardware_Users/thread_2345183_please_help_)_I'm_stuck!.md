---
title: "please help :) I'm stuck!"
date: 2016-12-01
forum: Apple Hardware Users
---

### Post by jxk2 on 2016-12-01
hej guys. 
I am trying to install Ubuntu and Kali on the same machine. I did a lot of reading, and in theory it should be possible! :)
During the install of either one (I tried ubuntu first, then kali on top on the other way round), I get stuck.

Does anybody run both systems and could tell me how to accomplish that? I suppose I need two partitions? right?
how should they be partitioned to make that work properly?

Thank you so much! I know its a dumb question and I wouln't post if I haven't tried everything else before.

cheers

---

### Post by zapp2 on 2016-12-01
What for device are you trying to run it on?

---

### Post by jxk2 on 2016-12-01
thanks for the quick reply! Its a Macbook Air

---

### Post by col48 on 2016-12-01
I'm no Kali user, but it should be straightforward as both are Linux flavours.  Yes, two partitions (or three with a swap partition, to share).

This link suggests you may want to take a different approach:

[https://www.quora.com/Which-Linux-OS-should-I-use-as-a-beginner-Ubuntu-or-Kali-Linux-and-why](https://www.quora.com/Which-Linux-OS-should-I-use-as-a-beginner-Ubuntu-or-Kali-Linux-and-why)

---

### Post by jxk2 on 2016-12-01
thanks for the reply! also the link is a good read! thanks. I like the usability of ubuntu and miss all of that in kali, which is only for pentesting. 
would be great to have both..

so you suggest two partitions and two separate boot records? 
(since kali is debian and boots somehow other than ubuntu)  .. :-/

---

### Post by howefield on 2016-12-01
Moved to the "*Apple Hardware Users*" forum for the time being.

---

### Post by col48 on 2016-12-01
We're getting into unknown territory for me!

Unless Kali demands exclusive use of the HDD (and even Windows doesn't demand it, although it rather assumes it when installing!), you will be able to have a Kali partition and a Ubuntu one.

Since Grub (the bootloader used in an Ubuntu environment) can know about Windows, it can surely know about Kali, so that a choice can be offered at boot time?

For all I know, an exclusively Kali machine may also use Grub.

In a VM, the issue is irrelevant; you'd boot to Ubuntu and start Kali from there.

---

### Post by jxk2 on 2016-12-01
I am overwhelmed by the quick and friendly help. I will try the first option and separate ubuntu from kali partinioning-wise. 
I will report back. Otherwise I'll go with the VM option. Never thought of that. Very good point! thanks!! :KS

---

### Post by #&amp;thj^% on 2016-12-01
Just to add my 2 cents here.
I have found on multiple try's  Dual booting with Kali && Ubuntu brought nothing but grief and a lot of time wasted on findings errors on either OS.
But Kali on its own drive IE: HDD SSD or even Thumb (Pen Drive)...Left me with a much better user experience and far less time wasted with problems.
But again that is just my 2 cents worth.:)
Kind Regards

---

### Post by jxk2 on 2016-12-01
good 2 cents :) but tell me please: do you live-boot kali or did you actually install kali on a thunbdrive? are there a lot of speed problems, since everything is going over usb .. 
again, great 2 cents!

---

### Post by #&amp;thj^% on 2016-12-01
> **jxk2 said:**
> good 2 cents :) but tell me please: do you live-boot kali or did you actually install kali on a thunbdrive? are there a lot of speed problems, since everything is going over usb .. 
again, great 2 cents!

I have both... Hard install to its own SATA drive and one on a SanDisk 32 Gig Ultra.
The Install to hard drive is more robust, quicker, and snappy.
The Pen Drive is just short of that with (Very) short freezes...but not a show stopper for me anyway:D but all in all I much like my machine to be speedy and fast..so I boot to hard drive install more...but when I need the most security IE on line Banking and such, I use the Pen Drive.:) BTW there are faster read/write Thumb Drives out there from what I use.
Hope this is useful.

---

