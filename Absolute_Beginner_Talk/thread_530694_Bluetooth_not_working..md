---
title: "Bluetooth not working."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-08-20
I am running an Inspiron e1505 laptop with integrated bluetooth. I want to be able to transfer files between my computer and my new phone. However, I am unable to. I have looked around a bit, installed all bluetooth-related packages, and have posted the basic information.

```

scott@scott-laptop:~$ sudo /etc/init.d/bluetooth restart
* Restarting Bluetooth services [ OK ]
scott@scott-laptop:~$ hciconfig
scott@scott-laptop:~$ hcitool dev
Devices:
scott@scott-laptop:~$ hcitool scan
**Device is not available: No such device**

```

Any help is appreciated.

---

### Post by philinux on 2007-08-20
I dont bother with bluetooth anymore. 

I just connect with usb cable fire up Gthumb and browse the phone, its much faster too.

---

### Post by Malice007 on 2007-08-20
Make sure you have your cellphone set up to you can see it when scanning for bluetooth(Discoverable). Once you connect to your phone I use Bluetooth File Sharing, you can find this by searching in Applications/Add/Remove.

Once installed you will have the icon in Applications/Accessories.  


Your phone manual should have come with instructions on how to make it Discoverable. If not you can post your model phone and I can try to look it up for you.


Also scan for new devices with your phone can you see your computer? This will help you figure out if you have a phone or a computer problem.

---

### Post by rouge568 on 2007-08-20
It is a computer problem: my phone can connect flawlessly with my bluetooth headset, and is easily made discoverable. My problem is that Ubuntu isn't recognizing my internal bluetooth transmitter/receiver.

---

### Post by Malice007 on 2007-08-20
I know this is a stupid question. But I know on my Inspiron 1420n there is a switch to enable my bluetooth/wireless. Do you have this on your laptop? All docs I have been reading Ubuntu should have no problem seeing this hardware.

---

### Post by rouge568 on 2007-08-20
Nope. I looked everywhere (and accidentally detached the battery) when I was trying to fix a similar wireless problem. Also, bluetooth is enabled in the bios.

---

### Post by Malice007 on 2007-08-20
The switch will not be on the bottom, looking at a pic online of your laptop it looks like the switch will either be right near your power button with the bluetooth symbol or this just my be a light. Is this light on? It looks like it is next to your wireless light? Or it looks like the switch is near your volume up/down on the very front of your unit?

Its hard to make it all out on the pics I see.When you hit your caplock A blue light turns on near your power button A I believe. now it that is just a light for bluetooth next to your power button that light should be blue also, letting you know you have it turned on. Bios might say you have it enabled but if your computer has a switch to turn it on and off it will not do anything.

---

### Post by Malice007 on 2007-08-20
Also one more thing, on my Dell laptop the Wireless (wifi) switch is also my bluetooth switch. When my bluetooth switch is on my bluetooth on my computer is on. And it has nothing to do with Ubuntu.

---

### Post by A$h X on 2007-08-22
I answered a similar query in another thread: 

[http://ubuntuforums.org/showthread.php?t=531753](http://ubuntuforums.org/showthread.php?t=531753)

Hope that helps.

---

### Post by rouge568 on 2007-08-28
Well, I figured out the problem. Turns out I do not have a bluetooth card installed. I went to the manual's section on replacing the bluetooth card and decided to check if it was installed or not. I took out the battery, opened the compartment, and was met by a loose connector. Ah, well. Perhaps eBay will help me...

---

