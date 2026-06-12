---
title: "ASUS X201e touchpad problems all of a sudden"
date: 2014-01-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by azhar.basit on 2014-01-19
Hello,

I am using ASUS X201e DH01 with Ubuntu 12.04.  
All of a sudden after quite  few months my touchpad has seem to gone bananas and has introduced new gestures.  
Maybe it has been due to one of the updates?

However now when when I do a two finger swipe it does a vertical scroll as expected but now it also opens up the dash.   I have spent hours looking into synaptiks, pointing devices, synaptics driver configuration but am unable to make it behave in a consistent manner.

Can anyone advise how I can enable/disable specific gestures only? 

thank you,

---

### Post by varunendra on 2014-01-21
Maybe take a look at the outputs of :
```
synclient
```
and
```
xinput list-props <Name or ID of your touchpad>
```
and see if the new gestures are listed in any of them. If they are, they can also be edited/disabled from these commands (although the change will be temporary).

The ID/Name of your touchpad can be listed with "xinput" (without options) command. Post the outputs here if not sure.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by azhar.basit on 2014-01-22
I had tried both of these commands (and many others) and tried to manually configure the synaptics ETPS/2 Elantech touchpad.  After two days of struggling with this I pretty much gave up.  And went back to an older setup that had worked.  

I created a synaptiks_startup.sh file which would load the synaptiks program on startup and also run a synaptikscfg init.  
Now this problem has gone away.  

I would also add this behavior started when I started using multiple monitors.  Now I am careful to first boot my laptop and then attach the extrenal monitor.  Doing this in sequence seems to have prevented from re-occuring.  I also had to mess around with "CompizConfig Settings manager'.  Including the experitmental part which had to do with 'pressure' and velocity. 

Whatever the issue was it is not happening now and I don't want to try to reproduce it (having lost two days).   Basically using loading synaptiks (with the saved configurations I want) in a startup batch file and attaching an external monitor after the laptop has booted up, seems to be preventing this from re-occurring again.

---

