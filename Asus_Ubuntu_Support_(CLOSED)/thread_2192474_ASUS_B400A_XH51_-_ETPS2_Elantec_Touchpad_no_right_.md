---
title: "ASUS B400A XH51 - ETPS/2 Elantec Touchpad no right click"
date: 2013-12-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mbio.kyle on 2013-12-08
Hello, 

First time poster here! Just got a new ASUS B400A laptop, and dumped win7 for Ubuntu. I have some experience (mostly in Debian) but cannot seem to figure this one out. I searched all over for possible solutions, but here is the deal:

I installed 13.10 and everything works fine, except the right click button. The laptop has to discrete clickale buttons (as opposed to the single pad). 

kyle@rubberfeet:~ > xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)] &#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] &#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)] &#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]     &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]     &#8627; Power Button                            	id=6	[slave  keyboard (3)]     &#8627; Video Bus                               	id=7	[slave  keyboard (3)]     &#8627; Power Button                            	id=8	[slave  keyboard (3)]     &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]     &#8627; USB2.0 HD UVC WebCam                    	id=10	[slave  keyboard (3)]     &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]     &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

I installed synaptiks (as per the reccomendation of many similar threads)
It verififed that the mouspad device was infact the ETPS/2 Elantech Touchpad.

I fired up xev and sadly the right click does not produce any output. Seems like the right mouse button just does not register at all. Looking for any advice.

Thanks,
Kyle

---

### Post by Techian on 2013-12-11
Hi!

I have the same problem on Asus pro BU400A running Ubuntu 13.10. The touchpad is identified correctly as ETPS/2 Elantech and the right button doesn't seem to work.
"xinput --test <device id>" recognizes left button click but nothing on right button.

I've also tried recommended scripts from below site without any success:
[https://github.com/avernois/enable-elantech-on-ubuntu](https://github.com/avernois/enable-elantech-on-ubuntu)

Any suggestions on how to move forward with a problem like this?

Regards,
Arbi

---

### Post by mbio.kyle on 2013-12-12
Hello Arbi,

Does your laptop have one mouse pad with designated areas for left and right click or is there a touchpad and then seperate buttons for right and left click? I think a lot of the threads and fixes I have come across have to due with the single trackpad problem. In my case I have discrete buttons that are not being recognized.

---

