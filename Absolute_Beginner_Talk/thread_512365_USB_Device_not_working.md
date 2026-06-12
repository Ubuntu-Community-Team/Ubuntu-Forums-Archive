---
title: "USB Device not working"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-29
I recently bought a USB adaptor for various flash cards, SD, MemoryStick, things like that.

I put it in my Computer and it wont work. Since the installer CD obviously wont run in Ubuntu, what should I do?

---

### Post by Cheese Roller on 2007-07-29
bump

---

### Post by AlexenderReez on 2007-07-29
hm...mine work fine...i just enter my memory stick and plug it to pc...have you try that in windows?..i think there is no need for driver for this kind of device:)

---

### Post by Peter76 on 2007-07-29
plug it in and the post the output of dmesg; preferably last 20 lines or so

---

### Post by Cheese Roller on 2007-07-29
I don't understand.

---

### Post by Peter76 on 2007-07-29
Ok, was ab bit quick, sorry. Here we go:

Open up a terminal ( it's under accesories or something in your app menu ) Don't plug in your usb thingie yet. In the terminal window type: dmesg. Notice the last lines and now plug in th usb dingie... Type dmesg again and you'll notice some new stuff at the end. Select it with your mouse and hit  ctrl+alt+c to copy it, leave the window open and post it here ( paste it ). Otherwise type dmesg > dmesg.log and attach this file ( now in your home dir ) here.

Good luck

Peter

---

