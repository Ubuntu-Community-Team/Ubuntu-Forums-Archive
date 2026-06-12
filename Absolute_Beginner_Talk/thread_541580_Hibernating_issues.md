---
title: "Hibernating issues"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-09-03
When I click the hibernate button I get the following error message:

HAL failed to hibernate

I know this has been brought up time and time again, and I apologise but I believe my problem is slightly different to that of others.

At first when I tried to use the hibernate option my computer just froze up and when I could see the mouse it was stuck at a point on the screen and my screen was black.

Then I did a bit of research and I found this solution: [http://ubuntuforums.org/showthread.php?t=471855&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=471855&highlight=hibernate)

at the time when I did the: sudo s2ram (to suspend), it put the laptop to sleep and I could resume and continue using without a problem. Now I get this error:

> 

Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "HP Pavilion dv5000 (RF999EA#ABV)  "
    sys_version  = "F.17"
    bios_version = "F.17"
See [http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram) for details.

If you report a problem, please include the complete output above.


Also, when I did the --force option the computer just freezes up on resume (with black screen).

Doing sudo s2disk (hibernate) gives the following error: 
> 

suspend: Could not use the resume device (try swapon -a)


Before it worked fine.

Finally, I changed the two HAL files as recommended in the post.

So at first everything was fine, I tested it a few times (by pressing the shutdown button, and then clicking hibernate and sleep). Then I restarted the computer and I've been getting these errors, and when I try to sleep and hibernate using the shutdown button, my computer goes into the lock screen mode asking for my password to unlock, and upon unlocking I get the Hal failed to initialize error.

Since then I have changed the files back so now if I click on sleep my computer goes to sleep and when I click the power button to resume I just get a black screen and I have to hold down the power button to reboot. If I hibernate the same thing happens.

Any thoughts?

---

### Post by obscur156 on 2007-09-04
Do you have a USB KEY pluged in???

I had problems with hibernation too.
I finally found that it was because of my AVIXE usb key pluged in.
I unplug the usb key before hibernation and VOILA,no more problems.

But maybe that's just me.
Best regards,good luck.

---

### Post by abhiroopb on 2007-09-05
Not sure what an USB key is, but I unplugged all my USB devices and tried it, and still the same thing.

---

### Post by obscur156 on 2007-09-05
A usb key is kind of like a little hard drive but its flash memory that you plug via a usb port.You can google it to see how it looks like.
Their is lots of format, 1 gig to 8 gigs or even more.

Of course if you did not know what it was ,you did not have one.
I hope someone will  give you an answer.

Best regards,good luck.

---

### Post by abhiroopb on 2007-09-05
Sorry, I didn't understand because I just call it a flash drive :P. And like I said I tried hibernating with EVERYTHING (external hard drive, webcam, keyboard, mouse) unplugged.

Thanks anyway. Hibernating seems like a pretty big problem!

---

### Post by abhiroopb on 2007-09-07
Haven't had any reply...should I start a new thread??

---

### Post by abhiroopb on 2007-09-10
Bump

---

### Post by isaacj87 on 2007-09-10
Could you give the Brand and Model # of your laptop?

---

### Post by cubeist on 2007-09-10
I have never been able to hibernate on my hp laptop but I have managed to get suspend working ok by following this tutorial:

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-89d16b15960aeb34ac020b17ac1120c534482e3e]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-89d16b15960aeb34ac020b17ac1120c534482e3e")

also, since I have an embedded nvidia graphics I had to add an option to enable soft EDID's.  Unfortunately I cannot find the link that shows how or where to add this.  Try the above link first and then see if you still have problems.

---

### Post by abhiroopb on 2007-09-19
My laptop is the HP Pavilion dv5242ea

---

