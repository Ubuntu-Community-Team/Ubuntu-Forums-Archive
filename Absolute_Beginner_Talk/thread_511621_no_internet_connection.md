---
title: "no internet connection"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by devarshi84 on 2007-07-28
Hi,

I have been a windows user until now. Just installed UBUNTU 7.04. 

I am not able to get connected to the internet with my desktop now. My laptop is running windows and connecting though.

The ADSL modem is from HUAWEI WA1003A and my desktop connects to the internet through USB.

I input the TCP/IP settings but to no avail.

I am a noob. help me. please.

---

### Post by tomcheng76 on 2007-07-28
USB ethernet adaptor ?
wireless or wired ?

---

### Post by devarshi84 on 2007-07-28
Its a USB ethernet connection.

---

### Post by devarshi84 on 2007-07-28
my laptop is on wireless with windows

but my desktop is on UBUNTU on USB.

---

### Post by devarshi84 on 2007-07-29
BUMP: The problem remains. Please help.

---

### Post by livingtarget on 2007-07-29
You can have a look at System -> Preferences -> Hardware information if your modem pops up there. If it isn't detected than it's likely there's no kernel driver for it. Unlikely but a good check.

I'm not much help with networking, I'm really bad at it. It may be an issue with the Network-Manager (the connection icon in your panel) try seeing what it says.

You can try a "sudo /etc/init.d/networking restart" to see if it helps. This is maybe a bit advanced for a newbie. Go in the terminal (applications -> accessories -> terminal) and type the command between the quotes. Let us know what it says if possible (I may not be here to reply, but it may help other people).

---

### Post by Espreon on 2007-07-29
Goto System>Administration>Restricted Drivers Manager and look for anything that looks like it would hafat do with your ADSL thingy. 

Or pop in your Ubuntu CD and when it says that Ubuntu detcts packages on the CD hit start package manager and hit origin and the Feisty CD and look for ADSL and  will find some thingies that could help.

---

