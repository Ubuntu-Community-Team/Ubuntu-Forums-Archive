---
title: "Doing something wrong, Runs really slow..."
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by SteveJ on 2006-11-27
I am certainly in the right forum because I am very new to Linux (Not so new to computers though). I downloaded the .iso image, burned it, placed it in the drive and restarted the computer.
    I get the option, 'run and install', which I choose. After a while Ubuntu finally comes up - but is is slow. It's not just a little slow, I'm talking start a program, go get some coffee and have dinner, come back and it may be open slow (no exhaderation). I recognize that I am running the operating system from a CD - but this is unusable. 
    I think that by installing it, maybe It will run faster (makes sense). It is so slow that I can't get through the install. After the screen that prompts to partition the drive, it hangs up. I left it for six hours to no avail.
    I know that I must be doing something wrong. I have tried it on three different computers. Two of which are 2.6Ghz processors with fast CD roms and 512M memory. 

    For what it is worth, Ubuntu looks pretty cool and would love to try it - if I could get it to work :).

Thanks

SteveJ

---

### Post by ziffel on 2006-11-27
The same thing happened to me today. What I did was go back and burn the ISO again, at a very slow burn speed (like 4x). Then when I booted to the Live desktop, things worked much better for me. 

I'm not sure if your problem is the same, but I did hang at the same spot you did (disk partitioning). When you first boot the Ubuntu CD, there's a menu choice to check the integrity of the CDR. You might want to try that, or maybe just re-burn the ISO at a slower speed.

---

### Post by taurus on 2006-11-27
Try using the alternate CD to install it on your machine then.  Also, don't forget to burn it at a slower speed like 4x.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by SteveJ on 2006-11-27
I'll give that a try, thanks.

---

### Post by SteveJ on 2006-11-27
Well, tried a new CD, burned it on a new computer, and did a data verification after burning the CD. The problem still exists though - it runs really, really, really slowly. 

Thanks;

---

### Post by 56phil on 2006-11-27
Welcome aboard. It does sounds like you will need to burn and use an alternate install CD. Remember to burn it really slow. Good Luck. Additionally, even fast CD drives are slow in computer terms. Why don't you just install it? That way you can get a feel for Ubuntu.

---

### Post by jdong on 2006-11-27
The LiveCD will run significantly slower than a hard disk install, because:

(1) It's running off a CD-ROM, which reads at a fraction of the speed of even the slowest hard drive.
(2) It's compressed, which means that to access each file your CPU needs to "unzip" it from the CD.
(3) A lot of pre-boot initialization needs to happen, such as detecting your hardware and setting up a temporary user environment
(4) A good chunk of RAM is being used to store temporary files and your temporary profile, which takes away from RAM being used to run the system. If you have less than 384MB RAM, you'll really feel the slowdown caused by this!
(5) Some accelerated video drivers are disabled in order to conserve RAM, so desktop drawing performance will be slower if you have an NVidia card or a recent ATI card.


In other words, install it to get the best experience. Don't make any judgements about the speed of your final Ubuntu system from what you feel on the LiveCD :)



You may have tried other live CD's in the past, and they may have worked better on your system. This certainly can be true. The Ubuntu LiveCD was designed so that it boots and acts as close to the hard disk Ubuntu system as possible, so you can evaluate if your hardware will be supported by Ubuntu or not. Many other LiveCD's (Knoppix, Kanotix, and so many others) are customized and tweaked to be used specifically as a LiveCD, so they'll boot faster and require less RAM. This was not the Ubuntu LiveCD's original design goal.

---

### Post by SteveJ on 2006-11-27
Thanks for this but..

I guess I am missing something. I have read the install instructions and don't see anything about doing an install without first booting Ubuntu. As I stated earlier, if I bott Ubuntu, it runs so slowly that I can't get through the install process. 

I, of coarse, have installed XP. It never has to go to windows. Is there a similar option for Ubuntu?

Thanks

SteveJ

---

### Post by taurus on 2006-11-27
With the alternate CD, you will get into installing it on your computer right away so no need to boot into LiveCD or run from it first before you can install it.  That's what the alternate is for, among other things...

---

### Post by jdong on 2006-11-27
There is an "alternate install CD" where you downloaded your Ubuntu from ([http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/))

This is a textmode installer that requires far less RAM to run and should get you through the installation without a hitch. It's textmode though, but IMO it's every bit as user-friendly and straightforward as a GUI.

Sorry that the graphical LiveCD installer couldn't run on your system :(

---

### Post by IYY on 2006-11-27
It's possible that despite having a good computer, you have a slow CD-ROM drive.

---

### Post by SteveJ on 2006-12-05
I wanted to follow up and let you (or anyone else reading) know that I did download the alternate install. It worked much better. I was even able to install Ubuntu on an old 300Mhz laptop that I had lying around.

Thanks,


SteveJ

---

