---
title: "WiFi not detected"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by yatinnaik on 2005-11-24
Hi Ubuntunites,
                          I am new to GNU/Linux and would love working on it for years to come. I have just installed UBUNTU 5.10 on a HP nx6120 Laptop. The problem i am facing is that I cannnot see my WiFi card detected under System>Administration>Networks.

Kindly Help 

Thanks

Yatin Naik

---

### Post by matthewv on 2005-11-24
You may need to install the drivers for it. Try running a search on the forums and the wiki for your laptop, or else run a search on ndiswrapper in the wiki (wiki.ubuntu.com)

---

### Post by aznboi on 2005-11-24
go to the hp site and look for drivers for your laptop. There shuold be some for your wifi card...

---

### Post by danne on 2005-11-24
first, go to the synaptic packet manager and install ndisgtk
then you take the windows driver of your card.
open ndisgtk and select the .inf file of your windows driver...now your card should be working like a charm.
But notice that you have to keep your .inf file on the same location so ubuntu can load it in boot...

bye:cool: :cool:

---

### Post by Brunellus on 2005-11-24
please post the exact model of your wlan adaptor.  

It may be that, as others have noted, you will need to use ndiswrapper to get it running;  it may also be that it is presently not supported at all.

---

