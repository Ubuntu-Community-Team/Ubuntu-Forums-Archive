---
title: "Computer Shuts Down Without Reason"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by Deadpool on 2008-12-18
I've recently had trouble with my computer shutting down whenever I do a strenuous task (mainly involving the internet) the computer simply shuts down. The major times when it happens are when I do something on the internet that tasks the computer, so watching a video or playing a flash game. It seems like it may be more of an issue with the memory, but if there is anything I can do inside of Ubuntu to try and help with the issue I would like to know about it.

---

### Post by mkvnmtr on 2008-12-19
Might be dirty. Unplug it and open the box. See if you don't have a lot of dust. Might be making things heat up. The little cans of compressed air might solve your problem.

---

### Post by Ghliofris on 2008-12-19
I had the same problem with my laptop. Come to find out, it was overheating! :shock: 

Next time it shuts down, reboot and go into the BIOS. Look at the PC Health and see at what temperature it is running at and what temperature it is set for shutdown. Mine is set at 75c to shutdown. It runs at 31c for system and 45c for CPU, I also have overclocked my CPU from 1800 to 2200.

I agree with mkvnmtr, a good cleaning might be in order. Before blasting it with a can of air, which is really cold when it comes out, wait till your computer is cooled down to room temp.

Make sure that the CPU fan and case fans are running. Check the power supply fan also. If any are not running, replace them.

---

### Post by Tomatz on 2008-12-19
Yeah its overheating. Buy some canned air, its a good way of removing dust from hardware.

[http://www.circuitcity.com/ccd/productDetail.do?oid=59373&om_keycode=4](http://www.circuitcity.com/ccd/productDetail.do?oid=59373&om_keycode=4)

---

### Post by cyberdork33 on 2008-12-19
> **Deadpool said:**
> I've recently had trouble with my computer shutting down whenever I do a strenuous task (mainly involving the internet) the computer simply shuts down. The major times when it happens are when I do something on the internet that tasks the computer, so watching a video or playing a flash game. It seems like it may be more of an issue with the memory, but if there is anything I can do inside of Ubuntu to try and help with the issue I would like to know about it.

Any OS in particular?

---

### Post by Deadpool on 2008-12-19
Thanks, i'll try cleaning out the computer and see if that works

---

### Post by stream303 on 2008-12-22
The only time I had a computer shut down that wasn't related to overheating was when the graphics card wasn't configured right, and it ended up being the graphics memory just stopping the machine.

I was trying to drive a monitor that was too large for my early-model graphics card to support, so I had to drop my bit depth down from 24 back to 16.  Basically a video memory issue.

---

### Post by Deadpool on 2008-12-25
I just ran hddtemp while tasking my computer with a youtube video. The applet spat 33 degrees Celsius at me right before the computer shut off. It doesn't seem to be overheating. Does anyone have any other recommendations, as I would hate to have to bring it in to the Genius Bar and deal with the Mac guys (I run Hardy on a macbook).

---

### Post by Irako on 2010-09-12
Hello all, I just start working Ubuntu, I really love it, but it suddenly shut down my computer with no reason. I see here comments this is an over heating problem but...

Why the same machine running Vista ( I have both, Vista and ubuntu) Still running all time with no problem???

Is it possible Vista controls an over heating system, like fan starting when CPU is warm, which ubuntu doesn't have???

I know over heating control mostly is conotroled by BIOS but...

Is there a possibility????

---

### Post by linuxopjemac on 2010-09-13
I would try the new fan control script:

```
sudo apt-get update
sudo apt-get install macfanctld
```

---

