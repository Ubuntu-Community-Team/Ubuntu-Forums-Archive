---
title: "im a noob who is lost"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by novacore on 2006-04-30
hi all im a noob with  linux but am very courious about trying a new os that was not microsoft. so i downloaded a live ubuntu cd and burned it to a dvd. it seams to load untill i get to the  part where i have to choose the screen resalutions id like to use. it tells me that the x-sever doesnt load and and it wont continue what am i doing wrong? 

 any help would be very aprecated  i would like to get to the point that i dont have to use windows any more.

---

### Post by huckem on 2006-04-30
please post your system specs.  Its hard to diagnose a problem like this without knowing the hardware you are using.  Also- Can you type the error message exactly as it appears when starting X?

---

### Post by novacore on 2006-04-30
i have an amd 64 3500 with 2 gig of ddr400 ram on a gigabyte k8ns ultra mobo. an ati 1600pro 512mb agp gpu , 2 120 gb hard drives in a raid 0 
a 120 gb hard and a 160gb hard drive setup for storage,and on board audio. sorry about that i should have put all this info in the first post.

---

### Post by nalmeth on 2006-04-30
hmm
do you get to a command line prompt asking you to log in, and leaving you in a shell?
username@hostname:~$


if so, type in the following command:
sudo dpkg-reconfigure xserver-xorg

when it asks you to pick your video driver, pick ati, or vesa.
ATI should be selected by default (as you have an ati card), but you may require the restricted driver. 
If that is the case, go with the vesa driver for now, and then when you're inside, you can get the restricted video driver.

---

### Post by huckem on 2006-04-30
what he said! :D

---

