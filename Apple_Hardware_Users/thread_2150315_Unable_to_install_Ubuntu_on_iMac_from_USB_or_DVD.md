---
title: "Unable to install Ubuntu on iMac from USB or DVD"
date: 2013-05-31
forum: Apple Hardware Users
---

### Post by runlevel0 on 2013-05-31
This is an ongoing issue. 

Note that I am not a newbie to neither Ubuntu, Linux nor computers in General.

I have an ageing iMac white Core 2 Duo 17" which I am trying to "Ubuntify" since quite some time ago.
The reason for that is that the portage system in Mac OS X is frustrating to say the least and I haven't been able to write a single line of code on this machine since I bought it.

I have tried installing from the ISO file burning it on DVD and CD. In both cases the image is nicely burnt without an error but it refuses to boot after restart. The disks are not visible when I insert them into a live Mac OS X either.

When I create an USB stick with DD using the procedure described here, [http://askubuntu.com/questions/86/how-do-i-create-an-ubuntu-live-usb-using-a-mac](http://askubuntu.com/questions/86/how-do-i-create-an-ubuntu-live-usb-using-a-mac) 
DD does it's job without an error but when I reinsert the drive I get an error message telling me that it's not bootable and asking me to initialize it. Cool!

When I reboot it is of course not visible either.

The options that I am considering now is to set the f*%#$ iMac ablaze but my actual financial situation doesn't allow me to buy a proper computer (=PC).

Thus my questions: 


[LIST=1]
[*]am I missing something? 
[*]are there already burned versions of the Ubuntu / Kubuntu install CD's for sale? 
[*]is there an alternative installation method? 
[*]from which high do I need to throw the iMac for a perfect and utter destruction? 
[/LIST]

](*,)

---

### Post by GhettoMrBob on 2013-05-31
It's normal that after the DD finished the USB will not be recognized. Just don't do anything and hit cancel.

The other bit that you need to is download and install rEFIt. Once installed you may need to reboot once or twice but you'll get a menu and that USB will be selectable for boot.

---

### Post by runlevel0 on 2013-06-01
Hi, Thanks....
but no luck.
The first thing is that rEFIt's menu not quite clear so I have to choose a random disk (I have 2 external HD's attached too). With one of them I get a "no operating system" message (in Spanish curiously enough, while my whole OS is set to Dutch) and on the only disk were the USB stick seems to react flashing the LED I get a quite clear message stating that the firmware refuses to boot from this drive. 

Cool! 

I will try to build full filesystem using VMware as "LiveCD"... 

:P

---

### Post by GhettoMrBob on 2013-06-01
Out of curiosity, which version of the iso are you using?

As for rEFIt, if at all possible I'd disconnect that external you have just until you get Ubuntu installed. Once you have it installed you'll have a clearer picture in that rEFIt menu of what's what.

---

### Post by runlevel0 on 2013-06-01
Both, 13.4 and 12.04.2 (that's the server) I also tried with the desktop.
MD5sum is checked and OK.

The problem with disconnecting the external is that that's where Ubuntu is supposed to go to, until I can manage to get a new USB CD reader casing and connect the hard disk to the second SATA... bit this will take a while.

I think I will go on and build the system more or less from scratch. Takes time but it's nothing special...

---

