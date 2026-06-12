---
title: "Midiman 1x1"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Sovietski1917 on 2008-01-31
Hi there. 

I just switched over to Ubuntu 7.10 from OS X about a month or so ago, and I'm trying to connect my Kurzweil K2600 keyboard to my computer via a midiman 1x1 USB connector, but I've run into a couple problems. I've downloaded the firmware from the synaptic package manager. I typed 'lsusb' into the terminal, and it looks like my computer detects the device. However, the midiman device isn't lighting up, and when I used PD to test the connection, it didn't receive any midi data.
 
Searching for help, I found the following website
[http://ccrma.stanford.edu/planetccrma/software/nanohowtos.html](http://ccrma.stanford.edu/planetccrma/software/nanohowtos.html)
I attempted to download some of the suggest files through the terminal using apt-get, as shown, and  I got a message saying I don't have sufficient privileges, along with the question "Are you root?".
As a noob, I don't know how to respond to that.

---

### Post by warbread on 2008-01-31
It's asking for admin priveledges.  Type:

:~$ **sudo** apt-get install .....

---

