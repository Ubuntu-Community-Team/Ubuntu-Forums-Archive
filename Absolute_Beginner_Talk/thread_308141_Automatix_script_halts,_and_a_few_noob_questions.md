---
title: "Automatix script halts, and a few noob questions"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by ziffel on 2006-11-27
Hi, absolutely raw Linux/Ubuntu noob here. 

I installed Edgy today, longtime Windows user. I've had no problems until I ran the Automatix script. It got to about 95% done, and then when it got to Beagle it halts and just says "Please Wait...", even though at the bottom of the terminal window, it says "FINISHED". Nothing has happened for about 35 minutes, and if I click Cancel, it says to wait till the script finishes.

My other idiotic noob questions have to do with app installs, locations, and partitions.

When I installed edgy, I did a 3gb root partition, a 512 mb swap (to match my ram), and the rest of the drive to an extended partition (about 180GB)

How do I know where things are being installed? is it going to try and cram everything into the 3gb root? or will it "know" to put new apps in the big partition? I guess I'm referring to the app manager. Like, for example, I downloaded the Celestia space sim, and it installed it, but I have no idea where to.

Also, when I went to install Nvidia video drivers, it said I needed to be logged in as 'root', and I don't know how to do that. :oops: 

thanks for any help!=D>

---

### Post by Madpilot on 2006-11-27
> **ziffel said:**
> Hi, absolutely raw Linux/Ubuntu noob here. 

I installed Edgy today, longtime Windows user. I've had no problems until I ran the Automatix script. It got to about 95% done, and then when it got to Beagle it halts and just says "Please Wait...", even though at the bottom of the terminal window, it says "FINISHED". Nothing has happened for about 35 minutes, and if I click Cancel, it says to wait till the script finishes.


Automatix is best avoided, for the reasons you've just run into: inadequate error handling, and other issues.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) has most of the stuff you'll need that Automatix tries to do for you about playing mp3/Flash/Java/etc.

> 
My other idiotic noob questions have to do with app installs, locations, and partitions.

When I installed edgy, I did a 3gb root partition, a 512 mb swap (to match my ram), and the rest of the drive to an extended partition (about 180GB)

How do I know where things are being installed? is it going to try and cram everything into the 3gb root? or will it "know" to put new apps in the big partition? I guess I'm referring to the app manager. Like, for example, I downloaded the Celestia space sim, and it installed it, but I have no idea where to.


3Gb really isn't big enough; all the install stuff in Linux is designed to go into the root partition, not /home. Before you get too far into Ubuntu, you should probably re-partition & re-install with a 5-10Gb root partition - if you've got a 180Gb /home, you've got lots of space to give more to /root.

> 
Also, when I went to install Nvidia video drivers, it said I needed to be logged in as 'root', and I don't know how to do that. :oops: 


[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) should work for you; I run an ATI graphics card myself so can't really help further w/ Nvidia issues.

Hope this helps - welcome to Ubuntu!

---

### Post by drphilngood on 2006-11-27
[Here´s]("http://www.psychocats.net/ubuntu/index") another resource that you´ll find helpful.

---

### Post by ziffel on 2006-11-27
Thanks for the help. Madpilot, I'll start over tomorrow, and extend the root partition. Would it make sense to go as big as 20GB? or would 10gb be enough?

drphilngood, thanks for the excellent link, I'll read over that tonight.

zif

---

### Post by arnieboy on 2006-11-28
> **Madpilot said:**
> Automatix is best avoided, for the reasons you've just run into: inadequate error handling, and other issues.

Advice such as above is best avoided because the person giving the advice obviously is too ignorant to know that the issue in this case was because of apt (Automatix2 is just a layer).

---

### Post by arnieboy on 2006-11-28
> **ziffel said:**
> Hi, absolutely raw Linux/Ubuntu noob here. 

I installed Edgy today, longtime Windows user. I've had no problems until I ran the Automatix script. It got to about 95% done, and then when it got to Beagle it halts and just says "Please Wait...", even though at the bottom of the terminal window, it says "FINISHED". Nothing has happened for about 35 minutes, and if I click Cancel, it says to wait till the script finishes.
did you by any chance have xchat2 running while running AX2?

---

