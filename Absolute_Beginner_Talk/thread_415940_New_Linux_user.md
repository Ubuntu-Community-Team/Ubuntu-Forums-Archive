---
title: "New Linux user"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by 00fez on 2007-04-20
Hi. I just installed ubuntu 7.04 today, first time too, and so far I'm liking it, I just have one little problem, actually two.

The first one is I can't get the resolution to go higher than 800x600. I don't have a video card, I have an integrated one, on the ubuntu hardware information it says it is the sis 630/730 pci/agp adapter. I've tried running sudo dpkg-reconfigure -phigh xserver-xorg  in the terminal but 1024x768 is already selected (which is my monitor's max rez, and is what I use in windows). I also tried running a program called envy, but I get this error: "Error: Dependency is not satisfiable: module-assistant"

The second one is a network problem. I get internet just fine if I connect the ethernet cable directly from the cable modem, but if I use my wired router, I don't get any connection at all. My ip is automatic (dhcp), I have a 1mb broadband connection, no need for username or password so I don't really know what is going on. Um... yeah that's pretty much it, other than everything is pretty cool.

If anyone can help me out with any of these issues that would be great. The resolution problem is a bit more important to me since I'm to having at least 1024x768...

Oh yeah, sorry if this has been asked before or if It's just some stupid option somewhere hidden, but I've had this OS for two hours..lol. so yeah bear with me

Thanks!

---

### Post by bwhite82 on 2007-04-20
Hello, you need to install your video driver:

> sudo apt-get install xserver-xorg-video-sis

---

### Post by 00fez on 2007-04-20
I'm afraid that did not work...

fez@fez-desktop:~$ sudo apt-get install xserver-xorg-video-sis
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-sis is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by bwhite82 on 2007-04-20
What computer do you have?

---

### Post by bwhite82 on 2007-04-20
Alright after doing a little research, it seems that Sis chipset graphic adapters are a pain to get correctly configured in Linux. I did find a forum that is solely related to this matter however:

[http://www.winischhofer.eu/sisforum/](http://www.winischhofer.eu/sisforum/)

What might help is to find your laptop in the list, is it a laptop?

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

