---
title: "K800i on ubuntu"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by JAK86 on 2006-10-30
Hey guys, first time poster here so be nice ;)

 recently went for it and removed windows from my computer and installed Ubuntu, i love the setup and cant wait until my update service allows me to download an install the newest release.. 

 Just got back from a works do and wont see many of my friends again, took a fair few pictures on my k800i camera phone and would like to upload them onto my computer so i can email them out.

 So my real question is, is there a k800i driver for ubuntu? where do i get it from? and does it have all the features that the windows software has?

 Cheers,

JAK

---

### Post by JAK86 on 2006-10-30
Dumbass alert!

 only needed to plug the thing in and it found it and let me upload straight away... oh i love ubuntu ;)

---

### Post by mariusdumi on 2006-11-08
Hi,

I had the same problem. 
Indeed, Ubuntu discover my K800i as a USB storage device, but only if I chose to use the phone in "File Transfer" mode (this mean that no calls could be received or initiated). But if I wanted to transfer file from/to the phone and also to use the phone (when connected to USB cable chose "Phone Mode") the phone was not mounted.
Took a little research and found some packages that can help to solve this problem.
Here they are: "obexftp"; "libopenobex1" and (may be not needed, but I installed it) "openobex-apps".
After you install those packages (using synaptic or apt-get) you run obexftp in console as su (you can access USB devices only if you have root privileges). To see a list of commands use obexftp --help

---

### Post by PriceChild on 2006-11-08
Glad to hear it worked out of the box!

I was amazed when my Motorola V3i worked first time. - Ubuntu's great isn't it :)

*Marks thread as resolved*

---

