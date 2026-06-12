---
title: "Compaq Presario V2000 laptop"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ChaosMastero on 2007-05-31
Does Linux Ubuntu have all the nessasary software to get a Compaq Presario V2000 laptop online wirelessly?  I was thinking about trying it on my laptop but want to be sure that I can atleast get it online so I can get the rest of the software I might need.

---

### Post by blazercist on 2007-05-31
you may want to specify the chipset of that laptop's wireless card... also try the live cd it may "just work".

---

### Post by lazyart on 2007-05-31
searching the forums for V2000 shows it will take some tweaking to get it right.  definitely download the live CD and see how it goes for you.

---

### Post by elquer on 2007-06-06
well i'm using my pressario v200 amd turion 64 right now and still can't figure out how to the radio button to light up. i'm able to see wireless as on under network but can't turn it on so have no wireless connection at the moment. if you succeed with your installation let me know please. ps using feisty fawn (/704)

---

### Post by homerhomer on 2007-06-11
more than likely your compaq is using a broadcom card.

take a look and see if it does

go to the command terminal and type the following (you can copy and paste it too)
lsmod | grep bcm43xx

or 

go to System > preferences > hardware information
look around for something that says wireless. and see if it says something broadcom

if it's using broadcom you need the firmware 
get it here
[http://debian.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://debian.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)

---

### Post by pbmax on 2007-06-12
thanks for the link to the broadcom firmware.  
It installed fine (xubuntu 7.04) and now my wireless button lights up.  However, it still doesn't connect.  And the light won't turn off (if that matters)
I deleted the ndiswrapper drivers, like it suggested, but still no good. (they didn't work either.)

Anything else I can try?

edit
nevermind.  After another reboot, it works flawlessly.  The button works and lights up, and I get connection.
Sweet.
thanks
pb

---

### Post by Cuogar on 2007-06-23
Thanks HmerHomer. Your link was the perfect solution after reboot I was on line and going. I have yet to fully test the range and functionality fully, but it is looking good.

---

