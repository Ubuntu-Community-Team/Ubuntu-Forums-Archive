---
title: "Webcam help needed"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-23
I found out the following using a command given somewhere on the forums to find out about my webcam ;)

```
Bus 003 Device 002: ID 0c45:602a Microdia Meade ETX-105EC Camera

```

Can anyone help me get this working PLEASE (be forever grateful) :KS

---

### Post by Viskovitz on 2007-05-23
It looks like your camera is recognized. It should work; have you tried opening Ekiga and seeing if it works? Do you receive any error message?

---

### Post by Kobalt on 2007-05-23
Check [this]("https://help.ubuntu.com/community/Webcam") or [this]("http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml").

---

### Post by chemtut on 2007-05-23
download camstream from synaptic
run camstream in aterminal

---

### Post by lopagof on 2007-05-23
try xawtv or search on google about your camera

---

### Post by Cloudedbrains on 2007-05-23
> **Kobalt said:**
> Check [this]("https://help.ubuntu.com/community/Webcam") or [this]("http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml").

Camerama give me an error :(

[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot-1.jpg[/IMG]

---

### Post by Cloudedbrains on 2007-05-27
Help it still wont work :(

---

### Post by michelek on 2007-12-05
looks, that there is no solution for Microdia cameras.
my camera
 
$ lsusb
Bus 005 Device 002: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

definately is not shining to /dev/video0

so, im giving up.
btw, I can use my camera from windows running in vmware player...

mmp

---

### Post by vivalant on 2007-12-06
0x624f is supported by the binary-only driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by ubu-lemon on 2007-12-07
> **Cloudedbrains said:**
> Camerama give me an error :(

[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot-1.jpg[/IMG]


i've got the same problem,

did you find any solution yet?

---

### Post by SyberKowboy on 2007-12-07
I have a Chicony webcam built into my MSI laptop that I can not get to work in Gusty or any other build for that matter, but will work in a XP or an XP VM. Would love to get it working natively. Thanks everyone for getting these drivers up and running.

---

### Post by subs on 2007-12-08
try camorama..... it works on mine.....

> sudo apt-get install camorama

---

### Post by philinux on 2007-12-08
you could try this driver

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Found this too.

[http://www.hermann-uwe.de/blog/for-those-who-care-about-sn9c10x-based-webcams](http://www.hermann-uwe.de/blog/for-those-who-care-about-sn9c10x-based-webcams)

---

### Post by ubu-lemon on 2007-12-10
how do i know what webcam (= in built) i have? 
i suppose i need that in order to find out about these pages with drivers you just posted here?

(sorry i'm just very new to linux, the ubu in my usersnames is for my enthousiasm not my experience...:rolleyes:)

---

### Post by subs on 2007-12-11
> **ubu-lemon said:**
> how do i know what webcam (= in built) i have? 
i suppose i need that in order to find out about these pages with drivers you just posted here?

(sorry i'm just very new to linux, the ubu in my usersnames is for my enthousiasm not my experience...:rolleyes:)



type *sudo lsusb* and paste the contents here...

---

### Post by ubu-lemon on 2007-12-11
Bus 006 Device 002: ID 0402:5602 ALi Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000


can you enlighten me ? 
(and also tell me what you see ? :-) )

---

### Post by subs on 2007-12-11
ubuntu does not have drivers for this particular camera(comes along with most lenovo lapstops)

there is a project underway to develop a driver..... but it hasnt produced any concrete drivers yet....

heres the link... [https://sourceforge.net/projects/m560x-driver/](https://sourceforge.net/projects/m560x-driver/)

u can try helping them to develop the driver...

---

### Post by ubu-lemon on 2007-12-11
ow, :'-)

what kind of help could that be ?

---

### Post by ubu-lemon on 2008-04-28
i bought an extern webcam, found here a page with a list of webcams
([http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html))


found the driver suggested, but i don't know what to do (being a enthousiastic but unskilled ubuntu user)

also it says that i should remove the ov511 driver's module before installing the ov51x
([http://alpha.dyndns.org/ov511/download.html#ov51x](http://alpha.dyndns.org/ov511/download.html#ov51x))

and there are three options on this page, which one should i choose (and why?)

thanks in advance !

---

### Post by ubu-lemon on 2008-04-30
:cry:


should i start a new topic instead ? (i thought since it was related but i also see 'archive' , anyway i'm a bit lost with the new look and all...)

---

