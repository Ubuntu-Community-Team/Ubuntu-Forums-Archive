---
title: "I'm compiling a driver for M$ Lifecam vx-1000 ... where do I put it?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-07-20
Hey folks. I just bought a Microsoft webcam (VX-1000) and I found a driver that claims to work with it. My issue is where I'm supposed to put it. Any thoughts?

---

### Post by sad_iq on 2007-07-20
So are you sure the camera isn't supported??? What does **lsusb** says??? Googled a little and found this...[https://answers.launchpad.net/ubuntu/+question/9617](https://answers.launchpad.net/ubuntu/+question/9617) they claim the cam is supported out of the box(maybe it's a different model). Also...where have you tried to download the driver???

---

### Post by CheshireMac on 2007-07-20
I haven't tried installing it anywhere yet. I just installed Ubuntu after being without a computer in any sense for six months, so I'm really sketchy on doing things like installing drivers. I was hoping Ubuntu would pick up on what it was and auto direct it to it's proper place. In any case, when I plug the cam in, the computer doesn't acknowledge that it's there, or at least that's what I've seen so far. I'm still digging here myself, but my connection is lousy (Wifi from one of my neighbours.) I have to work on that too. ~LOL~ In any case, I have the driver, and I'm just trying to find the proper place for it, to see if it activates the camera in some form. ~LOL~

---

### Post by sad_iq on 2007-07-20
Well the deal is that finding a driver is basically an Ms-Crap(TM) feature, linux _usually_ has the driver once you plug something in your box.To see if your camera is detected open a terminal(don't really know where it is...just look trough the menus) and type ```
lsusb
```. Just paste the result here.
 Oh...and another thing...I don't know if you get a warning when you plug a webcam with ubuntu(could be wrong thou)!!!

---

### Post by atm0sph on 2007-12-12
Bus 004 Device 003: ID 054c:014d Sony Corp. Memory Stick Reader/Writer
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00f7 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  


The sony corp vcc-u01 is a built in webcam that doesn't work due to a wiring issue..  I'm assuming the Microsoft Corp is the lifecam.  Any suggestions?

---

