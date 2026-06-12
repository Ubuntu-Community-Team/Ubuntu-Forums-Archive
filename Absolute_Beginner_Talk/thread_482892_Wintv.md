---
title: "Wintv"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by m47h3us on 2007-06-24
iv got it set up and computer knows its a wintv device, how ever i can not get it to work in mythtv when i come to scan for channels it says no signle but iv pluged it in windows it will pick up the channels fine it is set to dvb and uk as well.

---

### Post by wolfen69 on 2007-06-24
what model# is it?

---

### Post by m47h3us on 2007-06-24
Nova-t USB2 not sure on model so i will give you wats on bk erm 93000 rev b8a2 lot 1805

---

### Post by m47h3us on 2007-06-25
come on, some one help you cant tell me that the Wintv nova-t usb2 93000 is the only f^%&ing digital card that does not work on ubuntu, cos as you see this is really pissing me off. im thinking of going back to xp again if no ones gona help me.

---

### Post by wolfen69 on 2007-06-25
first off, nobody cares if you go back to xp. second, people that WANT to make linux work are the ones who are rewarded. if you go running back to xp so fast, maybe you shouldnt be using linux in  the first place.on to your problem.

try this:

Originally posted by tropicflite

 I have a Hauppauge 150 card running on my Feisty box, and I get live tv by going to 

File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing

sudo apt-get install ivtv-utils

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

### Post by Vorian on 2007-06-25
let's play nice folks :)

---

### Post by m47h3us on 2007-06-25
i have worked out what is wrong with my dvb, it seems that Linux does not like weak singles at all, i need a way so it will add the weaker ones aswell cos it works fine on xp with the areal in my room.

---

