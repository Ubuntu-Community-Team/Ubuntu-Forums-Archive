---
title: "Gutsy won't completely shutdown on laptop"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2008-02-17
I have a Toshiba Satellite Pro 6100 - Intel 1.8 Gig processor - 768 Gig RAM - 120 Gig HD, running Gutsy. Before updating kernel, Gutsy would shutdown just fine and comp would shut off just fine. Now after update, Gutsy gets to the end of shutting down (Progress bar almost to the end) and just stops and stays there. I now have to manually power down the laptop with the power button. I read somewhere in the forums a while ago that adding acpi=off would fix the problem. If so where do I add this. Thanks for the help !

---

### Post by sb12 on 2008-02-17
> **jerrynewt said:**
> I have a Toshiba Satellite Pro 6100 - Intel 1.8 Gig processor - 768 Gig RAM - 120 Gig HD, running Gutsy. Before updating kernel, Gutsy would shutdown just fine and comp would shut off just fine. Now after update, Gutsy gets to the end of shutting down (Progress bar almost to the end) and just stops and stays there. I now have to manually power down the laptop with the power button. I read somewhere in the forums a while ago that adding acpi=off would fix the problem. If so where do I add this. Thanks for the help !

you add it to the kernel line in menu.lst

---

### Post by fatality_uk on 2008-02-18
Assuming that you have an intel chipset, If that doesn't work, try the following. Worked for me on my desktop. I entered ACPI=off and that didn't work.

```
sudo gedit /etc/init.d/halt
```

Now add the following in this place in the do_stop() function

Add the line in **BOLD**
```
do_stop(){
**modprobe -r snd-hda-intel**
if [ "$INTHALT" = "" ]
...
```

---

### Post by zyvx on 2008-02-18
what about AMD? I have the same problem only i didn't notice when it started because I don't turn off the comp much.

---

### Post by fatality_uk on 2008-02-18
> **zyvx said:**
> what about AMD? I have the same problem only i didn't notice when it started because I don't turn off the comp much.

Sorry can't say. I took this from a hack I applied to my eeePc and thought it might work on my desktop and bang it did! I don't think it's Intel dependant actually now I read a bit more about it. All I can say is make a backup of your **halt** file in **/etc/init.d/** and then apply the patch and see how it goes!

---

### Post by billy.joe on 2008-02-23
Thank you, My eee pc wasn't shuting down eather.
I am now going to try this hope it works.. this is the last bug I have with my eeepc.

I love it.  I think every one should have an eeeubuntu

---

### Post by billy.joe on 2008-02-27
It did Thank you.

---

