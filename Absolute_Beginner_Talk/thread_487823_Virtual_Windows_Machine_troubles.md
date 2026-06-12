---
title: "Virtual Windows Machine troubles"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-29
I just installed a virtual windows machine using Vbox.  I can't seem to get it to detect my graphics card or wireless card.  Are there any tricks to getting it to do this?? Is it a problem w/ windows???

---

### Post by Seisen on 2007-06-29
It emulates a computer so your graphics card won't show up neither will your wireless. Does everthing work in Windows?

---

### Post by Mazen on 2007-06-29
I think you have to enable your ubuntu to share the connection or certain devices with the virtual machine.
i don't know exactly how it's done in Vbox, but that's the concept.
hope it helps

---

### Post by Mostlyharmless42 on 2007-06-29
yea, but i can't get it to the resolution i'd like and i would like to have internet for gaming purposes.  I wasn't sure if it was possible.  Another question is how do i get files into windows, like photos and such?

---

### Post by Mostlyharmless42 on 2007-06-29
> **Mazen said:**
> I think you have to enable your ubuntu to share the connection or certain devices with the virtual machine.
i don't know exactly how it's done in Vbox, but that's the concept.
hope it helps

i figured it was something like that, but i have no clue how to do that.

---

### Post by Mazen on 2007-06-29
> **Seisen said:**
> It emulates a computer so your graphics card won't show up neither will your wireless. Does everthing work in Windows?
It will give a Vbox virtual graphic card, and i guess same with the wireless.
Sharing is for USB devices mostly.
and as mentioned , if u have an ATi you will be given a virtual graphic card, NO 3D is functional in virtual systems either!

---

### Post by Seisen on 2007-06-29
Ya, no playing half-life in VirtualBox.

---

### Post by Mazen on 2007-06-29
> **Mostlyharmless42 said:**
> yea, but i can't get it to the resolution i'd like and i would like to have internet for gaming purposes.  I wasn't sure if it was possible.  Another question is how do i get files into windows, like photos and such?
Internet is gonna be provided by sharing the connection you have with the virtual machine,
i'm sorry i'm being very vague and general but i don't have vbox and i'm remotly connected to my machine so it's a hastle to install!!

---

### Post by Mostlyharmless42 on 2007-06-29
Right now i have a generic video card w/ a very basic driver and it shows no indication the wireless exists

---

### Post by Seisen on 2007-06-29
Have you tried opening up IE and see if works?

---

### Post by Mazen on 2007-06-29
> **Mostlyharmless42 said:**
> Right now i have a generic video card w/ a very basic driver and it shows no indication the wireless exists
For internet you will have to share your host connection, that's the only way!

---

### Post by Mostlyharmless42 on 2007-06-29
> **Seisen said:**
> Have you tried opening up IE and see if works?

Wow, it says it's not connected to anything, but IE just worked.  Unfortunately i really only need internet for gaming and what i'm gathering that isn't possible :(.

---

### Post by Seisen on 2007-06-29
It runs through a NAT, that is why it looks like you have no connection. VirtualBox is not actually physically connected to your computer that is why it comes up like it has no internet connection.

---

### Post by Mostlyharmless42 on 2007-06-29
So what would be the best way to run windows games??

---

### Post by Seisen on 2007-06-29
Wine

---

