---
title: "iMac 24&quot; running hot"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by pam258 on 2008-05-14
Hey, my iMac 24-inch 2.4GHz 1 gb RAM seems to be getting much hotter than usual while using Hardy.  I cant tell you the temp because I haven't found a proper utility to measure the temp (most say they can't detect temp sensors).  I can tell just by feeling the top/back of the computer where the vents are.  Is anyone else having this problem?

---

### Post by cyberdork33 on 2008-05-14
> **pam258 said:**
> Hey, my iMac 24-inch 2.4GHz 1 gb RAM seems to be getting much hotter than usual while using Hardy.  I cant tell you the temp because I haven't found a proper utility to measure the temp (most say they can't detect temp sensors).  I can tell just by feeling the top/back of the computer where the vents are.  Is anyone else having this problem?
everyone with a mac complains that it runs hot. My iMac seems to hot a bit hotter in Ubuntu than in OSX, but I have not had any issues.

---

### Post by pveith on 2008-05-15
Just open a console and do a ```
lsmod|grep apple
```
this should return a line, which contains "applesmc", if not there are two things.
Try loading the "applesmc" module. ```
modprobe applesmc
``` and see if the first command returns the line now. If not, this post won't help you, Sorry.

If the applesmc line appears:
change to directory /sys/devices/platform/applesmc.768/ in command line. There should be Information on fan-speed and temperature there. If you enter (in this directory) ```
sudo echo "3000" > fan1_min
```, your system should stay cooler. The preset min is just a little bit too low.
If this works you can sudo edit /etc/rc.local and add a line like "echo "3000" > /sys/devices/platform/applesmc.768/fan1_min" there.
Hope that helps...

---

### Post by oli1978 on 2008-05-17
> **pveith said:**
> Just open a console and do a ```
lsmod|grep apple
```
this should return a line, which contains "applesmc", if not there are two things.
Try loading the "applesmc" module. ```
modprobe applesmc
``` and see if the first command returns the line now. If not, this post won't help you, Sorry.

If the applesmc line appears:
change to directory /sys/devices/platform/applesmc.768/ in command line. There should be Information on fan-speed and temperature there. If you enter (in this directory) ```
sudo echo "3000" > fan1_min
```, your system should stay cooler. The preset min is just a little bit too low.
If this works you can sudo edit /etc/rc.local and add a line like "echo "3000" > /sys/devices/platform/applesmc.768/fan1_min" there.
Hope that helps...

Hi pveith,

I already tried this solution, however, this [topic]("http://ubuntuforums.org/showthread.php?t=794425&highlight=imac+fan") shows the result. Do you know where does this problem comes from ?

Regards

---

### Post by stream303 on 2008-05-17
I'm running the PPC architecture, but found that Hardy was the first one that didn't do cpu frequency scaling properly with powernowd, so my iMac was always running full-steam ahead - I had to change my scaler to cpudyn.

We're on totally different machines, but wonder how cpu frequency scaling is working for the Intel Macs with hardy...

---

### Post by oli1978 on 2008-05-17
> **stream303 said:**
> I'm running the PPC architecture, but found that Hardy was the first one that didn't do cpu frequency scaling properly with powernowd, so my iMac was always running full-steam ahead - I had to change my scaler to cpudyn.

We're on totally different machines, but wonder how cpu frequency scaling is working for the Intel Macs with hardy...
Hi,

I am also having an iMac. Can you tell me more about powernowd and cpudyn ? You said you changed your scaler, but, how did you do that ?
Note that however my temperature problem comes from the HDD (55-60°C), and not from the CPUs (35°C) ...

Regards

---

### Post by stream303 on 2008-05-17
I just used synaptic to search for powernowd, uninstalled it, and then searched for cpudyn and installed that.  Scaling took effect pretty quickly.  I just added a frequency-scaling monitoring applet in the top bar to keep an eye on it and verify that I had a problem in the first place. :)

Or if you think the system is settled, cat /proc/cpuinfo

This scaling issue only showed up on my PPC iMac, and not any other boxes..

---

### Post by Cows on 2008-05-17
I have a 20" Intel Mac and I was wondering if you fixed your problem ?

---

### Post by cyberdork33 on 2008-05-17
I think that the applesmc module only works on portables anyway.... (Macbook, Macbook Pro, Macbook Air) I get the same error when trying to load applesmc on my iMac. I have never had to change the fan speed though. It runs just fine without.

---

### Post by Cows on 2008-05-17
So I shouldn't worry about the heat ?

---

### Post by cyberdork33 on 2008-05-17
> **Cows said:**
> So I shouldn't worry about the heat ?
Like I said, I have been doing this for the last few Ubuntu releases on my iMac and have never had a problem from the heat. If you Mac starts randomly shutting down because it gets too hot then you might have cause for concern, but if it operates fine there is no issue.

---

### Post by Cows on 2008-05-17
Alright thanks :).

---

### Post by oli1978 on 2008-05-18
> **cyberdork33 said:**
> I think that the applesmc module only works on portables anyway.... (Macbook, Macbook Pro, Macbook Air) I get the same error when trying to load applesmc on my iMac. I have never had to change the fan speed though. It runs just fine without.

Hi,

I think, you are right. However, on OSX, I can set the fan speed for my HDD at the speed I want using smcFanControl. So, it is possible to decide the fan speed. Why isn't it possible with ubuntu ? 60°C is really, really to hot ... As you are in the MacTel support list, maybe you know how we can do it, or patch the kernel.

---

### Post by cyberdork33 on 2008-05-18
> **oli1978 said:**
> Hi,

I think, you are right. However, on OSX, I can set the fan speed for my HDD at the speed I want using smcFanControl. So, it is possible to decide the fan speed. Why isn't it possible with ubuntu ? 60°C is really, really to hot ... As you are in the MacTel support list, maybe you know how we can do it, or patch the kernel.I am sure there is a way to do it, but I have no idea. coretemp reports < 35C when basically idling for me and says that 100C is critical.

---

### Post by oli1978 on 2008-05-18
> **cyberdork33 said:**
> I am sure there is a way to do it, but I have no idea. coretemp reports < 35C when basically idling for me and says that 100C is critical.

OK. For me, coretemp is to at 35°C when idling. But HDD stills at 60°C ....

---

### Post by cyberdork33 on 2008-05-18
> **oli1978 said:**
> OK. For me, coretemp is to at 35°C when idling. But HDD stills at 60°C ....
what are you using to check the HDD temp? I noticed that the drive runs pretty hot. It does have a temperature sensor attached to the outside of it in my iMac which leads me to believe that some fan speeed relies on it's temp to operate.

---

### Post by oli1978 on 2008-05-18
> **cyberdork33 said:**
> what are you using to check the HDD temp? I noticed that the drive runs pretty hot. It does have a temperature sensor attached to the outside of it in my iMac which leads me to believe that some fan speeed relies on it's temp to operate.

I use hddtemp (you can get it with synaptic). And, I use lm-sensors (also with synaptic) to get CPUs speeds (it is a widget). However, I never hear my fan, which makes me think that there is a problem ...

And you, what is the temperature of your hdd ?

---

### Post by cyberdork33 on 2008-05-18
> **oli1978 said:**
> I use hddtemp (you can get it with synaptic). And, I use lm-sensors (also with synaptic) to get CPUs speeds (it is a widget). However, I never hear my fan, which makes me think that there is a problem ...

And you, what is the temperature of your hdd ?
It's nly about 41C right now, but I haven't been using it at all. 

I never hear my fans either.

---

### Post by oli1978 on 2008-05-18
> **cyberdork33 said:**
> It's nly about 41C right now, but I haven't been using it at all. 

I never hear my fans either.

OK. Mine starts after boot at 35°C and slowly goes to 55°C-60°C after an hour.

PS : I suscribed to the MacTel Support Team. I am experienced in C++ dev and, maybe I could help !

---

### Post by cyberdork33 on 2008-05-18
> **oli1978 said:**
> I suscribed to the MacTel Support Team. I am experienced in C++ dev and, maybe I could help !
OK. I will approve you. If you haven't made debian binaries before, you might want to have a look at some of the tutorials...

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

and how to access your personal and the team's ppa:
[https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)

People are using the Mactel-support ppa, so testing and such should be done with your personal ppa, and uploaded to the team ppa when a degree of certainty that the package is good for use has been reached.

---

### Post by Brightbelt on 2008-05-19
Hi, Since Cyber suggested some of the earlier code in this thread might apply to laptops, I tried this fix by Pveith for my Macbook Air:

```
lsmod|grep apple

this should return a line, which contains "applesmc", if not there are two things.
Try loading the "applesmc" module.
Code:

modprobe applesmc

and see if the first command returns the line now. If not, this post won't help you, Sorry.

If the applesmc line appears:
change to directory /sys/devices/platform/applesmc.768/ in command line. There should be Information on fan-speed and temperature there. If you enter (in this directory)
Code:

sudo echo "3000" > fan1_min

, your system should stay cooler. The preset min is just a little bit too low.
If this works you can sudo edit /etc/rc.local and add a line like "echo "3000" > /sys/devices/platform/applesmc.768/fan1_min" there.
Hope that helps...
Last edited by pveith; 4 Days Ago at 10:17 AM.
``` 

My Macbook Air seems to HAVE the applesmc module which leads me to believe his fix should work. But when I finally got towards the end and entered 
```
sudo echo "3000" > fanl_min
```
I got 'Permission Denied' among other things I didn't understand. And the permission denied surprised me because sudo is in the code.

I also see a possible typo in his last part: 
```
If this works you can sudo edit /etc/rc.local and add a line like "echo "3000" > /sys/devices/platform/applesmc.768/fan1_min" there.
```
I think that should be 'sudo gedit /etc/rc.local' (gedit, not 'edit')

So I am trying the second part, but I have to see whether it works or not... I appreciate any help or suggestions,...Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-19
> **Brightbelt said:**
> But when I finally got towards the end and entered 
```
sudo echo "3000" > fanl_min
```I got 'Permission Denied' among other things I didn't understand. And the permission denied surprised me because sudo is in the code.
The reason is because of the format of the command. you are using the echo command with sudo (which actually isn't needed) but the output of the command is being piped to fan1_min a virtual file interface to your hardware which has limited permissions. (i.e. there are actually two commands... and sudo is applied only to the first). using 'tee' is suggested to remedy this. See this thread:
[http://ubuntuforums.org/showthread.php?t=412329](http://ubuntuforums.org/showthread.php?t=412329)

---

### Post by Brightbelt on 2008-05-19
So, Cyber, to be specific, would the line be this?

```
echo 6 | sudo tee "3000" > fanl_min
```

---

### Post by cyberdork33 on 2008-05-19
```
echo "3000" |tee -a /sys/devices/platform/applesmc.768/fan1_min
```There is also a post on this in the FAQ, and you might find this interesting as well:
[https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

---

### Post by Brightbelt on 2008-05-19
Many Thanks Cyber. That'll be nice to try once I get my mouse back. ...Frank B.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> Many Thanks Cyber. That'll be nice to try once I get my mouse back. ...Frank B.
See other thread ;)

---

### Post by Brightbelt on 2008-05-20
Hi Cyber,
I tried your line:

```
echo "3000" |tee -a/sys/devices/platform/applesmc.768/fan1_min
```
And remember I'm supposed to be in this directory:
```
change to directory /sys/devices/platform/applesmc.768/
```
So, when I implement your code at the above directory, I get a message that says:
```
tee: invalid option --/
```
So who knows what's up here. I appreciate any guidance on this. Seeing as how I do have the applesmc on my Macbook Air, this code, if it can work, would really help out.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-20
Also, to be more on point for this topic, I've been rebooting back & forth lately on my 24" iMac and checking the heat just by feel, between the 2 OS.

I'm starting to conclude that the iMac may be running just as hot on the Mac OS X side as it is with Ubuntu. If there is any difference, it is VERY, VERY slight. 

OR, the Mac side is not offering any benefit of cooling for the computer after having run Ubuntu. 

I might get different results if I let the machine cool off and run only Mac OS X.

I'll try that next,...Frank B.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> I get a message that says:
```
tee: invalid option --/
```

Sorry, I made a typo. There should be a space between -a and the rest. I will edit my post. and with my command, you don't have to be in the directory.

> **Brightbelt said:**
> Also, to be more on point for this topic, I've been rebooting back & forth lately on my 24" iMac and checking the heat just by feel, between the 2 OS.

I'm starting to conclude that the iMac may be running just as hot on the Mac OS X side as it is with Ubuntu. If there is any difference, it is VERY, VERY slight.

I'd say that is pretty much the case for me too. I have had the fans spin up high for a minute before, but that has happened in OSX too.

---

### Post by Brightbelt on 2008-05-20
Hi Cyber,
Wow this code has a thorn in it or something. I tried it, both in the stated directory and without (as you said it wasn't really necessary).

Both times, I got "No such file or directory"...

So I guess something else is going on; I DID make the change with the -a part so that there is a space on both sides of it.

Many Thanks For your assistance, Frank B.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> Hi Cyber,
Wow this code has a thorn in it or something. I tried it, both in the stated directory and without (as you said it wasn't really necessary).

Both times, I got "No such file or directory"...

So I guess something else is going on; I DID make the change with the -a part so that there is a space on both sides of it.

Many Thanks For your assistance, Frank B.

If you navigate to /sys/devices/platform/applesmc.768/ and do 'ls' is there a file named that (fan1_min)?

PS might need to be sure that applesmc is loaded before trying too.

EDIT, I was looking through some emails and it looks like the applesmc module may not work with the MBA yet.
[http://sourceforge.net/mailarchive/forum.php?thread_name=aea46f8f0805010652k34a67eb3k2eb5578965492800%40mail.gmail.com&forum_name=mactel-linux-users](http://sourceforge.net/mailarchive/forum.php?thread_name=aea46f8f0805010652k34a67eb3k2eb5578965492800%40mail.gmail.com&forum_name=mactel-linux-users)

---

### Post by Brightbelt on 2008-05-20
Hi Cyber, Thanks for following through. Here's what I got from the 'ls' at that directory:

```
brightbelt@brightbelt-laptop:/sys/devices/platform/applesmc.768$ ls
calibrate                 key_at_index_name  subsystem     temp6_input
driver                    key_at_index_type  temp10_input  temp7_input
hwmon                     key_count          temp1_input   temp8_input
input                     modalias           temp2_input   temp9_input
key_at_index              name               temp3_input   uevent
key_at_index_data         position           temp4_input
key_at_index_data_length  power              temp5_input

```

So it looks like you are correct. I just hope my Macbook Air doesn't burst into flames !! :lolflag:

Seriously, it seems to be ok. This laptop would have an automatic shutdown mechanism if it got too hot, right? I guess the real question is: If it does have that, would it work in Ubuntu?

Again, Many Thanks for your following through.
Frank B.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> Seriously, it seems to be ok. This laptop would have an automatic shutdown mechanism if it got too hot, right? I guess the real question is: If it does have that, would it work in Ubuntu?If you really need to monitor the temp, you can use coretemp.

---

