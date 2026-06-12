---
title: "Is using Virtual Box with XP as good as having a partition?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by jorgecarrillo150990 on 2007-08-25
I am looking forward to Install Gutsy in October and then finally remove my Windows partition, but in my school there are some programs who only work in Windows like the printer network and stuff like that (I have tried Wine and Samba but they havent solved my problem) so i think of virtualizing XP.
Is it any good or should I stay with the WinXP partition?

---

### Post by jordanmthomas on 2007-08-25
It depends on what you're planning to run.  Everything except 3d apps will work fine in a VM.

---

### Post by krazytekn0 on 2007-08-25
I think that the best thing for you to do would be to get help setting up ubuntu to connect to your network and do the other things that you want (this is in terms of speed and ease of use once you're all set up)

The next easiest thing to use would be to stay with a Windows partition, because I have generally found it HARDER to set up a virtual machine on a windows network than it is to set up samba, and the other issue is that when you virtualize you will be losing speed. Now if you have a relatively fast computer with at least 1-2 gigs of RAM this won't be a problem, but on an older computer virtualizing XP can be quite painful.

A good solution would be to leave your drive as it is for right now and try and set up the virtual machine, if it works and does everything you need it to acceptably then you can get rid of the Windows partition.

---

### Post by asmoore82 on 2007-08-25
Virtual Box is ***_[COLOR="Red"]WAY[/COLOR]_*** better* than a partition for so many reasons.

1. Winders can reboot all it wants without interrupting your Real Operating System.
2. Winders is behind the Real Linux Firewall _AND_ VirtualBox's Simulated NAT firewall.
3. Windoze has very little knowledge of the real hareware it's on ...
   I run Virtual Box OSE on my laptop and Ubuntu manages Location profiles and Wireless stuff;
   as far as windows can tell, it's always using a wired Ethernet connection through an AMD NIC.

> **krazytekn0 said:**
> I think that the best thing for you to do would be to get help setting up ubuntu to connect to your network and do the other things that you want (this is in terms of speed and ease of use once you're all set up)

The next easiest thing to use would be to stay with a Windows partition, because I have generally found it HARDER to set up a virtual machine on a windows network than it is to set up samba, and the other issue is that when you virtualize you will be losing speed. **Now if you have a relatively fast computer with at least 1-2 gigs of RAM this won't be a problem**, but on an older computer virtualizing XP can be quite painful.

A good solution would be to leave your drive as it is for right now and try and set up the virtual machine, if it works and does everything you need it to acceptably then you can get rid of the Windows partition.

Little bit of misinformation there, as I said I'm on a laptop which has a 1.8 GHz single core CPU
and only 512 MB of RAM and everything runs smooth.

-------------------------
*if you don't need 3D acceleration.

---

### Post by jorgecarrillo150990 on 2007-08-25
Another thing that is keeping is games, I dont need High-end new games, sometimes yes but a very few, most of time I play Starcraft or AoE2 so what do you think?

---

### Post by asmoore82 on 2007-08-25
> **jorgecarrillo150990 said:**
> Another thing that is keeping is games, I dont need High-end new games, sometimes yes but a very few, most of time I play Starcraft or AoE2 so what do you think?

:D Wine for the games, VirutalBox for your school's picky Apps. :D

---

### Post by aysiu on 2007-08-25
You may not *need* more than 512 MB of RAM, but if you're running a virtual operating system inside another operating system, I'd *recommend* at least 1 GB of RAM.

---

### Post by oilchangeguy on 2007-08-25
> **jorgecarrillo150990 said:**
> I am looking forward to Install Gutsy in October and then finally remove my Windows partition, but in my school there are some programs who only work in Windows like the printer network and stuff like that (I have tried Wine and Samba but they havent solved my problem) so i think of virtualizing XP.
Is it any good or should I stay with the WinXP partition?

the one thing to consider about a vm, is that it does not get to take advantage of the computers full resources. whereas having the os in it's own partition (dual booting) will be able to use the computers full power. so, if you're not concerned about speed, and power. make windows into a vm, otherwise dual boot.

---

### Post by asmoore82 on 2007-08-25
> **aysiu said:**
> You may not *need* more than 512 MB of RAM, but if you're running a virtual operating system inside another operating system, I'd *recommend* at least 1 GB of RAM.

I also have a hunch that performance on this issue will vary widely between VMWare and VirtualBox OSE, but ...
I can run GNOME, Firefox, XMMS, Synaptic, VirtualBox OSE,
Windows XP Pro, MSOffice and not even fill my 512 MB of RAM.

(The Virtualized XP has 192 MB of RAM and a 6 GB C Drive.)

---

### Post by HermanAB on 2007-08-25
I'm using various kinds of virtualization - VMware, Qemu, Xen and BSD Jails.  In general, they all work and all have their strengts and weaknesses, but none are any good for graphical applications.  

A laptop with 1.8GHz processor is plenty good for Virtualbox and XP, but you should install more RAM first.  I recommend at least 1GB, so that you can allocate 512 MB to Virtualbox.

'Hope that helps!

Herman

---

### Post by asmoore82 on 2007-08-25
> **HermanAB said:**
> I'm using various kinds of virtualization - VMware, Qemu, Xen and BSD Jails.  In general, they all work and all have their strengts and weaknesses, but none are any good for graphical applications.  

A laptop with 1.8GHz processor is plenty good for Virtualbox and XP, but you should install more RAM first.  I recommend at least 1GB, so that you can allocate 512 MB to Virtualbox.

'Hope that helps!

Herman

you are confused ... we are unsure what type of hardware the person who started the topic has ..

I have the 1.8 laptop with 512 MB of RAM AND virtualbox already installing/working perfectly.

---

