---
title: "fatal server error : no screens found"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by SaJellish on 2008-01-16
Hello all,

            After a sabbatical of 2 years I tried to install Linux on my HP dv6500 laptop. I choose Ubuntu cause it made a lot of noise about being user-friendly. It has been a disaster. Let me assure you am a Laptop Linux newbie but have used a lot of distros on my desktop a couple of years ago.
            I tried to use Ubuntu 7.10. It wont boot at all. After some browsing got to know that HP laptops have lots of trouble with 7.10 so was suggested to get back to 7.04. With 7.04 too i got the same problem of ipw3945 and /bin/sh: can't access tty; job control turned off ................. I read through em all and fixed em somehow.........
            I have still been unable to run any live CD but ubuntu 6.06. Its grub does not detect my Vista bootloader so its useless. I finally installed Kubuntu 7.04. It installed fine but have been unable to run the GUI even once. It just stops at the command prompt. 
           startx does not run at all. It says[B]
            Fatal server error : no screens found
            X10 : fatal IO error 104 (connection reset by peer) on xserver ":0-0"[/B]
     I tried to reinstall the xserver-xorg, tinkered with n number of xorg.conf to change its driver settings, DRI, horizontal and vertical refresh rates and what not............ 
            Since I cannot load GUI but I have the command prompt, I keep doing a whole lot of things that people in forums suggested. Reinstalled KDM too...... 
            So this is where I left tinkering with Kubuntu and booted back to windoze.........
            At the end of it all am exhausted and appalled, probably cause I used to play with distros without any trouble. Now just to get one running has been imposs. All I can say is the Shuttleworth's millions sure market the product well but then that's precisely what Gates does for his product. I think I am done with Canonical and it hurts badly...........................cause i really wanted to stick with it

---

### Post by ajmorris on 2008-01-16
hi there,
could you please post the output of the following commands (you can issue them from a TTY1 session (ctrl+alt+F1):

```
sudo lspci
cat /etc/X11/xorg.conf
sudo env
```

Aj

---

### Post by geirha on 2008-01-16
According to [this](http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/), 7.10 should work fairly well on dv6500 ... Perhaps your CD didn't boot because of a bad burn? Try burning at low speed.

As for the Xorg problem on kubuntu 7.04, try setting Driver "vesa" in the Section "Device", either by editing manually or running ```
sudo dpkg-reconfigure xserver-xorg
```

---

