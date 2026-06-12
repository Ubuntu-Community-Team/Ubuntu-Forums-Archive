---
title: "Installing Keyspan Serial to USB converter"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by blakesle on 2007-07-24
I need to install a Keyspan Serial to USB Converter in Feisty 7.04. I have searched these threads for several days and while I can find a few direct references to installing this device none of them are complete. Can someone provide a step by step guide on how to install this device, including the re-compile of the Kernel? 

I am trying to use the device to connect a GPS device to my laptop.

---

### Post by deadgobby on 2007-07-24
Some times check Ubies wiki site. I hope this link helps
[https://help.ubuntu.com/community/BinaryDriverHowto/KeyspanDriver](https://help.ubuntu.com/community/BinaryDriverHowto/KeyspanDriver)

Gobby

---

### Post by blakesle on 2007-07-24
I did check the site but the instructions are very incomplete and when you click on the instructions about compiling the kernel it goes to a non-existant page.

---

### Post by gentoo-user on 2007-08-01
I'm running Ubuntu Fiesty 7.04 and just purchased a keyspan USB Serial Adapter (USA-19HS).
It is plug and play! :)
It can be accessed via ttyUSB0 as per my message log.

Hope that helps.

---

### Post by mmdski on 2007-10-25
Thats strange. I'm reading everwhere that Ubuntu doesn't come with the driver for the adapter. I'm running Gusty Gibbon, and its not coming up the same for me. Does anybody have any ideas?

---

### Post by blakesle on 2007-10-26
I have found the solution to the Keyspan problem. 

Go to this site and follow the instructions. Very simple and quick.

Only thing he did not tell you it to re-boot your system after loading the driver.

[http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/](http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/)

---

### Post by songo on 2007-11-13
denis .deb works fine, but 2.6.22-14-generic kernel doesn't detect my wireless card.

got my wireless back by copying

/lib/firmware/2.6.22-6-generic/ipw2100-1.3-i.fw
/lib/firmware/2.6.22-6-generic/ipw2100-1.3.fw
/lib/firmware/2.6.22-6-generic/ipw2100-1.3-p.fw

to

/lib/firmware/2.6.22-14-generic/ipw2100-1.3-i.fw
/lib/firmware/2.6.22-14-generic/ipw2100-1.3.fw
/lib/firmware/2.6.22-14-generic/ipw2100-1.3-p.fw

---

### Post by dlinuxor on 2008-01-08
Thank you blakesle that solved the problem.

Anyone can point me to a good tutorial about compiling drivers using kernel-headers please?

i think we could solve a lot of problems with this info.

Thanx in advance.:)

---

### Post by squeeb on 2008-02-18
It would now appear that his webserver is down.

It's been down for a while. 

Does anybody have the ability to host the .deb file he created on their own webserver? 

Or does anybody know how he created the driver? 

Regards, 
Squeeb

---

### Post by denislemire on 2008-03-14
The web site hasn't been down... The module, though dated is still posted on-line. Is anyone else having issues accessing the web site?

---

### Post by svnt on 2008-04-11
I can't get to your website (taking too long to respond) but the Google summary has the address for the file to download:
[http://rapidshare.com/files/95027400/keyspan-ubuntu-2.6.22.52.deb.html](http://rapidshare.com/files/95027400/keyspan-ubuntu-2.6.22.52.deb.html)

---

