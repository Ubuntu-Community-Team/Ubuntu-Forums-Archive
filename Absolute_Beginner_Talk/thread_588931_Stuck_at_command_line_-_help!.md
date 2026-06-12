---
title: "Stuck at command line - help!"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by JGT on 2007-10-23
Please help this beginner!

After I upgraded to 7.10, I am stuck at the command line after reboot.

The last item on the screen is "Runing local boot scripts (/etc/rc.local)"

If I ALT-F2. I can log on at the comand line.

How do I get the GUI back?

Cheers

John

---

### Post by Dr Small on 2007-10-23
Try ALT + F7

---

### Post by dynamethod on 2007-10-23
or type in "startx" without the commers

---

### Post by rudeboyskunk on 2007-10-23
If doing ALT + F7 doesn't get you back to your gui, at command line type:

```
$sudo killall gdm
$gdm
```

---

### Post by SOULRiDER on 2007-10-23
I would also suggest tryying to update. Go to a console (like you did with alt + f2) and type:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Then reboot.

You can also try:
```
sudo /etc/init.d/gdm start
```

Good luck and if you have any issues just ask, dont be affraid.

---

### Post by JGT on 2007-10-23
Thanks. I tried the first two, but I think my configuration is a shambles - I get lots of error messages. I've tried configuring xorg a few times.

I'll try the other suggestions...thanks for your quick responses.

John

---

### Post by Dr Small on 2007-10-23
> **JGT said:**
> Thanks. I tried the first two, but I think my configuration is a shambles - I get lots of error messages. I've tried configuring xorg a few times.

I'll try the other suggestions...thanks for your quick responses.

John
You may have to try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jonathanmotes on 2007-10-23
If none of the above work - especially "startx", you might want to reconfigure your xorg.conf, then try to start X again. Make sure to try everything else first. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``````
startx
```

EDIT: this has worked better for me than "sudo dpkg-reconfigure xserver-xorg". It reconfigures automatically without asking questions.

---

### Post by JGT on 2007-10-23
Hi

I think it's trying to run, as I get a black screen for a short time in lieu of a GUI. There are too many error messages to note, but the last one is something like X10: fatal 10 error 104. There seem to be keyboard and mouse issues too.

I think I've damaged badly it during the upgrade. I'll do a reinstall if all else fails.

Cheers

John

---

### Post by GSF1200S on 2007-10-23
Well definitely try what the last guy said- that command will fix any video/xorg problem.

---

### Post by JGT on 2007-10-24
Tried it before I posted!

---

### Post by jonathanmotes on 2007-10-24
A while back I had to use the boot up parameters "noapic noirdebug" after a Gutsy upgrade in order to boot as well as reconfigure X...Have you tried that? A good tutorial on how to do that is [here]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html").

---

