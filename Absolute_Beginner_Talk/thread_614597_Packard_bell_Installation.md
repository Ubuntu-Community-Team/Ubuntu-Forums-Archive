---
title: "Packard bell Installation"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Benzaa on 2007-11-16
I’m new to ubuntu and I’ve been trying to install it since last week. I have a Packard bell laptop Easynote with intel centrino processor. 

I can run the live session in my computer (which I like, because it gave an idea of my new future OS), I can even run all the software that is in the disc. The problem begins when I’m going to install the software in my hard disk. I formatted my disk before using the win98 format command. Once I answer all the questions the installation window appears. The process seems to go smoothly until I reach 50% of the installation (sometimes more other less). There the installation window disappears and I can not longer do something in the live session. When I click in any icon there is a message saying that “x” program can not be found.

I have tried with version 7.04, 7.10 and their alternative CD. I have made at least 4 copies of each and it seems that it is not working at all. 

I’ve followed all the recommendations from this forum and still I can not install ubuntu in my computer. 

Do you have any suggestions? I don’t want to return to windows, at least not this fast.

---

### Post by overdrank on 2007-11-16
> **Benzaa said:**
> I’m new to ubuntu and I’ve been trying to install it since last week. I have a Packard bell laptop Easynote with intel centrino processor. 

I can run the live session in my computer (which I like, because it gave an idea of my new future OS), I can even run all the software that is in the disc. The problem begins when I’m going to install the software in my hard disk. I formatted my disk before using the win98 format command. Once I answer all the questions the installation window appears. The process seems to go smoothly until I reach 50% of the installation (sometimes more other less). There the installation window disappears and I can not longer do something in the live session. When I click in any icon there is a message saying that “x” program can not be found.

I have tried with version 7.04, 7.10 and their alternative CD. I have made at least 4 copies of each and it seems that it is not working at all. 

I’ve followed all the recommendations from this forum and still I can not install ubuntu in my computer. 

Do you have any suggestions? I don’t want to return to windows, at least not this fast.

HI and welcome. Do you get any errors using the alternate cd? Or does it just stall?

---

### Post by Benzaa on 2007-11-16
> **overdrank said:**
> HI and welcome. Do you get any errors using the alternate cd? Or does it just stall?

Yes, there is a red screen.

It reads "The installation process has fail, you can chose to repeate the operation or to skip it" , well something like this. This windows apears when it is selecting and installing the software. With the alternative CD it usually fails when it is installing the X-server (something like 6% of the installation process)

I also tried skiping this step but nothing happens, actually the software doesnt reconize the CD. I cannt even take the CD out. I have to reestart.

---

### Post by overdrank on 2007-11-16
> **Benzaa said:**
> Yes, there is a red screen.

It reads "The installation process has fail, you can chose to repeate the operation or to skip it" , well something like this. This windows apears when it is selecting and installing the software. With the alternative CD it usually fails when it is installing the X-server (something like 6% of the installation process)

I also tried skiping this step but nothing happens, actually the software doesnt reconize the CD. I cannt even take the CD out. I have to reestart.

Ok, you stated in your first post that you have tried other advice and did that include burning the cd at the slowest speed and checking the cd for errors and checksum on the cd ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Benzaa on 2007-11-16
I did that
I checked that the sums are right. I burnt the cd at the lowest speed and and check that it was burnt correctly.

Now i dont know what else to do.

---

### Post by AlanRogers on 2007-11-16
I had similar problems on a Packard Bell iMedia desktop. How I got round it was to burn, at the lowest speed, the Alternate ISO for Dapper, and install that as a text install. Then:```
apt-get update && apt-get dist-upgrade
```which updates all packages and dependancies. Next```
sudo cp /etc/apt/sources.list /etc/apt/sources.back
``````
sudo gedit /etc/apt/sources.list
``` and replace every instance of Dapper with Edgy. Save and close before```
apt-get update && apt-get dist-upgrade
```
From there, I configured the machine the way I wanted it, including additional repositories. Periodic upgrades means I'm now at 7.10 without (touches wood) a glitch so far.
 
It's perhaps important to note that I have /home on a separate partition and I back that partition up too. Also, it's not advisable to attempt to upgrade from Dapper to Feisty or Gutsy; one upgrade at a time. It's an ugly way of doing things but, if the Gutsy Alternate CD isn't working for you, I can't suggest anything else, except perhaps more memory?

---

### Post by Benzaa on 2007-11-16
I finally install Ubuntu 7.10 in my laptop, the problem is that I don't know what I did.

Today in the morning I ask an expert to help me to install it. After trying several things he told me that we could try with Devian. I had no objection and we tried that. 

The installation was done from the internet and it was easy and fast. 

After playing for a while with the OS, I decided to give it a try to Ubuntu again. Only this time I was planning to follow the same things that I did with devian. 

I used the alternative CD and I set up the internet connexion and everything run normally. I installed UBUNTU and this is my first post from this OS. 

Could someone explain me what was the problem?

I want to know in case that I want to format the computer again.

---

### Post by overdrank on 2007-11-16
> **Benzaa said:**
> I finally install Ubuntu 7.10 in my laptop, the problem is that I don't know what I did.

Today in the morning I ask an expert to help me to install it. After trying several things he told me that we could try with Devian. I had no objection and we tried that. 

The installation was done from the internet and it was easy and fast. 

After playing for a while with the OS, I decided to give it a try to Ubuntu again. Only this time I was planning to follow the same things that I did with devian. 

I used the alternative CD and I set up the internet connexion and everything run normally. I installed UBUNTU and this is my first post from this OS. 

Could someone explain me what was the problem?

I want to know in case that I want to format the computer again.

Hi and glad to hear you got it going. My thoughts were that when you formatted the disc with win 98 that may have been the issue. If you installed via the internet that would lead me to believe that something maybe wrong with the cd drive that was causing the issue. But good luck!

---

