---
title: "[SOLVED] Starting from scratch"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by ockron on 2007-05-18
Hi all.

I have a Dell Precision 220 desktop that I want to use to gain an understanding and of Ubuntu/Kubuntu.

It currently has WindowsXP on it.

I want to remove XP and load Ubuntu (I have the CD) and get it to work.

1. I installed Ubuntu, but every time I start the PC it starts in XP. How do I get rid of XP?
2. I have a wireless network at home and the PC has a wireless network. How do I find out what drivers I need to make it work and get it working on the net?

I am sure that you have answered this a million time, but please be patient.

Thanc

---

### Post by Hobo Joe on 2007-05-18
When you run the live CD and install, click the option that says 'format entire disk'.

That should fix it.

---

### Post by ockron on 2007-05-18
I do not have that option.

I can choose between:
Start or install Ubuntu (the one I chose)
Start Ubuntu in safe graphics mode
Install with driver update CD
Check CD for defects
Memory test

Any ideas?

---

### Post by ahaslam on 2007-05-18
I find that running Darik's Boot and Nuke sorts out all Windows problems...

---

### Post by ockron on 2007-05-18
I have no idea what you are talking about - sorry.:(

---

### Post by RedSquirrel on 2007-05-18
[KillDisk]("http://www.killdisk.com/downloadfree.htm") is a nice program for wiping the hard disk.

---

### Post by AlexenderReez on 2007-05-18
> **ockron said:**
> I do not have that option.

I can choose between:
Start or install Ubuntu (the one I chose)
Start Ubuntu in safe graphics mode
Install with driver update CD
Check CD for defects
Memory test

Any ideas?


yup...that is it...choose start or install ubuntu.. then then.....when it load.........click install icon there......then format entire harddisk....

:)

---

### Post by apunc1 on 2007-05-18
choose the option to start or install ubuntu

after the linux kernel loads you will be in live cd mode. you can try things out and see if you like ubuntu and if everything works with your hardware.

when you are ready to install, double click on the install icon on your desktop. 
that will start the installation of ubuntu onto your hard disk

there will be a disk partitioner called gparted that will enable you to erase your entire hard disk and install ubuntu only, or resize windows and create partitions for ubuntu. the partitioner will take care of things for you, can choose to partition manually and make a /home partition or whatever other partitions you like.


[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by AlexenderReez on 2007-05-18
> **apunc1 said:**
> choose the option to start or install ubuntu

after the linux kernel loads you will be in live cd mode. you can try things out and see if you like ubuntu and if everything works with your hardware.

when you are ready to install, double click on the install icon on your desktop. 
that will start the installation of ubuntu onto your hard disk

there will be a disk partitioner called gparted that will enable you to erase your entire hard disk and install ubuntu only, or resize windows and create partitions for ubuntu. the partitioner will take care of things for you, can choose to partition manually and make a /home partition or whatever other partitions you like.


[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

gparted only appears till edgy...feisty use its own partition manager.....more like suse instation partition manager....but simpler....

---

### Post by ahaslam on 2007-05-18
As already mentioned, your problem can be simply resolved from within the installer (certainly the alternate, I've not used the live). Nuke Boot (as i call it) randomly writes over the entire disc (all partitions, inc. mbr) with 1's & 0's for a set amount of passes, literally giving you a fresh drive. It is OTT for your situation but it will certainly do the trick & it's worth knowing about, google it.

---

### Post by Nekiruhs on 2007-05-18
Man, I liked integrated gParted. I dont like this new tool.

---

### Post by apunc1 on 2007-05-18
> **reez0105 said:**
> gparted only appears till edgy...feisty use its own partition manager.....more like suse instation partition manager....but simpler....


weird. the screenshots on psychocats look like my dapper install with gparted.
well it's the same thing, basically
thanks for the correction

[IMG]http://www.psychocats.net/ubuntu/images/feistydual07.png[/IMG]

this is what the OP wants I think

---

### Post by ockron on 2007-05-19
> **apunc1 said:**
> choose the option to start or install ubuntu

after the linux kernel loads you will be in live cd mode. you can try things out and see if you like ubuntu and if everything works with your hardware.

when you are ready to install, double click on the install icon on your desktop. 
that will start the installation of ubuntu onto your hard disk

there will be a disk partitioner called gparted that will enable you to erase your entire hard disk and install ubuntu only, or resize windows and create partitions for ubuntu. the partitioner will take care of things for you, can choose to partition manually and make a /home partition or whatever other partitions you like.


[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I was sitting here in New Zealand thinking no one can help and then someone gives me the perfect advice!!

Thank you very, very much.

Now I will start the fight to get my wireless network to work....

---

### Post by apunc1 on 2007-05-19
> **ockron said:**
> I was sitting here in New Zealand thinking no one can help and then someone gives me the perfect advice!!

Thank you very, very much.

Now I will start the fight to get my wireless network to work....

you're welcome
you might have some trouble getting the wireless to work, but search here as there have been some  success stories

---

### Post by stalkingwolf on 2007-05-19
If I am reading the OP's post correctly The first thing they need to do is change their start up boot to boot
from CD first.  After that I would suggest they run live before they install, As I have had the Live run and wireless be a breeze to configure.  Then Install and have the wireless be a PITA.  I have also had it be seamless
and go with out a hitch.  I have also had Live run with no problems and install be screwed.

---

### Post by ockron on 2007-05-19
:popcorn:

I'm halfway through the Installation process and relaxing as all seems to go well.
FINGERS CROSSED!!

---

### Post by ockron on 2007-05-19
**Thank you to all that helped this far.**

I just restarted and it looks awesome!!

Can anyone now please help me to get my wireless network working?

---

