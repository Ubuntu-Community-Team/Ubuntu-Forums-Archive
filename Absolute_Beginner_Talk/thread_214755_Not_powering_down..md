---
title: "Not powering down."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-07-13
Hello. I am having a problem. Well it's not really big, but it is just a hassle. I cant reboot/shutdown my laptop without it hanging. I made sure it unmounts filesystem so it's safe to hard reboot. What it does is it shutsdown xserver. Then it brings me to a prompt, which i can type only a few seconds before it starts shutting down. After unmounting and all that, my screen shuts down but my power is still on. Is there any help? I tried googling and i got nothing. I also searched the forums. 

Also, when shutting down, i fail the HAL. I googled that and i'm not sure what to look for. I am new to linux. And im not totally a computer guru. Thanks for the time to read this and the help, if any.

---

### Post by aysiu on 2006-07-13
Does it make any difference if you type the shutdown command? ```
sudo shutdown -h now
```

---

### Post by wildseven on 2006-07-13
nope. I tried both from GUI and terminal
Things i have tried.
sudo reboot --- hangs
sudo shutdown -r t: now --- hangs
sudo shutdown -t: now --- hangs
sudo shutdown t: 1 --- hangs

---

### Post by patrick295767 on 2006-07-13
> **wildseven said:**
> Hello. I am having a problem. Well it's not really big, but it is just a hassle. I cant reboot/shutdown my laptop without it hanging. I made sure it unmounts filesystem so it's safe to hard reboot. What it does is it shutsdown xserver. Then it brings me to a prompt, which i can type only a few seconds before it starts shutting down. After unmounting and all that, my screen shuts down but my power is still on. Is there any help? I tried googling and i got nothing. I also searched the forums. 

Also, when shutting down, i fail the HAL. I googled that and i'm not sure what to look for. I am new to linux. And im not totally a computer guru. Thanks for the time to read this and the help, if any.

```
sudo apt-get -f -y install gdm 
sudo /etc/init.d/gdm start
```

from gdm, you can power down your machien.
If it's not working ... what's ur machine ? laptop ? which model / brand ?

---

### Post by wildseven on 2006-07-13
that doesnt work. Im already in GDM it says. i updated and upgraded everything. tried to ```
 apt-get -f -y gdm 
``` but i already have the latest. 

i have a vaio VGNFS laptop.

---

### Post by wildseven on 2006-07-13
sry for this but..

bump.

---

### Post by adamc55 on 2006-08-19
Yeah, same problem here. Desktop, not a laptop.

---

### Post by catty0320 on 2006-08-19
AFTER you shut down as you have described hold the power button for 10 seconds

---

### Post by adamc55 on 2006-08-19
That's a work-around, not a solution. And since my screen goes black before then, I have no idea whether the system is actually shut down.

---

### Post by Uncle Spellbinder on 2006-08-20
I've had the same problem from the very first day of using Dapper several months ago. Never been able to find a solution. After clicking shut down, it goes through the motions of the shut down and never really does. I always have to hold the power button to get a complete shutdown.

---

### Post by 3rdalbum on 2006-08-20
Are you using the proprietry ATI driver from the repositories?

---

### Post by Uncle Spellbinder on 2006-08-20
> **3rdalbum said:**
> Are you using the proprietry ATI driver from the repositories?

To be honest, I have no idea. I'm not even sure what a "proprietry ATI driver" is. How would I find out? 

*After some Google searches:*  it is apparently a known bug. Possibly kernel related as this problem is appearing in Fedora and Debian

[**Bug #43961 (Launchpad)**](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

[**Bug #6431 (Bugzilla Kernel Tracker)**](http://bugzilla.kernel.org/show_bug.cgi?id=6431)

---

### Post by adamc55 on 2006-08-30
bump. This kills ubuntu for me.

---

### Post by Shay Stephens on 2006-08-30
I have the same problem.  Desktop system that hangs when it get to the part that says "system will now halt" or some such.  I have to push the power button to get it to power off.

What cooks my goose is when I forget and it sits there all night and morning with the monitor burning away brightly hehehe.

I do have some other system instabilities that I am currently blaming on my motherboard.  Once I replace the motherboard, it will be interesting to see if this particular problem goes away.

---

### Post by Uncle Spellbinder on 2006-09-07
This damned bug will not die. Since using Ubuntu, my *_one and only complaint_* is the only way to shut down is to hope all processes ar done after clicking "shut down" and hold the power button for 5 seconds or so. 

Ridiculous.

---

