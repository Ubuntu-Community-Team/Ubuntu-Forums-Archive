---
title: "Hope this isn't heading to where I think it is...."
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by iceman16us on 2007-04-15
Hello Ubuntu Community,

Since this is my first post, I figured I would start out with a quick introduction.  I've been using ubuntu for about 4 months now and I have to say I'm very pleased with how its worked for me.  I had trouble my first time installing edgy since it refused to work with my wireless card (broadcom......ugh).  I then switched to dapper and used it until about a week ago when I installed the feisty beta.

Well onto the problem. Before installing feisty I was beginning to have trouble with dapper every once in a while.  Sometimes the cpu usage would go up to 100% with nothing open but the desktop.  When I would try to restart, it would take about 7 - 8 minutes to start up and even after starting up it would still have the same problem with the cpu usage.  The only solution I could find was to shut down the computer and leave it off for about 10 minutes and then everything was fine again.

Once I read that feisty was a little easier with the broadcom than edgy I decided to give it a try and hope it would solve my cpu usage problem I had in dapper.  Everything seemed to work fine for the first day then the cpu spiked to 100% and I decided to restart the computer and same old story.    Now in the last couple of days, I have had a few random shutdowns.  I will just be browsing the web and the computer just shut down.  This led me to believe that it may be a hard drive problem.

I searched the forums and found something about an iso you could burn and boot from to check your hard drive to see if it might be going down the toilet.  But unfortunately I have lost the  link and cannot find the thread it was listed in now.  My question is that if I am probably correct in my assumption that my hard drive is about to kick the bucket and also if there is any way I can check to see if this is the problem.  

Sorry for the essay and vague description of the problem.
Thanks in advance for any suggestions!!

---

### Post by speeves on 2007-04-15
Here is a good link that should get you started towards troubleshooting your problems:
[http://www-128.ibm.com/developerworks/library/l-hw1/](http://www-128.ibm.com/developerworks/library/l-hw1/)

Good luck!

---

### Post by bodhi.zazen on 2007-04-15
Hmm ...

Does not sound like a HD problem to me, but that is just me ...  Usually hd problems will give you error messages at boot time or the filesystem will be mounted ro.

My guess is your CPU is too hot. You might be able to check this in your BIOS (hit F2 or what have you to boot to bios).

---

### Post by nautilus on 2007-04-15
next time your CPU spikes to 100%, open a terminal and type: top

if you can't do this, let's talk more, but it sounds like a simple rogue process.

i wouldn't worry about your hard disc too much at this point, those symptoms don't seem to match up.

if your hard disc dies, programs will simply stop responding after doing something, but other programs will run along nicely until they need to access the disc, then they freeze too... etc.

i know this because recently a 30-day old SATA2 drive died on me, this is what happened.

in the event of bad sectors, spiking cpu makes as much sense as a bad cough being related to a stubbed toe...

in any case, if you could try running top, and seeing which one is eating up all your cycles, that would severely help narrowing down the problem.

---

### Post by iceman16us on 2007-04-15
Thanks for the replies.  I will try the suggestions at that link.  

It's odd that you mention cpu temperature.   Before installing ubuntu and while still in windows, I bought a very cheap fan for the laptop because it got so hot it would hurt your lap to set it on it.  The fan seems to do a pretty good job at keeping it at a decent temperature but I have still experienced the cpu spike with the fan.  I downloaded the grellm program that the first link suggested and I will use that to monitor the cpu temp.

The only reason I suspected a hard disk problem was the random shutdowns.  I had always thought random shutdowns to be almost a sure sign of a hardware problem.  The next time the cpu does spike, i will post the results of top and my cpu temperature at the time.  Thanks for all the suggestions so far.

---

### Post by ayenack on 2007-04-16
Have you installed BOINC by any chance? This app can play havoc with the load on your cpu especially when browsing the web.

Best of luck. ayenack.

P.S. It's not a good idea to put your laptop directly onto your lap. Your processor is emitting microwaves all the time these can cook your legs or other important parts. ;o

---

### Post by Titus A Duxass on 2007-04-16
> Your processor is emitting microwaves all the time these can cook your legs or other important parts. ;o - Sorry, but that is total rubbish! It's a micro-processor not a microwave emitter. The only danger is in getting your nuts too hot, that's not good for the sperm count.

---

### Post by Famicommie on 2007-04-16
It sounds to me like a processor issue, as well. Leave it off for several hours, then turn it on and go into the BIOS. You should be able to check your CPU temperature from there. Make a note of it. Then, use the laptop as normal until it shuts down again. Boot it up and check on the processor temp. If that's causing the problem, try putting some thermal gel on the processor itself.

---

### Post by RudolfMDLT on 2007-04-16
> **bodhi.zazen said:**
> Hmm ...
My guess is your CPU is too hot. You might be able to check this in your BIOS (hit F2 or what have you to boot to bios).

Definitely - If I where you, have the CPU fan checked out. You'll be crying be long tears if a $1 fan burns a $200 cpu.

---

### Post by ayenack on 2007-04-16
> Sorry, but that is total rubbish! It's a micro-processor not a microwave emitter. The only danger is in getting your nuts too hot, that's not good for the sperm count.


This is not total rubbish. 

When micro processors started running at 2Ghz (I thing it was) and above they also started releasing certain amounts of microwaves and will continue to do so as they increase in speed. 

WIFI Adapters and many other devices also emit microwaves. It's to do with the frequency they use. This is how microwave ovens work they emit waves at a certain frequency which vibrates the food causing friction thus heating it causing it to cook. There is of course the ever ongoing issue with mobile phones releasing microwave radiation and whether this causes damage to the brain. Have you noticed when you use a mobile for a certain amount of time that your ear will start to get hot yet the phone is still cool to the touch? Well that's a case in point.

That's why Laptop processors are shielded. But the shielding is not always adequate.

An interesting and slightly sick experiment is to put a fly in a microwave oven and turn it on. The fly will happily fly around with no ill effects. It's effectively flying between the microwaves because it is to small to continuously be vibrated and thus heated.

Best of luck. ayenack.

---

### Post by justleen on 2007-04-16
the loads of ******** part is the bit where he claims that those microwaves are harmfull.. they arent...

On topic: i'd suspect the CPU temp as well.. I had heat problems before, and the symptoms you are expiernce sound awfully familair..
If you installed a new fan, i'd remount id, and make sure theres not grains (old cooling paste, for example) in between the fan and the cpu...

---

### Post by konungursvia on 2007-04-16
To be exact, food microwaves emit at a frequency that exactly equals the difference between two quantum states of the water molecule's rotational energy, which causes water molecules to spin faster. After a few moments, collisions cause this rotational energy to be converted to regular translational kinetic energy (heat as we know it). It's not that likely that a microprocessor or a wi-fi card would emit at that frequency.

---

### Post by ayenack on 2007-04-16
> To be exact, food microwaves emit at a frequency that exactly equals the difference between two quantum states of the water molecule's rotational energy, which causes water molecules to spin faster. After a few moments, collisions cause this rotational energy to be converted to regular translational kinetic energy (heat as we know it). 

I believe this is adequately summed up as friction.

Best of luck. ayenack.

And they do.

---

### Post by ayenack on 2007-04-16
> the loads of ******** part is the bit where he claims that those microwaves are harmfull.. they arent..

These waves can be harmful.

Best of luck. ayenack.

---

### Post by ayenack on 2007-04-16
On topic.

It might be an idea to install a mother board sensor app (LMSensor). Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) it has instructions on how to do this. This will give you info on cpu, hard drive, and other components.

Best of luck. ayenack.

---

### Post by iceman16us on 2007-04-16
Well, just had it happen again to me about 5 minutes ago.  Running top showed the cpu usage being split 55% to firefox, 30% to Xorg and the rest was spread out.  Listening to the suggestions about temperature i turn my computer upside down to look at the fans and sure enough one of them isn't even spinning.  So looks like I have found the culprit.  Makes you feel a little dumb for not noticing something as simple as that haha. But oh well.   

Thanks for all the help!!

---

### Post by ayenack on 2007-04-16
The fans on laptops don't always spin. They will often turn themselves off for a time. You should have an option in your laptops BIOS to configure the thermal mode. If so change it to performance this may help if it's an overheating problem. Which it does seem to show the symptoms of.

Best of luck. ayenack.

---

### Post by guitarist549 on 2007-04-16
> **ayenack said:**
> This is not total rubbish. 

When micro processors started running at 2Ghz (I thing it was) and above they also started releasing certain amounts of microwaves and will continue to do so as they increase in speed. 

WIFI Adapters and many other devices also emit microwaves. It's to do with the frequency they use. This is how microwave ovens work they emit waves at a certain frequency which vibrates the food causing friction thus heating it causing it to cook. There is of course the ever ongoing issue with mobile phones releasing microwave radiation and whether this causes damage to the brain. Have you noticed when you use a mobile for a certain amount of time that your ear will start to get hot yet the phone is still cool to the touch? Well that's a case in point.

That's why Laptop processors are shielded. But the shielding is not always adequate.

An interesting and slightly sick experiment is to put a fly in a microwave oven and turn it on. The fly will happily fly around with no ill effects. It's effectively flying between the microwaves because it is to small to continuously be vibrated and thus heated.

Best of luck. ayenack.

A microwave *is* radio frequency. Yes, at 2 GHZ, the processor is naturally going to emit a slight amount of RF (every electronic component does) in the microwave spectrum, but it's not enough to hurt much. In regard to microwaves, the most vulnerable organ is your eyes.

---

### Post by ayenack on 2007-04-16
This is correct.

All thing radiate and have a frequency as you know. I believe that it's possible to cause ill effects in humans if you create a directed radiation at a frequency that is very close to the 2.4Ghz of wireless devices. This is close to the frequency of the human body I believe. It's also possible to make people urinate by using a sound modulation device at a certain sound frequency. All completely useless info I know.:-\" 

Best of luck. ayenack.

---

### Post by RudolfMDLT on 2007-04-16
> **ayenack said:**
> This is not total rubbish. 

When micro processors started running at 2Ghz (I thing it was) and above they also started releasing certain amounts of microwaves and will continue to do so as they increase in speed. 

WIFI Adapters and many other devices also emit microwaves. It's to do with the frequency they use. 

Well, bluetooth works on and about 2.4ghz... so does a microwave.... next time you put your phone in your pocket: How long wil it take something operating at mili-amps to cook you testicals in comparison with a 600Watt microwave. :)

---

### Post by ayenack on 2007-04-16
> Well, bluetooth works on and about 2.4ghz... so does a microwave.... next time you put your phone in your pocket: How long wil it take something operating at mili-amps to cook you testicals in comparison with a 600Watt microwave. 


LOL :D 

Don't intend to find out!!

---

### Post by iceman16us on 2007-04-16
> **ayenack said:**
> The fans on laptops don't always spin. They will often turn themselves off for a time. You should have an option in your laptops BIOS to configure the thermal mode. If so change it to performance this may help if it's an overheating problem. Which it does seem to show the symptoms of.

Best of luck. ayenack.

Well, it has two fans on the bottom and one of them was spinning while the other one was not.  I will still check in the bios for that option, but since the other one is spinning I would guess that would mean there is a problem with the fan.  Please correct me if I'm wrong though.

---

### Post by ayenack on 2007-04-16
I'm no expert on this but every laptop that I've had has turned it's fans on and off as a power saving function. If you watch the fans for awhile and one is continuously spinning and the other does not spin at all then yes it must be a problem with the fan.

The way I get more air under my laptop to help with cooling is to get a book and place the back of the laptop on it. Increases air flow.

Quick question. Is there an air vent on the left or right that blows air out of the side of your laptop? If there is I would suspect that this is the fan for the processor.

Best of luck. ayenack.

---

### Post by ayenack on 2007-04-17
You may want to print this out it's long.:( 

If you haven't done so already you may want to install lm-sensors as I suggested in an earlier post. I've heard that this has crashed some peoples PC's so don't do if you are not sure. It has never crashed any PC that I've used.

You can do this by typing these commands in terminal.

**sudo apt-get install lm-sensors**

Then type this

**gedit mkdev.sh**

This will open a empty text file. Paste the following into the file.

#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1] done
#end of file

Then save the file as mkdev.sh

Then type this to make the file executable.

**chmod +x mkdev.sh**

Run it.

**sudo ./mkdev.sh**

Then type this to detect your sensors.

**sudo sensors-detect**

This will run the sensors detect app. Answer YES to every thing here by typing y when asked.

Then type this.

**cat /etc/modules**

You will see something like this but probably shorter.

[B]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by sensors-detect on Tue Apr 17 03:06:17 2007
# I2C adapter drivers
# modprobe unknown adapter bt878 #0 [sw]
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-viapro
i2c-isa
# I2C chip drivers
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed on your system.
# For status of 2.6 kernel ports see [http://secure.netroedge.com/~lm78/supported.html](http://secure.netroedge.com/~lm78/supported.html)
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smartbatt
# Warning: the required module smbus-arp is not currently installed on your system.
# For status of 2.6 kernel ports see [http://secure.netroedge.com/~lm78/supported.html](http://secure.netroedge.com/~lm78/supported.html)
# If driver is built-in to the kernel, or unavailable, comment out the following line.
smbus-arp
eeprom
w83627hf

Load each module listed in the file shown with the command **sudo modprobe**. For example.

**sudo modprobe i2c-viapro**
**sudo modprobe i2c-isa**
**sudo modprobe eeprom**

Some modules may not load don't worry about these.

Then type this to show sensors.

**sensors**

This will show something like this.

[B]w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.66 V  (min =  +1.71 V, max =  +1.89 V)       ALARM  
+3.3V:     +3.28 V  (min =  +3.14 V, max =  +3.47 V)              
+5V:       +5.11 V  (min =  +4.76 V, max =  +5.24 V)              
+12V:     +11.98 V  (min = +10.82 V, max = +13.19 V)              
-12V:     -12.03 V  (min = -13.18 V, max = -10.80 V)              
-5V:       -5.25 V  (min =  -5.25 V, max =  -4.75 V)              
V5SB:      +5.67 V  (min =  +4.76 V, max =  +5.24 V)       ALARM  
VBat:      +3.66 V  (min =  +2.40 V, max =  +3.60 V)       ALARM  
fan1:     3970 RPM  (min = 10227 RPM, div = 2)              ALARM  
fan2:        0 RPM  (min = 4066 RPM, div = 4)              ALARM  
temp1:       +46°C  (high =   +36°C, hyst =   +40°C)   sensor = thermistor   ALARM   
temp2:     +58.0°C  (high =   +80°C, hyst =   +77°C)   sensor = thermistor           
alarms:   
beep_enable:
          Sound alarm enabled[/B]



The temp1 or M/B temp tag is the system temperature and the temp2 or cpu temp is the temperature of the cpu. You will be able to find out what the maximum temprature for your cpu is by doing a google search. Restart your system.

Best of luck. ayenack.

---

