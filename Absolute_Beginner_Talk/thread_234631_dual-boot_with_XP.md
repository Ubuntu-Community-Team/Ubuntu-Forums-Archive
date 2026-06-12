---
title: "dual-boot with XP"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2006-08-11
hello all, i am looking to this forum to get some help on making my system a dual-boot system. there is LOTS of information on installing Ubuntu alongside an existing XP system, but my problem is different: I already have Ubuntu installed and would like to add XP as a second system.

Is this possible? Or will installing XP clobber Ubuntu? My system is a single HDD system, but it may be possible for me to acquire a second hard drive if necessary.

Thank you so much for your time and help.
bill

PS my version of Ubuntu is 6.06 LTS Dapper Drake

---

### Post by goatflyer on 2006-08-11
Windows has two bad habits:
 1) it WILL overwrite your MBR
 2) it wants to live in the first partition

Your best bet might be to shrink your ubuntu partition, create a new 'backup' partition, copy all your data there, install windows on the first partition, then re-install grub.

As always, do a full backup before attempting this.

---

### Post by c0d4041292 on 2006-08-11
thanks goat-flyer. i was afraid of the XP's desire for complete MBR domination!  :)

---

### Post by confused57 on 2006-08-11
A second hard drive should work in a dualboot:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by fakie_flip on 2006-08-11
dual boot is not the best answer for using xp. i have found many advantages to using vmware server in ubuntu whenever theres a program in xp that i want to use. here are some of the advantages i have found.

1) doing this gives you better security. no need to worry about viruses and other problems while running xp in vmware server. you also have the added protection of having all network traffic going through linux's firewall, iptables when using vmware server.

2) vmware server is not an emulator. if it were, this would cause it to run slow. i have been told by my friend who used vmware server on a 300 mhz cpu, that it was running without being too sluggish.

3) instead of rebooting to use a different operating system, you can use resume in vmware server which is much faster compared to rebooting, and when you are finished using xp in vmware server, all the resources and memory that was allocated to xp is returned back to linux for use.

4) vmware allows you to try many different operating systems and types of linux without burning a single iso. you can also boot live cds without rebooting your computer.

---

### Post by doodsangel on 2006-08-23
Alright, but can you play games in VMWare?

Serious now. Will I be able to play games running MicroSwipe Winbloze XT running VMWare.

I have: 
AMD Sempron 64 2800+
1024MB RAM
NVidia GeForce 6600 PCI-E

Thanks in advance.

---

### Post by MrHorus on 2006-08-23
> **doodsangel said:**
> 
Serious now. Will I be able to play games running MicroSwipe Winbloze XT running VMWare.


No idea, I have never heard of "MicroSwipe Winbloze XT".

However, Windows XP will be able to play games since it;s a proper OS running under a virtual machine.

---

### Post by doodsangel on 2006-08-23
Cool, 

But won't the games have lag. Especially games like NFS Most Wanted as well as FEAR...?

Regards

---

### Post by MrHorus on 2006-08-23
[QUOTE=doodsangel;1412373]
But won't the games have lag. 
/QUOTE]

Obviously - you are running a virtual machine and since you are emulating hardware with software then there will be some degree of slowdown.

As ever Your Mileage May Vary to try it and see - it might be perfectly playable :)

---

### Post by doodsangel on 2006-08-23
Cool,
Thanks.

---

### Post by aeiah on 2006-08-23
games in vmware are often troublesome. vmware cant use direct x accelerated graphics, for a start. thats the main problem. so games that rely on direct x will not play to anything close to acceptable speed because all the graphics processing is done by the software rather than gpu. i dont know how open gl games run, sadly.

you could give vmware a spin and see how it fares for you - there's no harm in trying after all.

your best bet will probably be to shift your ubuntu off the primary partition and install windows there like someone said previously. xp will take over your MBR but it should just be a matter of popping your ubuntu cd in and reinstalling grub once windows has done its thing.

---

