---
title: "x server failed"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by N6e6r6o on 2008-01-16
i need help i tried to install ubuntu on my dell inspiron 1720 and it says my x server failed then i had an epileptic seizure

specs
2.2Ghz intel core 2 duo
3 gb ram
Nvidea graphics card

only used windows so im very new to this stuff so no big scary words please

---

### Post by overdrank on 2008-01-16
> **N6e6r6o said:**
> i need help i tried to install ubuntu on my dell inspiron 1720 and it says my x server failed then i had an epileptic seizure

specs
2.2Ghz intel core 2 duo
3 gb ram
Nvidea graphics card

only used windows so im very new to this stuff so no big scary words please

HI and welcome, Have you tried using safe graphics mode to boot the cd and what is the model of nvidia card? Also have you checked the cd for errors?

---

### Post by N6e6r6o on 2008-01-17
thanks, i dont know how to do the safe graphics...thing and i used a program called wubi i stumbled across

appreciate any help

---

### Post by nikoPSK on 2008-01-17
wubi is basically a beginners testing grounds for ubuntu. :)

---

### Post by N6e6r6o on 2008-01-17
oh...so what does that mean?

---

### Post by Semong on 2008-01-17
Hi. Your best bet for success is to download the Ubuntu iso and burn it to a cd. 

[Ubuntu]("http://www.ubuntu.com/getubuntu/download")

This is what we call a live cd. I'm assuming Windows is still on your system so after you've downloaded that you'll need a program capable of burning an iso onto a cd. I used:

[magiciso]("http://www.magiciso.com/download.htm").

Now when you've done that, insert the cd, restart your computer, go into your bios and change boot priority #1 to your disk drive then save and exit. If all goes well you should be greeted by a menu with all the options you need to successfully install Ubuntu on your system. 
A word of advice: On that menu there should be an option to "Check cd for errors". Do that before anything else. If there are no errors you can then choose the option too "Start Ubuntu in Safe Graphics Mode" and proceed with installation.

Best of luck too you pal. :)

---

### Post by N6e6r6o on 2008-01-17
how do i set the boot priority?

---

### Post by Semong on 2008-01-17
Hrm it's been a while since I've installed but let me see if I remember correctly. I would suggest letting the installer do all the work for you but if you insist on manually configuring your partitions (which I would reccomend you read up on before attempting) set the mountpoint of your biggest primary partition to "/". Also you may want to consider creating another primary partition with about 3 times the mb of your RAM and flag it as /home. This will allow you to completely re-install ubuntu or try out a different distro without losing your /home documents and configuration.

---

### Post by nikoPSK on 2008-01-17
> **N6e6r6o said:**
> how do i set the boot priority?

I wanted to do that too, but I just went ubuntu full time. :)

---

### Post by Semong on 2008-01-17
> **N6e6r6o said:**
> how do i set the boot priority?

lol sorry N6 I was really tired on my last response and misunderstood the question. Restart your computer and press the del key to enter bios. In your bios you should be able to figure it out from there.

---

### Post by N6e6r6o on 2008-01-17
ok i'll give that a shot

---

### Post by Semong on 2008-01-18
How are things coming along for ya dude?

---

### Post by N6e6r6o on 2008-01-24
i cant get the iso to burn so i sent in for a disk from ubuntu too see if that will be easier

---

### Post by N6e6r6o on 2008-02-01
ok so i have my live cd running and i have a few issues first off it won't connect to my wireless network and second it cant detect my sound card. another question i had was is it possible to leave windows on my computer so in case i want to play a game i can just boot vista however disgusting it maybe and use ubuntu the rest of the time. i also have alot of music and videos on here and if i install ubuntu does that delete it or anything. i realize these are probably easy questions but any help would be greatly appreciated

---

