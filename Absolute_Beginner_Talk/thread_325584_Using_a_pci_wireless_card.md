---
title: "Using a pci wireless card"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2006-12-26
hey all finally got ubuntu working, though barely. I have to connect to the internet so I can downlaod the Nvidia drivers but to do that I need to get my wireless pci card working how do I do this?

---

### Post by obrient on 2006-12-26
Well the first thing you might want to do is see if you have a wireless card that works natively on Ubuntu. I found this some where in the forums or wiki. Can't find the page now though. Basically if you can find out this information first that will help. 

If your card isn't there you might also want to compare the chipset in the card to others that are on the list. To do this open the terminal and run lspci (list all PCI devices). Look for your card in the output.

Then if you can't find a driver that works on this you will have to install NDISWrapper which will wrap the windows drivers inside of something that Linux will understand.

Three things that work well to get this stuff working are Network Manager, NDISWrapper, and NDIS-GTK
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Hope this helps some I just battled with this today or is it yesterday already?

---

### Post by mojoman on 2006-12-26
> **Griffongob said:**
> hey all finally got ubuntu working, though barely. I have to connect to the internet so I can downlaod the Nvidia drivers but to do that I need to get my wireless pci card working how do I do this?

Try to give a little more info on your problem. My experience is that the more specific your question is, the higher chance of someone on the forum having an answer.

Is your card detected at all? What is the output in the terminal from ipconfig and iwconfig? 

Best regards
/Mojoman

---

### Post by Griffongob on 2006-12-26
haha thanks I'm gonna try the thing is that it sees that there is something from linksys connected to a pci slot but it cant seem to see its a wireless card

---

### Post by Griffongob on 2006-12-26
ok I found a linux driver for my wireless card at [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
so how do I install it in Ubuntu? and do I still need Ndiswrapper?

---

### Post by Azakus on 2006-12-26
No you don't need ndiswrapper. Those are the source codes for a linux driver for your card. You take the source code and compile the driver for it.

---

### Post by Griffongob on 2006-12-26
ok I'm gonna try it lets hope this works! Crosses fingers......

---

### Post by Griffongob on 2006-12-26
ok I have no clue how to compile...help...

---

### Post by Azakus on 2006-12-26
Which card do you have?
What version of Ubuntu?
32bit or 64bit?

---

### Post by Griffongob on 2006-12-26
I have WMP54G the latest version and I am using 5.10 Ubuntu..i know its old but thats the install disk my friend gave me

---

### Post by Griffongob on 2006-12-26
also is 5.10 using kernal 2.4 or 2.6?

---

### Post by Griffongob on 2006-12-26
ok so it runs 2.6 now how do I compile it does anyone know?

---

