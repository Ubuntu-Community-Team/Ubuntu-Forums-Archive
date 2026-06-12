---
title: "A few questions..."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by nwkegan on 2007-08-11
Hey, I have a few questions I was hoping you guys and gals could help me out with.

First of all, I was looking at the chmod command with the command man chmod, then I hit the Q button and it said something like Reformatting chmod(1), please wait...

What did I do? Was it bad?

Secondly, I want to have global hotkeys in XMMS. I tried using gconf to go into metacity and change the commands and then their global hotkeys, but it didn't work at all. I found out how to do this through a google search, so what gives?

Thirdly, how do I change a partitions permissions? It says the owner is root and I don't want to log into root to change them, all I want is to be able to edit this partition completely, delete and add files, etc.

Fourth question, after a quick edit, it says my Nvidia drivers are proprietary, I'm guessing there are no supported drivers then?

I think that's it for now, thank you all in advance for your help!

---

### Post by MenZa on 2007-08-11
> **nwkegan said:**
> First of all, I was looking at the chmod command with the command man chmod, then I hit the Q button and it said something like Reformatting chmod(1), please wait...

What did I do? Was it bad?


Oh, not at all. That's merely the manual viewer's way of saying it's translating it from manpage-markup (or whatever; I've never seen the source of one) to the text you read. "Reformatting" is in this case "changing format". Not purging or removing :)


> **nwkegan said:**
> 
Thirdly, how do I change a partitions permissions? It says the owner is root and I don't want to log into root to change them, all I want is to be able to edit this partition completely, delete and add files, etc.


Changing permissions on various partitions can be done in the file /etc/fstab; there's a good guide on how to edit the file [here](http://www.tuxfiles.org/linuxhelp/fstab.html)

> **nwkegan said:**
> 
Fourth question, after a quick edit, it says my Nvidia drivers are proprietary, I'm guessing there are no supported drivers then?


All that means, is that NVIDIA doesn't release the source code for them; there are supported NVIDIA drivers for pretty much all cards. What graphics card do you have?

---

### Post by nwkegan on 2007-08-11
Thanks for your help!

I use a 7900 GT GEforce.

I don't want to screw anything up, after looking at that fstab article, I'm seeing that I have to edit the fourth line for the partition. it currently has defaults, and the other lists the defaults, so instead of "defaults" it should read as follows

rw, suid, dev, exec, auto, user, async

or without the commas?

rw suid dev exec auto user async

or do I have to specify the user?

---

### Post by MenZa on 2007-08-11
You want "rw,suid,dev,exec,auto,user,sync" [I recommend you always use sync]. Just like that; no spaces, commas there. Obviously remove the quotation marks. 

You can install video drivers for your card by installing nvidia-glx-new and linux-restricted-modules-common and linux-restricted-modules-generic. Then change the driver xorg uses to nvidia with sudo dpkg-reconfigure xserver-xorg.

---

### Post by nwkegan on 2007-08-11
I changed the line to that and it didn't change the permissions, I still cannot edit it, even after restarting.


I feel like I'm relying too much on these forums but google is my only other resource and I can't find anything good on this topic through it.

Thanks to anyone who helps in advance.

---

