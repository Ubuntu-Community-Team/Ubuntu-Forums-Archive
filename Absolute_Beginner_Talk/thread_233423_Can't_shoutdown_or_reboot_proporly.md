---
title: "Can't shoutdown or reboot proporly"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by lodbergs on 2006-08-10
Hi

When I try to reboot or shotdown my screen just turns into sleepmode and nothing else happens. What can be the problem?
I have to force a shoutdown on my powersupply but I dont guess thats the way to do it or am I wrong?
I really hope somebody can help :) 

Regards, Søren

---

### Post by coffeecat on 2006-08-10
Rather than just turn the power off, try this in a terminal:

```
sudo shutdown -h now
```

Perhaps once it's shutdown properly, unmounted all devices and updated logs etc, it might let you shutdown/reboot from the GUI. Alternatively you could try (again from a terminal):

```
sudo reboot
```

---

### Post by lodbergs on 2006-08-10
it couldn't do the job :(

---

### Post by coffeecat on 2006-08-10
If the two commands I gave you don't work from a terminal, then there's something seriously wrong with your system. But I don't believe there is. Questions. What exactly did you do? Are you sure you typed the first command **exactly** as I gave it - correct spelling, correct spaces? What, if any, error messages did you get?

After I posted my last post I opened a terminal and typed 'sudo shutdown -h now' (without the quotes) - that is, exactly as I had posted. It prompted me for my password and after I had entered that it did a clean shutdown.

---

### Post by lodbergs on 2006-08-10
Hi again coffecat.

Well, I copied your text into the terminal so I don't think it's mistyped. 
In both cases my screen goes black (like on standby) but I can still hear all my fans are turned on. And all the led's on my pc's front are on as well.

Maybe due to the fact that I have problems rebooting proberly I now have to choose between the following in the startup:

Ubuntu, kernel 2.6.15-26-amd64-generic and
Ubuntu, kernel 2.6.15-23-amd64-generic 

I choose the first one and ubuntu starts up fine - both I can't reboot or shout down properly.

Regards, Søren

---

### Post by coffeecat on 2006-08-10
The choice of two kernels would not have been caused by this rebooting problem. When you first installed, the kernel would have been the 2.6.15-23 one. With a recent update, the 2.6.15-26 kernel would have been installed as well. With a kernel update your /boot/grub/menu.lst is automatically edited so that you have the choice of the newer or older kernel. There are various reasons for having the old one still available, but in most circumstances you simply choose the new one. Since the reboot/shutdown problem occurs with both kernels I doubt whether this has been caused by a kernel upgrade.

From what you say the same thing happens whether you try to shutdown from the GUI or with the terminal shutdown command. And you get no error message in the terminal. I'm afraid I'm out of ideas at the moment. I'll think about this for you and I just hope someone else may post on this thread with some fresh ideas.

---

### Post by lodbergs on 2006-08-10
Well, I don't know if it's the right thing to do, but I think I'll install the 32-bit version instead. Hopefully everything geths a bit easier then and hopfully my system will run smoother. 
I'm a totally newbie so maybe I should make it a bit more easy in the begining and change to the more newbie friendly 32-bit version.

Regards, Søren

---

### Post by coffeecat on 2006-08-10
Best of luck with that. It's always a pity when one decides to reinstall because, in theory, a Linux installation is almost always repairable - unlike a certain other OS from Redmond. :wink: Having said that, it's sometimes quicker and easier just to reinstall - you can spend so much time, effort and heartache tracking down what the problem is.

As far as installing a 32-bit version on a 64-bit machine is concerned I'm with you there. My main desktop machine is a self-build AMD64, nearly a year old now. I chose an AMD mainboard and processor because - well I wanted a change from Intel. I'm not really interested in 64-bit performance. Until a couple of months ago I was running the 64-bit version of SuSE 10.0 on it, but when I changed to Ubuntu I went for the 32-bit version. I couldn't be bothered with all the hassle of missing firefox plugins and other similar issues.

Sorry I couldn't help you fix this one.

Best regards.

---

### Post by lodbergs on 2006-08-10
Hi again coffeecat

Well, I'm VERY happy that you try to help me. I'm now in 32-bit mode and now I can reboot and shutdown without problems. Don't know what did it - but now it's working.

Regards, Søren

---

