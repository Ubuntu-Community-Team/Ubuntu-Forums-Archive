---
title: "cpu fan not spinning"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by neuraljay on 2007-12-17
hi everyone. I am definitely a new user to Ubuntu. Been using windows for so long now. But this OS really fascinates me that I would let go of Windows. I am using a HP/Compaq V3000S, bought last year. A month ago, I installed the ubuntu 7.10, dual boot with XP(used for my programming job). Little by little, I was able to setup Ubuntu to work with my Java based frameworks however, I've noticed that my cpu fan is not spinning at all. No hot air is coming out from the back like the normal way when I am using windows. When i boot back up to Windows, you will noticed how hot my cpu was because the fan starts to fire up  giving a hot air.. Which actually bothers me since it may definitely damaged my centrino duo processor and slows my system. . Can everyone help me out with this or there's no fix yet.

Thanks alot..

---

### Post by mondy on 2007-12-17
is your cpu fan dirty orif not replace it

---

### Post by alphaniner on 2007-12-17
Let me see if I understand.  Your CPU fan works when you are running windows, but not when you are running Ubuntu?  The only thing I can think of is maybe you have some kind of 'intelligent' fan control on your motherboard which Ubuntu is somehow interfering with.  I would check the documentation on your motherboard/BIOS and see if this is the case.  And if so, turn it off.  This is just an off the cuff suggestion, because I can't imagine that the OS should be able to affect such a thing, but it is worth a try if you are comfortable in your BIOS.

---

### Post by neuraljay on 2007-12-18
> **alphaniner said:**
> Let me see if I understand.  Your CPU fan works when you are running windows, but not when you are running Ubuntu?  The only thing I can think of is maybe you have some kind of 'intelligent' fan control on your motherboard which Ubuntu is somehow interfering with.  I would check the documentation on your motherboard/BIOS and see if this is the case.  And if so, turn it off.  This is just an off the cuff suggestion, because I can't imagine that the OS should be able to affect such a thing, but it is worth a try if you are comfortable in your BIOS.

Yes. If I am running windows, my cpu fan works just fine. But when running ubuntu, it does not spin. I've checked on the BIOS configuration and there is no option to configure cpu fans. I am using T2400 1830mhz. You will notice that upon windows log on screen, you can feel that there is air coming out from the back instantly but with ubuntu login, nothing. 


thanks lots

---

### Post by neuraljay on 2007-12-18
or simply because Compaq v3047TU does not support Linux OS. But I am guessing, the compatibility of the mobo and cpu should be just fine

---

### Post by cyrusrayne on 2007-12-18
Unusual issue.  I think I'll have to look at this one.  It could possibly be the way Ubuntu handles power on the bus that's causing the CPU fan to not spin, seeing as the OS wouldn't need significant resources to switch it on or off.

---

### Post by neuraljay on 2007-12-18
or would it be possible that Linux does not really eats alot of resources that heats up the cpu so fast causing the fan not spin until needed? 

however, what's bothering me though that the hdd part of the laptop is already at least a bit hot then still at the back, fan is still off. 

Okay new discovery, the air coming out is not that strong. But in windows, it really is noticeable? is that normal?

thanks

---

### Post by neuraljay on 2007-12-18
then another thing I've noticed was when you are scrolling a page then it reached the end of file and you keep pressing let say the down arrow key, the lcd blinks.. like if the brightness is set to lowest or whatever, and example a terminal window is open , when you press the down arrow key, the lcd becomes dark in a split second.. is that normal??

---

### Post by neuraljay on 2007-12-18
not again.. let me clarify myself everyone to what really is happening..

during the boot process of ubuntu, the fan is still spinning. Then right after the log on screen comes up, it stops. you can't hear anything. There's the problem... Scary right???

---

### Post by zakirs on 2007-12-18
> **neuraljay said:**
> or simply because Compaq v3047TU does not support Linux OS. But I am guessing, the compatibility of the mobo and cpu should be just fine

i dont think its an v3000 issue since mine is an v3239 and my fan works

---

### Post by neuraljay on 2007-12-18
i am really anxious to know what's causing the problem. I've already reinstalled ubuntu many times and still getting the same problem. including my boss dell inspiron 9300.. Ubuntu 7.10

---

### Post by niteshifter on 2007-12-18
> or would it be possible that Linux does not really eats alot of resources that heats up the cpu so fast causing the fan not spin until needed?


Yes it's possible. Depends on CPU and BIOS (specifically the power management) for the most part. Intel CPU's that have SpeedStep can be throttled up and down in speed, some AMD processors can do this also.

I dual boot. In Ubuntu my fan seldom runs, it comes on only during sustained CPU-intensive activies. When I boot XP it comes on after a few minutes and pretty much stays on. The difference being in Ubuntu I stay at 600MHz and I can see it bump up and then down in response to loading. In XP it stays at 1.4GHz.

You can check the temperature of your CPU. Start a Terminal and type
```
cat /proc/acpi/thermal_zone/THM/temperature
```

If that gets you nothing (or an error message) you may need to install the sensors application:
```
sudo apt-get install lm-sensors
```

If you're running GNOME (standard Ubuntu) you can install a panel applet so as to monitor it while you work:
```
sudo apt-get install sensors-applet
```
(You can also install these via Synaptic Package Manager if you wish, just search for "sensors")

Once the sensors-applet is installed, right-click on the panel you want it on, click "Add to Panel". A dialog appears, the sensor-applet is named "CPU Frequency Scaling Monitor" , click on it to select it, then click the Add button, then the Close button. An icon that looks like a thermometer will be on the panel, the CPU temp beside it.

Now that leaves the question: What's to hot? That's not so easy to answer as different hardware (laptop / destop / server chassis) all have very different thermal characteristics. IIRC somewhere around 100C is considerd the cut-off point for most. If what you see is below 80C you're OK.

HTH

---

### Post by Presto123 on 2007-12-18
Odd...I just realized that mine isn't either.

It's not running hot though...I have never really paid attention to this before.

**Edit**Just ran PI with a high number to utilize everything and heard that little thing fire up, so never mind.

---

### Post by neuraljay on 2007-12-18
niteshifter thanks for those information. I will try them. 

HOT? yes, once I'm done doing my programming stuff in linux and booted back to windows, the fan fires up and you can feel that the air coming out is really hot. lat say about 60-70F. That if your put your laptop in your lap, you won't stand the heat..Which concerns me that even though linux is not using much of the system resources compares to windows, one way or the other, the hot air coming our when windows loads is something to pay attention to..

---

### Post by neuraljay on 2007-12-18
> **niteshifter said:**
> Yes it's possible. Depends on CPU and BIOS (specifically the power management) for the most part. Intel CPU's that have SpeedStep can be throttled up and down in speed, some AMD processors can do this also.

I dual boot. In Ubuntu my fan seldom runs, it comes on only during sustained CPU-intensive activies. When I boot XP it comes on after a few minutes and pretty much stays on. The difference being in Ubuntu I stay at 600MHz and I can see it bump up and then down in response to loading. In XP it stays at 1.4GHz.

You can check the temperature of your CPU. Start a Terminal and type
```
cat /proc/acpi/thermal_zone/THM/temperature
```

If that gets you nothing (or an error message) you may need to install the sensors application:
```
sudo apt-get install lm-sensors
```

If you're running GNOME (standard Ubuntu) you can install a panel applet so as to monitor it while you work:
```
sudo apt-get install sensors-applet
```
(You can also install these via Synaptic Package Manager if you wish, just search for "sensors")

Once the sensors-applet is installed, right-click on the panel you want it on, click "Add to Panel". A dialog appears, the sensor-applet is named "CPU Frequency Scaling Monitor" , click on it to select it, then click the Add button, then the Close button. An icon that looks like a thermometer will be on the panel, the CPU temp beside it.

Now that leaves the question: What's to hot? That's not so easy to answer as different hardware (laptop / destop / server chassis) all have very different thermal characteristics. IIRC somewhere around 100C is considerd the cut-off point for most. If what you see is below 80C you're OK.

HTH

hi again. how will I run the lm sensors? because after installing it, then in the jay@jay-laptop$ i entered lm-sensors and got an error *this script must be run in root*, then when I tried it i am not getting *try sensor-detect*..

---

### Post by Phosphoric on 2007-12-18
I had the same issue, different motherboard, but it was a setting in the BIOS.  The CPU fan would spin during bootup but stop when Ubuntu was loaded completeley.

Turned fan speed control off in the BIOS and now my CPU fan runs 100% all the time.

This can be a bit noisy so I stuck a 100 ohm variable resistor in the 12V supply to the fan and turned the volyage down to about 9V.  Now runs at areasonably quiet speed and the CPU temp is OK.

I'd check the BOIS settings again.

---

### Post by -error on 2007-12-18
people! why you're bothering about fan not spinning. it's great, because it lowers overall noise. just keep an eye on cpu temerature and if it is ok - sleep with no worry.
weird. everybody should be concerned about fan that spins constantly at high RPM. that is the real trouble.

---

### Post by niteshifter on 2007-12-18
@neuraljay: Sorry, should have put that out there. To get lm-sensors readings:
```
sudo sensors
```

Caveat: With some hardware lm-sensors doesn't work, or report completely and getting it to work requires detailed knowledge of the hardware and editing lm-sensors config file. It doesn't work at all on my two Dells laptops, does work mostly with the one Dell desktop, I am hoping that HP (with a history of being Linux / Unix friendly) it will work for you.

What happened when you did:
```
cat /proc/acpi/thermal_zone/THM/temperature
```

 ??? ACPI reporting should be there regardless of lm-sensors.

---

### Post by zakirs on 2007-12-19
well i too own a compaq v3000 and my temp always hovers  around  65 deg but yeah i find that its hotterwhen usuallly compared with vista , seems that a problem with fans speed...coz i can hear fan running but not as loud as in vista ...may be some experienced user can throw some light on this  :(

---

### Post by zakirs on 2007-12-19
or is it a problem with kernel coz my laptop is even heating up with puppy linux

---

### Post by GSF1200S on 2007-12-27
This is bugging me too. My problem is a little different.

My fan stays off most the time, but then my processor cores idle at like 1-2%. If I boot up CNC3 under Wine and core 2 goes up to 100%, my fan comes on with force reliably. The lappie never seems to get super hot, unless im playing a game (the fan is going though). The problem is, cpu frequency scaling isnt supported. cat /proc/cpuinfo shows that my processor is at 2.16Ghz at all times, with no scaling options. To make matters worse, I cant access the cpu temp sensor either, so I dont know how hot my CPU is getting. Ive been running a variant of Ubuntu now for almost 9 months on this lappie/cpu, so it couldnt be doing too much damage. I would think running 2.16ghz with no stepping wouldnt be good for the cpu

My nvidia GPU reports its temp, which may go up to 80 (112 is core slowdown). I have a feeling im dealing with acpi support issues- of course I have the boon of my existence as a bios: Phoenix Bios. Apparantly not only does it give you 0 options at the bios screen, but it wont give linux any either... Any ideas? Sorry to hijack OP- were all suffering acpi issues here...

---

### Post by Romin-1 on 2007-12-27
Could it be that when you log into Ubuntu that you are essentially telling Win dosen't that the machine is going to sleep and it shuts the fan off to save battery.

Just a thought.

Jon

---

### Post by spydon on 2008-03-03
> **Romin-1 said:**
> Could it be that when you log into Ubuntu that you are essentially telling Win dosen't that the machine is going to sleep and it shuts the fan off to save battery.

Just a thought.

Jon

Hmm, that sounds unlikely.
BIOS will probably give the fan a wake up signal before Ubuntu can control it.

---

