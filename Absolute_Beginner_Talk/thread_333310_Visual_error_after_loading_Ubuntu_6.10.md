---
title: "Visual error after loading Ubuntu 6.10"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Niketas on 2007-01-07
Hi everybody! I'm new to the Ubuntu and Linux-based systems. Please, don't use tricky-complicated language, as I'm Russian, though I could speak English pretty well.

Yesterday I tried to install Ubuntu 6.10 on my Intel Celeron 1.7GHz, video GeForce MX400, 768Mb DDR. There were options to install or run Ubuntu live at the boot CD screen, and I tried them, but after a preloader, screen turned to diagonal stripes, and everything was quaking when I was moving the mouse. So I tried the text installator, and generally it was ok, so installation completed successfully.

Then I rebooted, but again, after preloader, the desktop (pale-brown screen) become unstable, diagonally-striped and quaking due to mouse moves (no, it's neither an apocalypsis nor volcano eruption). I guess thres an Ubuntu logo besides the shaking lines, and I even can see the cursor when it's in the upper part of screen, but I can't understand anything else. So, that's the problem. If needed, I could present sreenshots, but they are not at very good quality.

Well, I tried different modes of booting, pressing the Esc at grub loading and choosing Recovery Mode at following menu. But what do I do in this mode? Dunno. I tried to customize smth, entering "sudo dpkg-reconfigure xserver-xorg" in it's command line, but I hadn't have a success. There was such recomendation at [Psychocats]("http://www.psychocats.net/ubuntu/nox"), but it didn't give a result.

If you have any ideas, please, let me know. I've been already searching for similar problems for a 24+ hours and haven't achieved any success yet. I've posted requests at ubuntux.org, forum.ubuntu.ru, forum.ru-board.com, but no result yet. You, guys, seem to be the last hope :-|

---

### Post by Niketas on 2007-01-07
I can't believe there no ideas =(

---

### Post by Niketas on 2007-01-07
If you wanna view screenshots, here they are:

---

### Post by mcduck on 2007-01-07
> **Niketas said:**
> I tried to customize smth, entering "sudo dpkg-reconfigure xserver-xorg" in it's command line, but I hadn't have a success. There was such recomendation at [Psychocats]("http://www.psychocats.net/ubuntu/nox"), but it didn't give a result.
If you run that in recovery mode leave away the 'sudo', and just run 'dpkg-reconfigure xserver-xorg' and answer to the questions it asks.

---

### Post by Niketas on 2007-01-07
Oh, I'm sorry.
Well, somehow that command run successfully that time, but under "it din't give a result" was "it became worse", because after executing command, answering questions and reboot even striped desktop didn't load. Instead of that, the usual text became hyeroglyphs. =(

---

### Post by Alexzzzz on 2007-01-07
> **mcduck said:**
> If you run that in recovery mode leave away the 'sudo', and just run 'dpkg-reconfigure xserver-xorg' and answer to the questions it asks.

Some times this tool don't help. And need corect xorg.conf by hands in manual mode. 
To this need found some information about **vsync and hsync ranges** of type of your monitor. It can do at vendor site. and using this information to change settings in xorg.conf at some lines! :-k

---

### Post by Niketas on 2007-01-08
Well, guys, the problem is solved by now.
I've replaced current videocard by older, Nvidia GeForve2 MX400, and everything goes alright now (except my newer card is out of use in Ubuntu, well, hukarz).
Thanks for participating =)

---

