---
title: "How can I troubleshoot IEEE1394 / Firewire board and cameras?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by transistor on 2006-05-20
I have a Unibrain PCI Firewire card in my Compaq running Ubuntu. I have a couple of Unibrain Fire-i cameras and cables. I have spent many many hours trawling through the forums looking for info on getting the gear going but have failed.

Q1. Can anyone point me to a howto showing me how to get the system working? i.e. What program could be used to test the cameras? (I'd use NetMeeting on a Windows machine.)

Q2. How do I get the IEEE1394 working?

Q3. Will this be easier in Dapper Drake? Should I put the project on hold for a month until Dapper is released?

Many thanks.

---

### Post by transistor on 2006-05-20
Progress report:
I found **gscanbus** on Synaptic Package Manager and this gives some debug information. Gscanbus gives a graphical representation of the firewire devices. I can see my ohci1394 device(?) and the cameras appear and disappear as I plug them in and out. A nice touch is that it shows the cameras in series when daisy-chained and in star configuration when each camera is plugged into a separate firewire port.

Q. What program can I use to view the camera output?

Thanks again

---

### Post by Sef on 2006-05-20
You can check out this, but it is in alpha now.

[http://www.diva-project.org/]("http://www.diva-project.org/")

---

### Post by benguin on 2006-05-20
Coriander. Best for IIDC compliant iee1394 cameras. I have a significant amount of work on firewire cameras under linux, and coriander is the best I have seen so far. 

That said, if these are IIDC cameras then you will be able to use coriander. If they are camcorders with DV output, then go for kino. Both these software are available from synaptic. I personally also use coriander 2 pre-release, but its not easy to setup.

Hope that helps.

-J-

---

### Post by transistor on 2006-05-21
Thanks Sef and Benguin. I have Coriander running and it can see my cameras but I still haven't got a picture from them. 
The [Coriander manual]("http://damien.douxchamps.net/ieee1394/coriander/manual.php") says 
> **SDL**
One of the major feature of Coriander is its live display. This function requires the SDL library. You should simply install the library on your computer, using your distribution packages. I can't think of a distribution without SDL so you won t have problems to find it.

**Vloopback**
The vloopback interface is a kernel module which can be used to export video through a V4L device. It elegantly changes Coriander into a V4L source that can be further used by applications like Effectv or Gnomemeeting. 

Q1. There isn't any window in Coriander to show a live display. Does this only appear when the video stream is working?
Q2. Do I need SDL? I can see in Synaptic that I have libsdl1.2debian and libsdl1.2debian-oss installed. Is this all I need or am I missing something?
Q3. I can't find any reference to Vloopback in Synaptic or lsmod. Do I need it and how do I get it if I do?

Thanks.

---

### Post by benguin on 2006-05-21
Hi there,
Quick questions:

1. Did you start ISO tranmission? 
2. If you did, did you click on the receive button on the services tab? To see live pictures, you have to first start the ISO stream, click receive and make sure you are receiving frames at a certain frame rate (that information should appear right under the receive button) and finally click on display to see the live feed.

Now to answer your questions:

Q1. There isn't any window in Coriander to show a live display. Does this only appear when the video stream is working?
Answer is yes.

Q2. Do I need SDL? I can see in Synaptic that I have libsdl1.2debian and libsdl1.2debian-oss installed. Is this all I need or am I missing something?
Answer is, if you used synaptic, everything you need should have been installed automatically. 

Q3. I can't find any reference to Vloopback in Synaptic or lsmod. Do I need it and how do I get it if I do?
You do not. vloopback is for using a firewire camera as a video4linux device. If you understand what that is, you might want to look into it out of curiosity, but you do not need vloopback at all for just firewire output.

Hope that helps.

-J-

---

### Post by transistor on 2006-05-22
Thanks Benguin.

A little progress. On the services tab I started ISO (isochronous) control, enabled the receive button and the display button. The trigger is set to 30fps but the Switch/FPS is showing only 16fps received and displayed.

The image is awful - it looks dark brown, underexposed, way out of focus and stretched vertically. It can make out the window of the room and light bulbs and would have been very exciting in 1937 (but not in 2006). The cameras work fine on a Windows machine. I'll try to troubleshoot this step of the process.

---

