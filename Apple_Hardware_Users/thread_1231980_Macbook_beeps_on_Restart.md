---
title: "Macbook beeps on Restart"
date: 2009-08-05
forum: Apple Hardware Users
---

### Post by Brightbelt on 2009-08-05
Hi,
 I've just installed Ubuntu 9.04 on my Macbook and I have 2 issues:

1) If I'm in Ubuntu and do a computer restart, my Macbook starts beeping during the restart phase. It doesn't stop on it's own so I have to manually shut it down. Then I can boot up and everything seems fine at that point.

This is very disconcerting so I'd really like to have this solved....

2) I have no sound. So I've tried the traditional sound fix, which is:

```
sudo gedit /etc/modprobe.d/alsa-base.conf

options snd_hda_intel model=mbp3
``` 

And I still have no sound, so I'm at a loss there. 
I really appreciate any help or pointers on these. Many Thanks, Frank B.

---

### Post by llamabr on 2009-08-05
regarding number 1, do you just want the beeping to stop, or are you saying it won't reboot at all?

I hate that loud beep.  You can disable it by:

[http://ubuntuforums.org/showthread.php?t=717169](http://ubuntuforums.org/showthread.php?t=717169)

---

### Post by Brightbelt on 2009-08-05
Thanks for responding Llamabr - actually you're right. It won't reboot either, so I guess that's a real problem. 

I will try disabling the beep in the meantime through the instructions given in your link there. Many Thanks for that.

So I guess I do have a rebooting problem.

Thanks, Frank B.

---

### Post by crocowhile on 2009-08-05
> **Brightbelt said:**
> 
2) I have no sound. So I've tried the traditional sound fix, which is:
What model of MBP do you have? For the new ones there's a new fix - need to recompile the kernel module.

---

### Post by Brightbelt on 2009-08-05
Hi Crocowhile,
   Thanks for responding. I have the newest model of the 13" Macbook, not a Macbook pro. I hope that helps. Thanks, Frank

---

### Post by crocowhile on 2009-08-05
> **Brightbelt said:**
> Hi Crocowhile,
   Thanks for responding. I have the newest model of the 13" Macbook, not a Macbook pro. I hope that helps. Thanks, Frank

Then follow [this]("http://ubuntuforums.org/showpost.php?p=7627817&postcount=98"). It will work.

---

### Post by Brightbelt on 2009-08-05
Well Crocowhile, I did all of it and I still have no sound, despite the fact that I think it all went through correctly. I did have to do the last lines of code twice. I might have forgotten to enter my password on the first round. Anyways, I rebooted and tried again and everything seemed to compile like it should.

And I restarted and checked for muted channels etc. Still no sound.

I appreciate the help and I'm open to more ideas I guess.

Thanks, Frank B.

---

### Post by crocowhile on 2009-08-05
Hi Frank,
could you please run the following command?

```

sudo dmidecode -s system-product-name

```

If by newest 13" you mean the 5,5 then that way should really work. Maybe the newest alsa module snapshot has some trouble? In that case I could upload mine somewhere.

---

### Post by Brightbelt on 2009-08-05
Yes Crocowhile, I got this when I ran your command:

MacBook5,1

---

### Post by Brightbelt on 2009-08-07
Sorry, but *Bump*

---

### Post by fyz on 2009-08-07
I got the same problem of rebooting. I can have sound from headphone only, but NOT from internal speaker.
My machine is 'iMac9,1'. Try everyting, still no luck to fix the rebooting and no sound problem.

---

### Post by Brightbelt on 2009-09-04
I finally fixed my sound - go to the Community Documentation here --->
[https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)

It's down towards the bottom.

---

### Post by Tompalaz on 2009-09-04
Rebooting problem solved for me since 2.6.30 kernel.

---

### Post by Brightbelt on 2009-09-04
I thought I had found a fix for my boot problem on here from another post/thread doing a grub fix like this using the LiveCD:

```
sudo grub
find /boot/grub/stage1
root (hd0,x)
setup (hd0,x)
```

But it didn't fix the boot issue and also, I now have 2 tuxes at the rEFIt boot menu from which to choose.

I appreciate any help on this for sure. Many Thanks to everyone so far for your input,...Frank B.

---

### Post by Brightbelt on 2009-09-04
Hi Chynna16, if there was something you did to solve your boot problem, could you share it with us? 

Perhaps it solved itself somehow, if that's what you meant? Thanks, Frank B. [Chynna16 has since deleted his/her post]

---

