---
title: "Newbie In Need Of Help!!!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by AaronNewbie on 2007-06-03
Im a total Newbie to Linux I am only used to windows as most people are but after reading an article and looking into Ubuntu I was sold the idea!!! Anyway to my problem:-

Downloaded Ubuntu 7.04
Burned To Disc
Loaded it via Live Cd and had a play decided to go for full install
Installed it!
Starts booting up get the splash screen bar slowly filling up then couple of screen flashes..
Then message appears FAILED TO START X SERVER
Check detailed reason why and says as follows...
FAILED TO LOAD MODULE "NVIDIA" (MODULE DOES NOT EXIST, 0)
NO DRIVERS AVAILABLE

FATAL SERVER ERROR
NO SCREENS FOUND

So after clicking ok I get told X SERVER DISABLED, RESTART GDM WHEN CONFIGURED CORRECTLY
Im then presented with a "DOS" login do put my login and password and presented with the "DOS" flashing cursor with nowhere to turn!!

Please guys your advice will be much appreciated idoit guides only please :) Im running a AMD Duron 1.6 with  1gig ram and Nvidia geforce 6200 AGP graphics if that helps in anyway!

thanks in advance

---

### Post by annda on 2007-06-03
the easiest way to get out of this predicament may sound a little scary but in fact it's easy. you need to edit one configuration file. here's how it goes:

log in with your username and password (you won't see the password, just hit enter). then type

```
sudo nano /etc/X11/xorg.conf
```

find the line that says 'Nvidia' and change it to 'nv' (lowercase!)

ctrl+o to save, ctrl+x to exit the editor.

restart the computer. then you should be able to log in and use the restricted drivers manager (in system>administration) to install the nvidia module.

---

### Post by cotcot on 2007-06-03
If the above post does not help you might try the Alternate install CD

---

### Post by AaronNewbie on 2007-06-03
Still No luck so far trying a reinstall of disc i have see if i get any luck from that. Where can i download the alternate cd from? Whats the difference?

---

### Post by AaronNewbie on 2007-06-03
what do u know!!! A reinstall actually done the trick everything is in working order. Thanks to all for the advice though now to start the real journey to see what Linux can do!!!:)

---

### Post by hyper_ch on 2007-06-03
Please use a descriptive title when posting here in the forums... you know, I tend to think most people starting here a thread would like to get some help with their problem....

---

### Post by patsfan on 2007-06-03
do you have a onboard video card?

---

### Post by patsfan on 2007-06-03
well i need to know how to install this on ubuntu 7.04 and have been working on it for hours .any help would be graetly apperciated.

---

