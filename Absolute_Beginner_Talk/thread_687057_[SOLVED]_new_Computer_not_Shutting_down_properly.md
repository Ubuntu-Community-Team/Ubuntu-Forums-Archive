---
title: "[SOLVED] new Computer not Shutting down properly"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by very_japi on 2008-02-03
My boyfriend has been strugguling with vista ever since he bought his new PC, a HP Pavillion Tx1000 (a tablet PC; i thought it would never run linux). I finally convinced him to give linux a try :) .

I tried installing Gutsy... total failure. So i installed the Alpha version of Hardy Heon- I was afraid it might be unusable, beeing an Alpha in development and all... but it actually worked quite nice. Everything worked out of the box except for the Touchscreen, wireless, and fingerprint reader.

Got the wireless, Compiz, screen rotation, and touchscreen to work... :guitar: miracles DO happend.

Anyways, theres one proble i havent been able to figure out:

When i shutdown / reboot one of this two events occur:

1.- Screen goes terminal-black and reads:

```
---
[COLOR="Red"]System is shutting down, please wait...[/COLOR]
---

```

And it just Hangs there, the log-out sound playing over, and over again like some old Long Play Album from the 60's hell.

2.- 

>  Running local boot scripts (/etc/rc.local)

(which just happends to be the last out put on tty1 during boot)


IF I TRY to go on a terminal and type sudo reboot or sudo poweroff, the process Hagns at:

```
* Saving the system clock
```

I would be so embarassed if, after long hours of work to get everything else to work, i had to tell him to go back to vista just because of this.

My honor is at stake here, guys. Please help!!

---

### Post by very_japi on 2008-02-04
SOLVED

added "noapic nolapic" to the end of the kernel line in 'boot/grub/menu.lst'

---

### Post by Skiabq on 2008-02-06
Thank you VERY much for this post. I have spent more time than I would like to admit trying to get Ubuntu on my TX1000 (TX1220US to be more precise). I downloaded 8.04 Alpha 4 and have it installed on my computer right now. The only thing I couldn't get to work was during installation the  autoconfig partitioner would hang, I just did that part manually. I didn't even have to use the acpi option that you did. 

This install went so smoothly and so much is working on my computer now I was a little hesitant to do all the updates, but those went smoothly too. 

I do have a question as to exactly how you got your wireless to work. I am an absolute beginner and could use any help you would be willing to offer in this area.

Thanks again

---

