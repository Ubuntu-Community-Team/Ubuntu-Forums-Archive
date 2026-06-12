---
title: "Mactel (AppleSMC macfantld) Create folder in /sys/devices/platform"
date: 2016-02-28
forum: Apple Hardware Users
---

### Post by pestilence000 on 2016-02-28
I need to fix the fancontrol for Ubuntu 14.04. I had everything in place, but when i did a SMC reset, the fancontrol was gone, macfanctl was not working.

I see that there is no applesmc folder in /sys/devices/platform. I need to create a folder called "applesmc.768" at this location. I looked around and I can't find it how to do it. I may be going in a very bad direction, by trying to do something that I'm not supposed to do like editing contents of sys folder ( I know that this is sort a virtual space). But, if it's possible lemme know.

If there are other ways to fix the fan issue, then I would really appreciate that as well. I'm running Ubuntu 14.04 in Mactel 4,1. Thank you.

---

### Post by Bucky Ball on 2016-02-28
*Thread moved to **Apple Hardware Users**.*

---

### Post by MikeBraxner on 2016-02-29
@pestilence000 ... I'd say, forget about 'creating' sys folders.

With an SMC-reset, I'd presume you'd need to re-run your sensor-detect, but to be on the safe side, your best bet would probably be a clean re-install of applesmc, macfanctl, and sensors (+detect). That should take care of it.

---

### Post by pestilence000 on 2016-02-29
I'm on Ubuntu 14.04, and I cannot install applesmc. The log error with macfanctld is that "applesmc device cannot be found", no temperature files in /sys/devices/platform. 

@MikeBraxner : There is no package for applesmc for 14.04. Somehow, I had fixed it before, but can't remember how. It's been bugging me for days now. 
Yeah, making folder doesn't make sense, even if there might be some ways to do it. I need to install applesmc. Btw, the keyboard backlight is also not working, same sensors issue i guess.

---

### Post by MikeBraxner on 2016-02-29
@pestilence000 ... You should be able to use the Raring version straight from the PPA. A while back, someone [had a similar issue, and managed to get sorted]("http://ubuntuforums.org/showthread.php?t=2222611"). There were a couple of goofs, so make sure you read it ALL first.

Otherwise, just compile it yourself, should work without a hitch.

---

### Post by pestilence000 on 2016-03-01
I ended up formatting and installing OSX. But I still cannot get temperatures using smcFanControl, it just reads 0C and 0RPM even though the fan is running at full speeds. It might be some hardware issues as well, my battery is bloated, I dont know if it has anything to do with that.

@MikeBraxner : And thanks for pointing out the alternative PPA for 14.04. I will certainly try it out after I reinstall the Ubuntu 14.04.

---

### Post by pestilence000 on 2016-03-02
After searching over forums over forums, I have found the solution to quiet down the battery. 

At the time I had OS X installed, not Ubuntu, but Should work with Ubuntu too. 

Problems : 
Fan Blowing at Full Speed. 
None of the sensor apps reading temperatures. ( No applesmc in ubuntu, 0C and 0 RPM in os x )
BackLight not working.

Solutions.
SMC Reset : But the regular SMC Reset that I found on most site including Apple didn't work. This is what I did.

Turn off the computer. Take out the battery. Unplug the charger. Press the Power Button for 20 seconds. Then, plug in the charger without leaving the power button, do this for another 20 seconds. 

Now, DONOT turn on the computer. Put the battery back, it'll start to charge. Let it charge for 30 mins or an hour. Then, turn it back on. It should work now.

Hope it will be helpful to someone.

---

