---
title: "How to get wireless connected automatically when started up?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-25
I have Xubuntu on a different computer. its 7.10, the newest one.

I have ndiswrapper and the driver has installed fine. Wireless is working. 

But..
Every time I start up my computer I have to put in my wireless WEP key. Its 128/64bit hex. 

How do I make it do it automatically when I plug in my usb wireless adapter? 


Thanks,
Tom

---

### Post by Tom--d on 2008-03-25
```
 gksudo gedit /etc/modules
```

How do I get to edit /etc/modules in xubuntu?

---

### Post by plucky on 2008-03-25
```
sudo nano /etc/modules
```

CTRL-O to write to file and CTRL-X to exit

Good Luck

---

### Post by Tom--d on 2008-03-25
Thanks :)

It still doesnt work. 

Basically. When I plug in my usb for wireless the manual config i used to connect to my wireless is not loaded. (Well not enabled) I have saved it and pressed the 'Tick' button. IT connects after. 
When I plug in my usb, the box which is next to the wireless icon is unticked. I have to tick that to enable my connection. 
Can't it do it automatically?

It does it automatically connected on Ubuntu but why not on Xubuntu??

---

