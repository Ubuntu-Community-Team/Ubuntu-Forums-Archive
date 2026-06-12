---
title: "the fan is always working?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by hanuman1000 on 2007-05-12
hi

i have ubuntu feisty in my new HP, and i notice that the fan is constantly on making noise. The cpu goes up to +60 C almost instantly when i turn it on. I have Computertemp as an app and there i can change the max temp down to +50 - is this a good thing to do? I dont want the fan working all the time...

---

### Post by Lucifiel on 2007-05-12
> **hanuman1000 said:**
> hi

i have ubuntu feisty in my new HP, and i notice that the fan is constantly on making noise. The cpu goes up to +60 C almost instantly when i turn it on. I have Computertemp as an app and there i can change the max temp down to +50 - is this a good thing to do? I dont want the fan working all the time...

First things first,

1) NEVER trust temperature values from a software.

This is because such values are often read from the sensor chip which measures the temperature of the air around the hardware(in this case, the cpu). Such values can be as much as 1.x to 2.x times the original value. 

If you want a more accurate reading, try using a probe. Unfortunately, I've no idea how to use that, though. You'd have to enquire in some hardware forum, instead. 

If you want to know how hot your pc is, when the computer is running, put your hand near the cpu(be sure not to get in the way of your cpu fan. :p ). If you're using some branded computer, then you can't open the casing. But you can put your hand at the back of your pc, near the power supply unit and feel for yourself how hot the air is. :p 

2) Linux tends to be more demanding when using system resources. 

3) Which fan are you talking about? Power supply unit fan, cpu fan or something else? 

Note: all fans are meant to be on. There is no way to turn them off unless you disconnect it or remove it from the computer or the fan has a controller(which is either in the front of or the back of your computer). You cannot turn off a cpu or psu fan or your entire computer system would overheat and all your hardware parts will die(as in "fry", being melted).  

If you can't hear the fan, it just means the fan is working but very quietly. 

I suggest that you leave the fans alone and learn more about hardware first. Then, when you've known enough, you'd be able to know whether it's safe to tinker around with certain fan/hardware settings and what not. :p 

4) If you want to know what's causing the fan to spin so loud, open up Terminal and type "top".

Edit: Finally, don't worry about the fan or anything.

---

### Post by mt330404 on 2008-03-29
i'm having the same problem, when I had Windows XP installed on my computer (Sony VAIO VGN-A150 laptop) the fan NEVER used to be this loud... but now on Ubuntu Gutsy, it runs 100% of the time. It's really annoying if I'm in public and trying to be low-key about being on my laptop. I don't want to disable the fan bc that would obviously cause things to run slower/majorly destroy my innner-workings. What is it about Ubuntu that requires fan usage 100 percent of the time?!??!

---

### Post by stefangr1 on 2008-03-29
According to my brother (I configured a dual boot system for him), his notebook works 3.5 hours with windows-xp, and only just over 2 hours with Ubuntu. I haven't looked at the temperatures, but increased power consumption is normally associated with more heat.

How come? No idea, but if anyone knows I'm interested as well.

---

### Post by metalpancake on 2008-03-29
That's wiers, because on my laptop, the system seems to run more efficiently than my dual-boot xp install.

---

### Post by stefangr1 on 2008-03-29
Yes, it's really weird. On my systems (first Athlon single core 3800+, now C2D 2667Mhz) everything runs perfectly cool too. Maybe I should check at his computer if there's some process running that stresses the cpu.

@ mt330404: can you maybe post your cpu usage, and what processes are running when your computer is idle (for example using the "top" command)?

---

### Post by mt330404 on 2008-03-30
> **stefangr1 said:**
> Yes, it's really weird. On my systems (first Athlon single core 3800+, now C2D 2667Mhz) everything runs perfectly cool too. Maybe I should check at his computer if there's some process running that stresses the cpu.

@ mt330404: can you maybe post your cpu usage, and what processes are running when your computer is idle (for example using the "top" command)?

OK Here it is:

mike@mike-laptop:~$ top

top - 14:33:42 up 15:38,  2 users,  load average: 1.22, 1.00, 0.78
Tasks: 124 total,   1 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.4%us,  3.3%sy,  1.0%ni, 81.9%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515140k total,   508764k used,     6376k free,    21252k buffers
Swap:  1510068k total,   217508k used,  1292560k free,   128772k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5298 root      15   0  289m  71m 7852 S  7.7 14.2  15:04.77 Xorg               
10621 mike      15   0  209m  81m  22m S  4.7 16.1  20:11.64 firefox-bin        
 5658 mike      34  19 29020 4416 2472 S  1.7  0.9   0:07.78 trackerd           
10579 mike      17   0 1243m  91m  23m S  1.7 18.3  14:11.20 java               
19767 mike      15   0  132m  28m  18m S  1.0  5.7   0:03.39 evolution          
20252 mike      15   0 62616  18m  10m S  0.7  3.7   0:00.38 gnome-terminal     
 4966 haldaemo  15   0  3264 1172 1068 S  0.3  0.2   0:01.23 hald-addon-stor    
 5628 mike      15   0 19952 6320 4328 S  0.3  1.2   0:45.92 compiz.real        
    1 root      18   0  2952  532  484 S  0.0  0.1   0:01.39 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:14.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0          
   27 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

---

### Post by stefangr1 on 2008-03-31
I indeed find your cpu usage a bit high, does it stay constant like this or was it just a coincidental peak? You already have almost 20% usage when you're doing nothing. 

When I have only firefox open, both firefox and Xorg are using only about 1%. On a somewhat slower processor, that should be more like  2/2%, not 4.7/7.7%. When you had a lot of firefox sessions open, however, 4% processor usage firefox isn't strange.

Maybe you could disable Compiz to see if that helps, or is that not acceptable for you...

---

### Post by shuttleworthwannabe on 2008-03-31
I can second that: compiz for me is a resource hog. and raises tempt by at least 5'C on my notebook. With compiz off (Visual effects=None in Gnome Ubuntu) the system runs cooler; but for the OP, I agree with you about Linux (ubuntu) running warmer than XP on the same hardware. Battery life is also shorter on Ubuntu cf XP.

---

### Post by Daveg4otu on 2008-03-31
This makes sense- everything you do that involves (extra) graphics processing will increase the load on both CPU and GPU....As these work harder they will use more juice and also output more heat into the case(system). As far as  overall performance is concerned - in most systems  the GPU(graphics card) is the bottleneck

---

