---
title: "gutsy problem - no internet, grub error 17"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-10-30
I have finally got gutsy installed, but at this point it is virtually useless as I have no internet access and can only load the three Os's on my rig via super grub disk. I have tried to get grub working by entering shell commands in terminal, but none seem to work. Master drive has xp and feisty, slave drive is where I have installed gutsy.
Question 1: Anyone know which commands to enter in terminal to ensure all three OS's can boot. Both ubuntu's show a grub error 17, whilst xp shows grub error 13 (I believe xp is still intact despite the grub error 13).
Commands I have tried so far are:
sudo grub
find /boot/grub/stage1 - this brought up 2 possibilities, (hd0,4) and (hd1,2)
root (hd0,4)
setup (hd0)
quit
Also tried 
root (hd1,2)
setup (hd1)
quit
I am unable to get the internet connection going (works fine in fesity and xp). Have an ethernet connection to adsl 512kb/s with a netgear wifi router connected to a computer upstairs. 
Have requested DHCP rather than a static address. When I go into network tools, it is set on feedback loop (or something [am at work at present]). When I set it ethernet, nothing happens, as in, the next time I recheck the settings it has defaulted back to the feedback loop.
Question 2: Does anyone know how to configure this type of connection or know how to get gutsy to recognise that it is linked via ethernet.
Without the internet I can't get anything working properly such as graphics card etc.
Any help would be appreciated in pointing me in the right direction with these issues.
System: AMD 2600+ athlon, 1 gig ddr RAM, ge force 4 mx 4000 vga.

---

### Post by jenhsun on 2007-10-30
> **bumanie said:**
> I have finally got gutsy installed, but at this point it is virtually useless as I have no internet access and can only load the three Os's on my rig via super grub disk. I have tried to get grub working by entering shell commands in terminal, but none seem to work. Master drive has xp and feisty, slave drive is where I have installed gutsy.
Question 1: Anyone know which commands to enter in terminal to ensure all three OS's can boot. Both ubuntu's show a grub error 17, whilst xp shows grub error 13 (I believe xp is still intact despite the grub error 13).
Commands I have tried so far are:
sudo grub
find /boot/grub/stage1 - this brought up 2 possibilities, (hd0,4) and (hd1,2)
root (hd0,4)
setup (hd0)
quit
Also tried 
root (hd1,2)
setup (hd1)
quit
I am unable to get the internet connection going (works fine in fesity and xp). Have an ethernet connection to adsl 512kb/s with a netgear wifi router connected to a computer upstairs. 
Have requested DHCP rather than a static address. When I go into network tools, it is set on feedback loop (or something [am at work at present]). When I set it ethernet, nothing happens, as in, the next time I recheck the settings it has defaulted back to the feedback loop.
Question 2: Does anyone know how to configure this type of connection or know how to get gutsy to recognise that it is linked via ethernet.
Without the internet I can't get anything working properly such as graphics card etc.
Any help would be appreciated in pointing me in the right direction with these issues.
System: AMD 2600+ athlon, 1 gig ddr RAM, ge force 4 mx 4000 vga.

Tough question, here you go
[http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)
[http://www.linuxcompatible.org/Grub_error_17_when_dual_booting_Fedora_5..._t34507.html](http://www.linuxcompatible.org/Grub_error_17_when_dual_booting_Fedora_5..._t34507.html)

You better solve your grub error first.

---

### Post by bumanie on 2007-10-30
Thanks jenhsun, I will give that all a good read. I am sure I will get the grub issue solved in time because I can access everything via the live cd, therefore there must not be too much wrong. It will be a question of finally finding the right commands to set grub straight. In fact I had the same thing happen three times and fixed it by deleting gutsy from the slave drive and then putting in the grub shell commands as  noted. That works but I then loose gutsy. I have read Herman's grub page etc. so far it has not helped with this problem but I will read it again in case I missed something.
Any ideas on the internet problem from what I have described? Would waht you put on the firrst post still be relevant. Very strange all this because whenI installed feisty I had no issues with the internet at all.

---

### Post by jenhsun on 2007-10-30
> **bumanie said:**
> Thanks jenhsun, I will give that all a good read. I am sure I will get the grub issue solved in time because I can access everything via the live cd, therefore there must not be too much wrong. It will be a question of finally finding the right commands to set grub straight. In fact I had the same thing happen three times and fixed it by deleting gutsy from the slave drive and then putting in the grub shell commands as  noted. That works but I then loose gutsy. I have read Herman's grub page etc. so far it has not helped with this problem but I will read it again in case I missed something.
Any ideas on the internet problem from what I have described? Would waht you put on the firrst post still be relevant. Very strange all this because whenI installed feisty I had no issues with the internet at all.

I think Hermanzone tutorial is a good place to see.
I google the webs that come out some people suggests like "remove partition magic in your windows". some suggest "change menu.list...etc".....
You know, I play with grub long time ago and give up. It's because my data is more important than playing the multi-boot environment. 
In the end, I just setup one system (Desktop/Server) for one machine, that's all.
I even do simple mount/unmout to each single harddrive for a single but particular storage preventing OS crash because I did get so many pains on data lost. 

No matter what kind of OS I used, I only trust "Simplicity" is the only way to solve the "Stupidity".

---

### Post by bumanie on 2007-10-30
> **jenhsun said:**
> I think Hermanzone tutorial is a good place to see.
I google the webs that come out some people suggests like "remove partition magic in your windows". some suggest "change menu.list...etc".....
You know, I play with grub long time ago and give up. It's because my data is more important than playing the multi-boot environment. 
In the end, I just setup one system (Desktop/Server) for one machine, that's all.
I even do simple mount/unmout to each single harddrive for a single but particular storage preventing OS crash because I did get so many pains on data lost. 

No matter what kind of OS I used, I only trust "Simplicity" is the only way to solve the "Stupidity".

I have all my important data triple backed up on other media so data loss is not a real problem, sometimes an annoyance, but not a problem.
I am unfortunately one those people who is prepared to have a go at some of these more difficult configurations. I know that sometimes it causes problems, but on the other hand, it is a good way to learn things by making you read, read and read and of course try new things. I think in this situation, there seems to be problems with gutsy - at least from the number of similar problems posted on this forum, would indicate that.
Regarding the internet problem, there seems to be some (but not entire) consensus that ipv6 is causing some of the problems in gutsy and the internet. There is a way to disable or blacklist it. I may try this because as it is, gutsy is basically useless now.
Despite the grub problem, I think there is a good chance that it will be sorted out soon because all the partitions and OS's are in tact (with their data). So it is really just a matter of finding the right code to enter in terminal.

---

### Post by jenhsun on 2007-10-31
> **bumanie said:**
> I have all my important data triple backed up on other media so data loss is not a real problem, sometimes an annoyance, but not a problem.
I am unfortunately one those people who is prepared to have a go at some of these more difficult configurations. I know that sometimes it causes problems, but on the other hand, it is a good way to learn things by making you read, read and read and of course try new things. I think in this situation, there seems to be problems with gutsy - at least from the number of similar problems posted on this forum, would indicate that.
Regarding the internet problem, there seems to be some (but not entire) consensus that ipv6 is causing some of the problems in gutsy and the internet. There is a way to disable or blacklist it. I may try this because as it is, gutsy is basically useless now.
Despite the grub problem, I think there is a good chance that it will be sorted out soon because all the partitions and OS's are in tact (with their data). So it is really just a matter of finding the right code to enter in terminal.

I think it's too early to tell gutsy is useless. Did you find out the problem yet?

Check your hardware
```
lspci | grep Ethernet
```

List your message
```
dmesg | grep pci
```

Show your network
```
ifconfig
```

And post here.

---

