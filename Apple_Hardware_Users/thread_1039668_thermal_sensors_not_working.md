---
title: "thermal sensors not working"
date: 2009-01-14
forum: Apple Hardware Users
---

### Post by WinterWeaver on 2009-01-14
Hi there,

I've been using ubunu 8.10 for quite a while now on a macbook 4,1

Recently the macbook seems to be getting quite hot, so I tried to install various sensor tools to measure my cpu temperature. None of them work.

The only one that 'seems' to be working is the sensors-applet. I say 'seems', because firstly, it gives me 3 temperature meters, each measuring a different temperature, but no indication whatsoever, on what temperature each of those are actually measuring.
Also, error notifications is constantly popping up for each meter.

I also tried to measure my temperature in the terminal with: acpi -t
but I get the following:
```
andre@andre-laptop:~$ acpi -t
     Battery 1: charged, 100%
No support for device type: thermal
```Thanks for any help,

WW

---

### Post by pragmatine on 2009-01-14
what sensors does it detect?
Also make sure you've got the applesmc kernel module loaded (from the applesmc-dkms package in the mactel-ppa)

---

### Post by WinterWeaver on 2009-01-15
> **pragmatine said:**
> what sensors does it detect?
Also make sure you've got the applesmc kernel module loaded (from the applesmc-dkms package in the mactel-ppa)

No idea which sensor it detects, as it does not give them any sensible labels. After switching on this morning, the sensors is now showing only 2 O.o ... their labels are: "temp2" and "temp7"

as for the modules you mentioned, you lost me :P ...
If you mean that I should check if the module is active ny doing sudo modprobe applesmc , I've already done that and it didn't make any difference. Unless you mean somthing else.

Thanks,

WW

---

### Post by pragmatine on 2009-01-15
Yeah thats what I meant - its weird that it shows only temp2 and temp7 - it should probably show all the ones in between as well.. can you post the results of an:

```
ls /sys/devices/platform/applesmc*/

and

cat /sys/devices/platform/applesmc*/temp?_input

```

---

### Post by WinterWeaver on 2009-01-15
```
~$ ls /sys/devices/platform/applesmc*/
calibrate    hwmon                     modalias      temp3_input
fan1_input   input                     name          temp4_input
fan1_label   key_at_index              position      temp5_input
fan1_manual  key_at_index_data         power         temp6_input
fan1_max     key_at_index_data_length  subsystem     temp7_input
fan1_min     key_at_index_name         temp10_input  temp8_input
fan1_output  key_at_index_type         temp1_input   temp9_input
fan1_safe    key_count                 temp2_input   uevent
```

and...

```
~$ cat /sys/devices/platform/applesmc*/temp?_input
28250
cat: /sys/devices/platform/applesmc.768/temp2_input: Input/output error
45750
cat: /sys/devices/platform/applesmc.768/temp4_input: Input/output error
45750
cat: /sys/devices/platform/applesmc.768/temp6_input: Input/output error
46750
cat: /sys/devices/platform/applesmc.768/temp8_input: Input/output error
47000

```

---

### Post by pragmatine on 2009-01-15
Right well all the temp sensors are there but it has trouble reading from them - can you confirm whether you are using the applesmc module from the applesmc-dkms package in the mactel-ppa? If not, add the mactel-ppa to your sources.list and then install the applesmc-dkms package and see if that works any better for you, since it has some fixes for making reading from the SMC hardware more reliable

see [here]("https://wiki.ubuntu.com/MactelSupportTeam/PPA") for more info about the mactel-ppa

---

### Post by WinterWeaver on 2009-01-15
> **pragmatine said:**
> Right well all the temp sensors are there but it has trouble reading from them - can you confirm whether you are using the applesmc module from the applesmc-dkms package in the mactel-ppa? If not, add the mactel-ppa to your sources.list and then install the applesmc-dkms package and see if that works any better for you, since it has some fixes for making reading from the SMC hardware more reliable

see [here]("https://wiki.ubuntu.com/MactelSupportTeam/PPA") for more info about the mactel-ppa

Thanks, this is the first that I have seen about mactel-ppa. should I remove the current smc first, before installing the mactel stuff? or will it automatically update smc based on the new repository?

Also, since I'm on hardy, would it be ok to add the Interpid repo for this package, as mentioned in that link?

---

### Post by cyberdork33 on 2009-01-15
> **WinterWeaver said:**
> Thanks, this is the first that I have seen about mactel-ppa. should I remove the current smc first, before installing the mactel stuff? or will it automatically update smc based on the new repository?

Also, since I'm on hardy, would it be ok to add the Interpid repo for this package, as mentioned in that link?
It should update your current applesmc module, but I don't think it will work on Hardy. Most of the work on the applesmc package was done with the kernel in Intrepid.

---

### Post by pragmatine on 2009-01-15
I would suggest installing Intrepid as it will have much better support for your macbook, then add the mactel-ppa and install the applesmc-dkms package (as well as the others which are applicable to your machine listed on the wiki page I linked to before)

---

### Post by WinterWeaver on 2009-01-16
Ok, thanks guys.

To be honest I was considering installing interpid, but I've got so much important work here, and in a middle of a big web project, so I was afraid to risk it just now.

At least I have my home folder on a separate partition :).

thx for the help.

I'll mark this thread as resolved.

EDIT: erm... am I just dumb or blind... I cannot find the link to resolve the thread... O.o

---

### Post by alexmurray on 2009-01-16
Just change the title and add [SOLVED] at the start of it

---

### Post by cyberdork33 on 2009-01-16
> **alexmurray said:**
> Just change the title and add [SOLVED] at the start of it
You cannot edit the thread title in this forum.

Some forum features were disabled as the admins are working on some issues. The thanks system is also turned off. The ability to mark threads as solved should be back in the future.

---

### Post by WinterWeaver on 2009-01-17
ok, I finished the Interpid Install and I have to say I'm very happy. In hardy I had many issues setting up everything, isight didn't work, brightness keys never worked no matte what I tried etc.

All of those works beautifully now, and wasn't even hard to set up.

Also, it seems that the thermal stuff is working now:
```
andre@andre-laptop:~$ acpi -V
     Battery 0: Full, 96%
  AC Adapter 0: on-line
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10
```

Unfortunately the sensors applets I tried is not working :(
Which ones do you guys suggest I try install?

WW

---

### Post by WinterWeaver on 2009-01-17
Ok, sensors are finally working.

quick output:
```
andre@andre-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +51.0°C  (high = +100.0°C, crit = +100.0°C)
```

isn't that a bit hight? The sensors are showing anything from 50 and up as red.

---

### Post by alexmurray on 2009-01-17
Nah, not too high - when I wrote sensors-applet I added some default values for high and low for temp sensors which were based on the desktop machine I used at the time which idled at about 30C, so to me at the time 50C or so seemed high - now I have a MBP5,1 the temp sensors idle at about 55C so its always in the red - you can change the limits by editing the sensor preferences, and you can change the colour of the graph if you use that too.

Try adding the mactel-ppa to your sources.list now and installing applesmc-dkms package then loading the applesmc module - then you should get readings for 8 or so more sensors too.

---

### Post by cyberdork33 on 2009-01-17
yea, in OSX, my temps get that high all the time on a Macbook Pro 4,1

---

### Post by WinterWeaver on 2009-01-17
> **alexmurray said:**
> Try adding the mactel-ppa to your sources.list now and installing applesmc-dkms package then loading the applesmc module - then you should get readings for 8 or so more sensors too.

how do I lode the module to get the extra sensors? I already have applesmc-dkms installed.

thx :)

---

### Post by alexmurray on 2009-01-17
open up a terminal and type:

sudo modprobe applesmc

---

### Post by cyberdork33 on 2009-01-17
> **alexmurray said:**
> open up a terminal and type:

sudo modprobe applesmc
and add "applesmc" to /etc/modules to have it load automatically on boot from now on.

---

### Post by WinterWeaver on 2009-01-18
AHA! Thanks guys! hehe, now I can finally see my fan speed as well :)

Now I can surely mark the thread as solved, if only the forum team put the feature back soon :P

---

