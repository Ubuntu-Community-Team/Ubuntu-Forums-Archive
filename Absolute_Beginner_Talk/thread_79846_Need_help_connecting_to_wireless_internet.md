---
title: "Need help connecting to wireless internet"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by Linkdx on 2005-10-20
I have cox, and my dad's router is downstairs, now pay in mind... He set up every single wireless connection in our house but absoloutely wont touch my dual-booted ubuntu linux, I need to learn how to connect to the internet by myself.

---

### Post by odin on 2005-10-21
well I'll take as a "I dont know anything about it" question and try to explain.

First of all you should be sure your wifi card is up so open a terminal and type this:

**ifconfig "device" up **

then be sure that your device is up and running by typing: 

**iwconfig**

You should see some parameters of your interface.

Find out what your access point essid (the essid is just the name the access point has for identifying it) is and the wep-key (if you have set one for connecting to your access point) too.Now look for your wifi access point:

**iwlist "device" scanning**

You will see a list of all the access points in the range of your wifi card.You should see in that list your access point.When you know all this data then type:

**iwconfig "device" essid "your_access_point_essid"**

if you need the wep-key just type:

**iwconfig "device" key "your_key"**

And after this the last step.I guess you can get your ip via dhcp so I'll explain it based on that and if you dont get it working like this,post it, and I tell you how to set it in the other way.So for dhcp just type:

**dhclient "device"**
 
And after all this story  you should have your wireless conection working.Well english is not my language so probably you didnt undertand some things so jsut ask and I'll try to explain better as soon as I can.Please tell me if everything worked and then I can tell you how to set it so you dont have to do all this manually everytime you boot.

---

