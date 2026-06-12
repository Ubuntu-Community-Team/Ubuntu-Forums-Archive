---
title: "PowerPC booting into a black screen"
date: 2011-07-17
forum: Apple Hardware Users
---

### Post by speedydan on 2011-07-17
Hi Guys,

I've just tried installing Ubuntu 10.04 on my powerpc. It installed fine, and booted first time ok, but since restarting it just seems to boot into a black screen. My monitor says 'going to sleep mode' 

I don't think it's hanging on anything, as I can hear sounds if I play around with the keyboard. Could this be something to do with the resolution being too high? If so, can anyone tell me how I go about changing this?

Thanks!

---

### Post by linuxopjemac on 2011-07-17
your Mac model please (link in everymac.com)

---

### Post by speedydan on 2011-07-17
[http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_dual_2.3.html](http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_dual_2.3.html)

---

### Post by linuxopjemac on 2011-07-17
What kind of monitor do you have? Specs please...

You could try to start with this:
```
wget http://mac.linux.be/files/xorg/g5_1.txt
sudo mv g5_1.txt /etc/X11/xorg.conf
```
reboot

---

### Post by speedydan on 2011-07-17
I have an HPW2207 monitor... 22".

Do i type the above when booting?

---

### Post by linuxopjemac on 2011-07-17
You have to type it after booting. Can you switch to a terminal with CTRL-Alt-F1 ?

---

### Post by speedydan on 2011-07-17
I can't seem to switch to that...

I get 'welcome to yaboot version 1.1.13' then boot, with space to type some paramaters i guess.

---

### Post by linuxopjemac on 2011-07-17
then boot into single user mode, at the yaboot prompt type:
```
Linux 1 nosplash
```
or if your Linux has another name, use that name and the "1 nosplash"
then you have to give your root password and then you do what I told you, you can leave out the sudo now as you are root now
after that
CTRL-D to resume booting

---

### Post by speedydan on 2011-07-17
The same thing happens.... I type that in, hit enter and the screen goes into sleep mode :s

---

### Post by rsavage on 2011-07-17
Linuxopjemac, I'm not sure if that works in ubuntu.  It didn't when I tried it a while back.  There is no root user account in ubuntu.
 
Speedydan, you need to do the CTRL-Alt-F1 thing after the system has fully booted.  So way after the yaboot prompt.  This is something that randomly works for me so it may take you a few reboots for it to work.

---

### Post by linuxopjemac on 2011-07-17
ok, didn't know that...oh well, switching tty should work, right.

---

