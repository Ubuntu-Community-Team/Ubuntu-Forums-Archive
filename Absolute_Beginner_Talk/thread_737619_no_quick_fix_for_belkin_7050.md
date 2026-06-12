---
title: "no quick fix for belkin 7050?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by leviticusforjesus on 2008-03-27
i need something i can leave in a file from windows and open ubuntu and retrive it. all the forum stuff i found about it is way beyond my experience considering i cant get online on 8.10 and reach the forum to learn...

---

### Post by cardinals_fan on 2008-03-27
> **leviticusforjesus said:**
> i need something i can leave in a file from windows and open ubuntu and retrive it. all the forum stuff i found about it is way beyond my experience considering i cant get online on 8.10 and reach the forum to learn...
Could you explain your problem in a little more detail?  I can't tell what you want to do.

---

### Post by leviticusforjesus on 2008-03-27
the links i found about my device are for fixing it on edgy eft...
i have 8.10 and xp but my ubuntu wont recognize the belkin software or hardware. i need "ndisgtk" but i have to be online on ubuntu to get it and even if i did get it on xp i have no clue how to make it work on ubuntu

---

### Post by cardinals_fan on 2008-03-27
First off, I think you have 7.10 (8.10 isn't even under development yet).  Second, the guide from Edgy Eft would probably work.  With that said, you should check [this page]("http://opensource.bureau-cornavin.com/belkin/index.html") for tons of good info.  Here is my advice for getting a rt73 Belkin dongle working in Ubuntu:

Start by installing ndiswrapper (ndisgtk if you want more of a gui).  Get ndiswrapper at [http://ftp.osuosl.org/pub/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://ftp.osuosl.org/pub/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb) Double-click it to install.

Find the files rt73.inf and rt73.sys on your Belkin driver CD.  Copy them to your home folder.  Then open a terminal (Accessories -> Terminal).  Type the following, in order (each line is a seperate entry):

```
ndiswrapper -i rt73.inf
ndiswrapper -i rt73.sys
ndiswrapper -m
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo dhcpcd -d wlan0
```
You may need to reboot after this.  Configure the interface through Network Manager.

---

