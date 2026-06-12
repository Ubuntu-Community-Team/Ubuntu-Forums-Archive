---
title: "Installed HP dvd 840--now hd running wide open all the time--what did I do??"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-20
I just finished installing the HP dvd 840 internal drive on my compaq 5900Z comp (Ubuntu 6.06.1-256 RAM AMD 700Mhz processor, 40 Gig hd). I can play dvd"s, read cd's and everything fine so far but now the hd activity light on the tower stays lit up all the time, and I see a noticeable slowdown in my RAM speed--internet web pages loading, applications in nautilus, and other comp activities that were pretty fast before. The light does seem to flicker brighter when surfing the web during page downloads but it never stayed on like this before. Any ideas as to what I did wrong??

---

### Post by iluminate on 2007-01-20
Greetings,

I have no clue but maybe we can narrow the problem down.
Have you tried to unplug the DVD player to see if the light is still on?
Is the DVD connected on the same IDE as the HDD?
Check jumper settings...
Try to use IDE2 for DVD player....

Only suggestions =)

---

### Post by jerrynewt on 2007-01-20
I will give both suggestions a try -- Thanks for the quict response--be back in a few.

---

### Post by jerrynewt on 2007-01-20
As a post script- I unplugged the old cd ROM and used the power cable and data cable plugs that were plugged into it. I also set the jumper to"cable select" just like the cd/rw unit below it. The original cd ROM is still in the tower but not hooked up at all, just the new dvd and original cd/rw.

---

### Post by jerrynewt on 2007-01-20
Just finished checking things out and the two cd units are on drive 1 and the hd is on drive 0 (IDE) so they are not sharing at all. Everything returns to normal if I unplug the data ribbon from the new dvd unit. I just can't understand why it would have any effect on the hd if they are not on the same IDE controller. I'm not very comp literate so this could be way over my head. I would appreciate any suggestions or solutions from someone with a lot more tech savvy than me (which includes about 99% of all of you out there). Thanks for the replies--I'll be waiting.

---

### Post by jerrynewt on 2007-01-20
This probably is going to sound silly but should I run the CD that came with the dvd unit? It is supposed to install Nero OEM Suite which includes drivers, but if there are no drivers in linux for this how is it working at all?

---

### Post by jerrynewt on 2007-01-21
Bump ](*,)

---

### Post by oilchangeguy on 2007-01-21
no it would be a waste of time to try and load the nero cd, it's not written for linux. try this,  set the new dvd drive to master, and the old cd/rw drive to slave and see if that has any effect. the reason the drive works is the same reason it would work in windows, both os's have some drivers already loaded. the nero cd only contains the burning software, which windows would not already have. go to the dvd makers website and see if there are any new drivers for linux. and if nothing else return it (even though it seems to work) for another one and try that.

---

### Post by jerrynewt on 2007-01-21
I just went ahead and took the unit back--seem the 700Mhz processor I have wasn't up to the task--needs at least 800 Mhz to operate. Any way I'm looking into upgrading processor to 1 Gig or better (whatever the motherboard will stand. Thanks for the reply.

---

