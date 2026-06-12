---
title: "Help with Virtualbox and Migration to Ubuntu"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by inque_54 on 2007-03-28
Hello to everyone,

I'm the IT Manager of our family business and I maintain about 30 computers in our office. We also have 1 main server for data backup and executables.

I've been planning to make the transition over to Ubuntu for the longest time, but my main concern was the programs that our staff uses are programs that are made for Windows which are also critical in day to day operations (MYOB and Customized MS Access program which are stored in the server)

So i tried Virtualbox but the other way around (Host: Winxp, Guest: Ubuntu 6.10) and I've discovered that I couldn't network properly with Virtualbox since it generates it's own ip via NAT or something like that (pardon for the noobness) and I couldn't get on the same network as my Host machine even with Samba is properly configured via SWAT

So to make things short, I need assistance on getting Virtualbox to ride on the internal network of the Host so in theory, I could run executables of the server. But other than that I think I'm good to go on having the mass exodus over to Ubuntu.

Other tips would be also appreciated for making the transition but I think Ubuntu covers almost all basic computer use since it has a lot of open-source alternatives (Open office and etc..)  

Thank you in advance for the replies

---

### Post by hyper_ch on 2007-03-28
Instead of using NAT try to use Bridged Networking. I'm not sure if Virtualbox supports that. If not, try VmWare instead. It's also free to use and it has bridged networking (although this won't work over wifi... briged networking needs ethernet :))

---

### Post by inque_54 on 2007-03-28
Ok! Thank you very much for the tip!!! 

I'll be giving VMware a shot

---

### Post by ahmatti on 2007-03-28
In virtualbox you can do what you need with "host interface networking ". More info from Virtualbox user manual [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf). 

It is good that you are migrating to Ubuntu :)

---

### Post by inque_54 on 2007-03-28
Thanks for the link to the manual!

I've gone through it and I could see the option for Internal Network. I think that would be the simplest option for my case since I wouldn't need the guest to have an internet connection. 

But for some reason, in the GUI of Virtualbox, I can not seem to find that option, it's only up to "host interface networking" only

FYI: I've also posted in their forums about this issue, but no one seems to be replying to it 8(

---

### Post by david_kt on 2007-03-28
A better idea I think is to use dual boot to test it. You could use usb drive for example to boot ubuntu in order not to disturb the current harddisk.

DK

---

### Post by inque_54 on 2007-03-28
@david

Hmm when I boot under Ubuntu, the same will still apply.

I would like to test the network capabilities of a guest os inside Virtualbox to be able to run the executables for MYOB and MS Access. So thats why I'm still using Windows XP to host Ubuntu for the mean time.

---

### Post by david_kt on 2007-03-28
Well, last time I like to use emulator also, until one time I faced the problem with the emulator but I thought it was the problem of the guest operating system.

So, at least for me, sometime it is difficult to differentiate whether the problem lies in the guest operating system, host operating system, or the emulator. That is why I think to do dual boot will save you a lot of trouble like making sure the compatibility of host operating system and the emulator, and the compatibility of guest operating system with the emulator.

Further more, you will need a lot of ram and cpu speed to run emulator. So, end up it will slow down your work as well.

DK

---

### Post by inque_54 on 2007-03-28
Ahhh I see your point Dave. That would be the 2nd phase of my testing as for now I'm strapped for extra PC's that I can use for testing. 

Maybe after I get through the Networking problem inside Virtualbox, I'll go ahead and let one of the machines here migrate and see how it turns out.

Thanks again!

---

### Post by david_kt on 2007-03-29
> **inque_54 said:**
> 

Maybe after I get through the Networking problem inside Virtualbox, I'll go ahead and let one of the machines here migrate and see how it turns out.

Thanks again!

Yes, but I think it is better for you to dual boot first, i.e. when there is problem with linux, what you need to do is just to restart the computer and run wndows to do works. And you could continue trouble shooting again as and when the computer is idle i.e. restart and run linux.

And below link is a good way to do dual boot, to make migration from windows even easier:

[http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761)

Regards,
DK

---

