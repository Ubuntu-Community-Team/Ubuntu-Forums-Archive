---
title: "disable tap to click on wireless keyboard?"
date: 2012-12-04
forum: Apple Hardware Users
---

### Post by mbaucco on 2012-12-04
Hello,

I've purchased a Perixx 716 wireless keyboard for my macbook running 12.04. Although the keyboard and mouse work, I can't disable tap to click on the wireless keyboard's integrated touchpad. I tried installing "Pointing Device Settings", but it only shows the apple touchpad.

Can anyone please help me fix this? Please let me know if you need more information.

Thanks,
Matt

---

### Post by circleinsideabox on 2013-02-07
> **mbaucco said:**
> Hello,

I've purchased a Perixx 716 wireless keyboard for my macbook running 12.04. Although the keyboard and mouse work, I can't disable tap to click on the wireless keyboard's integrated touchpad. I tried installing "Pointing Device Settings", but it only shows the apple touchpad.

Can anyone please help me fix this? Please let me know if you need more information.

Thanks,
Matt
I am having the same exact issue with my newly purchased logitech wireless keyboard/touchpad and ubuntu 12.04

---

### Post by valroadie on 2013-02-08
Hello,
I am not sure about USB keyboards or mice but with the trackpad on the macbook if you install synaptiks it lets you disable the trackpad at will. 
I am not sure if it will be used to manage the wireless keyboard and mouse but you could give it a try! 

It can be found in the ubuntu software center under synaptiks. Hope this helps!

---

### Post by mbaucco on 2013-04-22
Thanks for the suggestion! Unfortunately it tells me I do not have a synaptics touchpad installed. I read somewhere about some touchpads being ALPs or PS/2, but couldn't find a fix that I could understand with my limited knowledge of Linux.

Thanks again,
Matt

edit: here is some information from xinput list:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Chicony USB Wireless HID Receiver       	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Chicony USB Wireless HID Receiver       	id=8	[slave  keyboard (3)]

As far as I can tell, the trackpad is using the evdev driver.

---

