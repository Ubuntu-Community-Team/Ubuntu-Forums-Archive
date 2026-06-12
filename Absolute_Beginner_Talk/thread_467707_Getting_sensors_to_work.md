---
title: "Getting sensors to work"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by wink on 2007-06-08
Having experienced power supply problems in the past and it being a pain to gain access to data by way of the BIOS (which means a reboot), I was delighted to hear about lm-sensors. I downloaded and installed the package but now, as a total newbie, I am stuck, i.e., don't know how to get them to work. Here is how far I have gotten:

sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
lutz@lutz2:~$ sensors-detect
You need to be root to run this script.

How do I get to be root or, better yet, is there another way than what I have done?

Thanks in advance for any advice.

wink

---

### Post by w4ett on 2007-06-08
try sudo sensors-detect

---

### Post by wink on 2007-06-08
Beautiful! That did it, allowed me to run the script, and works great. Thank you. 

My next question is instead of running "sensors" from the command line, can it be made into an icon and placed on the panel? Or is that asking too much? 

wink

---

### Post by mills on 2007-06-08
gdesklets will give you small monitors on the desktop and i think there may be an option for a top panel monitor
right click the top panel then click add to panel and see if theres a monitor there, iam sure there is but cant quite remember for certain

---

### Post by voided3 on 2007-06-08
ksensors has a panel monitor as well as a floating window; it's very similar to MBM5 (motherboard monitor) for windows if you are familiar with that.

---

