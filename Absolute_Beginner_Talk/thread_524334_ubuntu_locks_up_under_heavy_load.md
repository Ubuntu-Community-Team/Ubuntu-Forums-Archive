---
title: "ubuntu locks up under heavy load"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by u-slayer on 2007-08-13
Recently, ubuntu keeps locking up randomly under heavy load. Like today I had it encoding some video files while surfing the net. I managed to go for a few minutes doing this before everything just ground to a halt and I could here the hard drive seeking like a madman. 

Tried <ctrl><alt>x to launch xkill.
 -didn't work
Tried going into tty1
 -managed to login in, but it never actually showed the prompt to start issusing commands
Tried to go back into the graphical thingy and it wouldn't even display. I had to do a hard reboot with the power button.

I thought that linux was always supposed to be function at the command line and you just restart the gdm?:( In the past I could always get into tty1 and never had to push the power button.

---

### Post by ramjet_1953 on 2007-08-13
What are your hardware specs?

Processor type and speed

How much RAM do you have?

Is it shared with your video?

How big is your swapfile?

Regards,
Roger :cool:

---

### Post by u-slayer on 2007-08-13
Toshiba Satellite M100 series.
Dual Intel T2300 @ 1.66 GHZ

1 gig of Ram, No Swap file, never needed it.

---

### Post by ramjet_1953 on 2007-08-13
Might I suggest that if you are encoding videos, using a GUI and also surfing the net, a swap file just may be a good idea?

Regards,
Roger :cool:

---

### Post by u-slayer on 2007-08-13
> Might I suggest that if you are encoding videos, using a GUI and also surfing the net, a swap file just may be a good idea?


I don't think that is the problem. My ram usage is never above 500 megs (even when encoding video and surfing the net) leaving me plenty of breathing room.

---

### Post by ramjet_1953 on 2007-08-13
OK, you may have enough RAM, but the processor load under those conditions would be quite intensive.

I always just leave the system alone, when it is encoding, as it has plenty to do with just that operation.

There is always the risk of corrupting the iso and having nasty things like the synchronization of sound and video slipping.

It is like being in a room and having several people asking you questions all at once.

Certainly, your brain has the memory capacity, but the processor will have problems with the multi-tasking.

Funnily enough, women seem to be able to handle it OK.

Perhaps we should make female CPU's????

Regards,
Roger :cool:

---

### Post by wirelessmonkey on 2007-08-13
Video encoding is incredibly I/O intensive.  Even if your RAM usage doesn't stay steadily high, it may spike and cause system instability or unresponsiveness.  In situations where that occurs, the system will write to swap, even if it uses that swap quickly.  On the other hand, if you crash gdm to get to a command prompt, it may kill your encoding application, depending on how it was started.   You may just need to wait after logging in.  Occasionally it takes a minute or two (or so it seems) for your terminal session to get its turn in the process list after logging in.

---

### Post by Hospadar on 2007-08-13
Also, if you are going to video intensive website (sites like cnet or youtube that have a lot of flash on them etc.) and you arn't running a video card with good drivers (i.e. if you have an nvidia card with no nvidia drivers, etc.) this could also really tax your system as it would put a lot of extra load on your ram and processor.

It may also be that you are just unlucky and have some piece of hardware with a driver that makes it bug out a little and cause instability.

---

