---
title: "Udev Rule usb inserted"
date: 2015-10-25
forum: Any Other OS
---

### Post by people2 on 2015-10-25
Hi im a newbee in this forum and in all related with ubuntu.

I received a raspberry pi running raspbian at work and I've being ordered to make a task with it. I've never do anything with rasp. and just a li Little tle bit in linux so im really lost.
I need to execute a program that opens a tcp socket and send some data to a server every time a usb is inserted and removed no matters wic which kind of usb device.
I've being reading a lot and searching for help but i didn't even manage to do the first part (usb insertion and removal events) what I've read is that i have to create a udev rule for us add and removal but i had no succes with it.

I've create a new file in my udev/rules.d foler with this line

ACTION=="add", env{DEVTYPE}=="usb_device"  RUN+="/home/pi/Desktop/hi"
ACTION=="remove", env{DEVTYPE}=="usb_device"  RUN+="/home/pi/Desktop/bye"


hi and bye are just two c++ scripts that open a notification to see if the rule is correctly done. But looks like it is not correct because nothing happens :(

Please guys can somebody help me (without making fun, i already say im a newbee) hehe

---

### Post by howefield on 2015-10-25
Hello people2 and welcome to the forum. Your thread has been moved to the "*Any Other OS*" forum as it is not an Ubuntu query.

---

