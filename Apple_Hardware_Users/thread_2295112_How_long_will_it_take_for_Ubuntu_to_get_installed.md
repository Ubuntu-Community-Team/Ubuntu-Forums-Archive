---
title: "How long will it take for Ubuntu to get installed ?"
date: 2015-09-16
forum: Apple Hardware Users
---

### Post by Berthus on 2015-09-16
Hello everyone,

I'm new to Ubuntu so I hope my question doesn't seem too silly but I own a MacBook Air (which runs on OS X and does not have a CD player). I managed to put Ubuntu 14.04.3 on a USB key yesterday and I am now using Ubuntu besides OS X on my laptop. The problem is that I wanted to fully install Ubuntu in order to remove the USB key and be able to customize my new OS (but still keep OS X on the side, for the moment at least).

After partitioning my disk I used the installer to get Ubuntu, but here I am, 10 hours later, my laptop is really warm and noisy (which is unusual) and the installation doesn't seem to be working... I'm on the fourth step (out of seven) but I can't click yet to "Install now", "previous" or do anything else. Am I supposed to wait more ? And how long ? Is there a way to see how far the installation has went ? Is it dangerous for my disk if I stop the process now ? I would really much appreciate your help, because I would like to be able to shut down my computer at some point, before it starts melting.

Thank you in advance, and a good day to you all,

Berthus

---

### Post by howefield on 2015-09-16
Thread moved to the "*Apple Hardware Users*" forum for better support.

---

### Post by Berthus on 2015-09-16
Thanks for that but do you happen to have any idea on how to resolve my problem ? It's been more than 11 hours now... :frown:

---

### Post by Bucky Ball on 2015-09-16
Not an Apple expert but Ubuntu takes between 1/2 hour to an hour to install, depending on machine, and if you've been at it for eleven, something is  wrong, the install has failed as eleven hours is far from normal. Do you have backups of your OSX install?

---

### Post by howefield on 2015-09-16
> **Berthus said:**
> Thanks for that but do you happen to have any idea on how to resolve my problem ? It's been more than 11 hours now... :frown:

I am unfamiliar with Apple hardware so would be reluctant to venture too far other than make sure that your query is in the best place for support. 

I'm not sure what you mean by the 4th step, is this the partitioning screen you are stuck on and if so have you mounted the relevant partitions for install ?

---

### Post by Berthus on 2015-09-16
I'm at the fourth step of the installation program (first it asked me if I wanted to delete OS X or use both, and so on, then when I chose "Install now" it warned me that it could take time and after that my computer started to get warm), I think it is the partitioning screen. What do you mean by mounted the relevant partitions ? I divided my disk into two partitions and ask Ubuntu to install on the new empty one (20 Go). And no I have no backup of OS X whatsoever, but if something goes wrong I know how to reboot entirely my computer, that should set back OS X, right ? ^^'

---

### Post by Berthus on 2015-09-16
Ok, so I tried something else, I stopped the installation, restarted my computer and instead of choosing "Try Ubuntu" I took "Install Ubuntu" but the same problem happened : When it started the installation on the partition, it did nothing. So I'm a bit disappointed because I followed all of the steps found [here ]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx")and I was able to use Ubuntu from the USB stick (I was very happy !) but I cannot install it on my computer (so I'm less happy). Is there ayone who could help me ? Sorry for the double post, and for being a noobie...

Berthus

---

### Post by Bucky Ball on 2015-09-16
[This]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20live%20CD") any help? Seems you need to do some stuff with Boot Camp and install reFIT if you want it. I believe it's easier with reFIT as otherwise you need to go through something more long-winded to boot Ubuntu once installed. I believe ... :)

---

### Post by Berthus on 2015-09-17
Thank you Bucky Ball, but I have no CD player on my computer, so I cannot burn a CD :cry: I tried to use BootCamp to create a partition because everyone on the web was talking about it, but my version doesn't seem to look like the others I found, it doesn't create a partition without installing Windows (and on a USB stick again), and even then it doesn't partition my computer but leaves me with a USB stick that I don't know how to use. But I created a partition with Disk Utility, isn't it the same ? Will it be different if I install rEFIt ? I also thought that maybe I could stick with the USB stick and not have Ubuntu permanently installed, but I would need to be able to customize it (instead of having to configure Ubuntu everytime) and I don't know how to do that (the key is out of reach on the desktop).

Maybe I should try first to improve my computer skills, because obviously I cannot do much on my own...

---

### Post by Bucky Ball on 2015-09-17
Just do what it says but boot from the USB instead. Disk/USB, makes no difference. Let us know how you go.

There is no reason to burn a CD/DVD. All you need is bootable media and you have it. Follow the instructions as precisely as possible. Ask if you get stuck and report your progress.

---

### Post by luciano.x on 2015-09-17
No need to use bootcamp IMO.
I noticed my Mac took like 15 mins before "Installation type". But then it went ok.
You did right by creating the partition using disk utility.
What installation type did you choose? What do you mean by "When it started the installation on the partition, it did nothing."?

If you decide to go rEFIt, I recommend using rEFInd instead.

---

### Post by imattux on 2015-09-20
I'm not sure if any of the people trying to help you are even using Macs, and I'm not quite sure why someone who admits to knowing nothing about Macs would even reply, but if you're still here, I'll try to help.

Before I go on, I have to ask why you want to install Ubuntu or any other Linux for that matter. At the risk of opening myself up to flames, you need to know that Ubuntu (or any other distro) is not like a commercial OS - at all. It doesn't "just work" the way a Mac does. To generalize, it's for people who either have a specific need to run Linux and/or for people who like to tinker and want to learn more about how things work "beneath the hood". 

To extend that analogy, running Linux is like driving a custom-built car. What you've done is taken a custom-built car on a test drive. If you're just bored or you just wanted to check out another OS, then  booting from the USB is the way to go. An intermediate option to  consider is installing it on a Virtual  Machine, either Parallels ($) or  Oracle's Virtual Box (free). This would be like renting or taking a short-term lease on a custom-built car, not too much commitment. Installing it natively is like *buying* a custom-built car. When it breaks - and it will - you have to a.) use the other car (OS X) to get to work and b.) either fix it yourself or get rid of it. There is no taking it to the mechanic. On the plus side - you eventually become a mechanic. But you're gonna have to learn where to get parts and who to ask for help and the car is not going to be reliable to get you to work every day for a while.

I fall into the latter category and if you want to learn, I'm happy to help and you'll be surprised to find that there are at least hundreds of people who've probably done exactly whatever it is you're trying to do and are willing to help you follow in their footsteps. You just have to find them. It's a great community and this is me trying to pay it forward.

I don't want to discourage you, but you need to know that getting it installed, configured and stable is not trivial, especially on a Mac. But you already know that. I really can't believe you waited 10+ hours. NOTHING takes 10 hrs to install. I gotta be honest: If you didn't know that something was seriously wrong after an hour, you might be better off doing something else with your time. But, if you're determined, press on...

Neither Boot Camp nor Refit/Refind are needed. If you can boot into the installer, that's all you'd really need either of those for. The installer crashed on me several times and I have no idea why. I have no idea why it worked the *n*th time and not the times before. That's part of the deal. The minute I got it installed and running I broke it and had to start all over again. I've learned much in the process and I'm happy I committed to doing it, but there have been many frustrating hours in between. So, again, if you want to learn something new, there are people who are happy to help.

I'll see if you're still around before I go on.

---

