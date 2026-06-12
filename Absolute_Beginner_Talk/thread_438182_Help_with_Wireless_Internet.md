---
title: "Help with Wireless Internet"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-05-09
I have a comcast wireless usb adapter for my windows computer and that is how I get my wireless internet from my router. But Ubuntu will not even read  the usb adapter when I put it in my computer. I know that is probably some driver that I need, but given that Ubuntu will not even read it, I will have some trouble. I would greatly appreciate if you could walk me through the steps about how to set up a comcast wireless adapter, get it to actually detect wireless settings and to automatically connect to a wireless connection.

Thanks
:guitar:

---

### Post by Hero of Time on 2007-05-09
What does "lspci" say in a terminal? Post that first so others know how to set it up. Some adapters need special installation, others work out of the box and others have a run and fun setup. You must look at the section of "Network". It can look like this:
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
This is my network card, build-in in my laptop. Yours will look different of course.

---

### Post by jprb85 on 2007-05-10
When I type lspci I do not get anything that says any about networks. I says RAM memory and other things but nothing related to network. My wireless connection is my wireless usb adapter. It of course connects via usb, but Ubuntu will not even detect it or acknowledge it. The card was made by a company called Comcast which is now part of Time Warner. I would greatly appreciate any other help you can offer. Thanks. 

:popcorn:

---

### Post by jprb85 on 2007-05-10
The official name of the card is wireless usb adapter. I am now listing some important information about it
MA111
FCC ID: PY3MA111
MAC: 000FB5003C37
S/N: MA18149ZD000543
Comcast ID: MA1814900543

---

