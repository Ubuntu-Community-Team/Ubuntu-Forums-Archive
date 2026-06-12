---
title: "Need help installing Ubuntu 7.04 on an Acer Travelmate 2200"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by revolutionaction on 2007-07-18
I've scoured the internet and the ubuntu irc for help with this and havn't gotten any closer to a solution, I'm wondering if you guys can help.

I put the live-cd in the drive and it loads up normal giving me the options on what I want to do, I go to run live cd & install and starts loading up as usual. Next thing that happens is the Desktop background for ubuntu shows up, with the reddish tannish colour, and then a mouse icon shows up, then it freezes and does nothing else. I've looked up all the issues surrounding my laptop and still havn't gotten past this problem! Any help with this would be wonderful! I'm extreamly anxious to get ubuntu running so I can play around with it and eventually switch over from windows xp.

This is the only support I can find for my type of laptop: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer")

---

### Post by AlexenderReez on 2007-07-18
how long did you wait for it?maybe it takes time to load driver configuration....my machine having problem long loading in live cd,but after install it.that particular solve....

---

### Post by Immolatus on 2007-07-18
just a thought. Try unplugging everything unnecessary for operation: mouse, any pcmcia cards (including a wireless card) printer, cellphone, anything. 

I just had a problem with udev hang booting fedora 7 that was caused by incompatibility with my pcmcia sound card. Just to rule it out.

---

### Post by revolutionaction on 2007-07-18
I have nothing else plugged in, and I've waited atleast 2 hours at install, still nothing!!

damnn

---

### Post by jimrz on 2007-07-18
> **revolutionaction said:**
> I have nothing else plugged in, and I've waited atleast 2 hours at install, still nothing!!

damnn

may be an issue with your vid card. try selecting the boot option to use the "vesa" driver and see if it helps. you can always get the card straightened out after install, if this works

---

