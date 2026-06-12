---
title: "[SOLVED] How to Install Nvidia Geforce Fx 5200"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-06-19
I have two hard drives, one with Ubuntu, one with Windows XP.  I've recently been using the windows XP, and in that time installed a Geforce Fx 5200.  I decided I wanted to go back to Ubuntu, and booted up the hard drive.  It went normal, then the progress bar stops halfway.  It gives me an error, and can't load the graphical interface.  It then puts me into terminal.  I'm assuming it's a driver problem, that I need to acquire them, but I don't know how.  I searched this forum, and found something about envy.  I put in apt-get install envy
it does it like 50%, then stops, and says it' not there.  Any help on how to get the drivers would be greatly appreciated.  Cheers!

---

### Post by starcraft.man on 2007-06-19
I don't think its a driver issue, I guess probably just have to reconfigure the xorg, it must have got confused.

Boot up into GRUB and select the recovery mode (second option in almost all cases).

Log in then run this command in the console:

```
sudo dpkg-reconfigure xserver-xorg
```

Read all the screens and when in doubt stick with the default/ok. When you get to the graphics section make sure it reads your card (it should) correctly, and make sure your using the "nv" drivers. Also while your at it make sure it reads right screen and resolution. Then reboot with:

```
sudo reboot
```

It should reboot and you can then do as you like. 

Were you using a 3d manager like Beryl before or something else non-standard? Just curious...

---

### Post by steveneddy on 2007-06-19
Lets see - when you boot, boot into the safe mode (no graphics) and after the logon appears, type this in:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the vesa video driver

Go into your desktop GUI and THEN DL Envy scripts and execute them.

Restart - you should have nVidia graphics and drivers now.

How to check the nVidia driver version?

In terminal type

```
cat /proc/driver/nvidia/version

```

Good Luck

---

### Post by Specter043 on 2007-06-19
I don't know what beryl is:confused:

But I am going to try what you suggested, just getting it down so I know what to type when I reboot it into ubuntu.

---

### Post by starcraft.man on 2007-06-19
> **steveneddy said:**
> 
Go into your desktop GUI and THEN DL Envy scripts and execute them.


Good Luck

Wuuups, my bad. I forgot to mention Envy :D.

Go [here]("http://albertomilone.com/nvidia_scripts1.html") for the script. Once your in your GUI. Simple enough to use, install and find it in the Applications > System tool menu. Then just let it install the nvidia drivers and that will be it :).

---

### Post by Specter043 on 2007-06-19
Starcraft, the 1st method you suggested worked, and I am posting this from Ubuntu :D

Thanks for all the help guys.

---

### Post by starcraft.man on 2007-06-19
> **Specter043 said:**
> Starcraft, the 1st method you suggested worked, and I am posting this from Ubuntu :D

Thanks for all the help guys.

Your welcome. Remember to install your drivers if your gonna do anything that requires rendering or you just want things to look/be smoother. Envy does a good job getting it in. And now, I go, have a nice day :).

---

### Post by steveneddy on 2007-06-19
> **starcraft.man said:**
> I don't think its a driver issue, I guess probably just have to reconfigure the xorg, it must have got confused.

Boot up into GRUB and select the recovery mode (second option in almost all cases).

Log in then run this command in the console:

```
sudo dpkg-reconfigure xserver-xorg
```

Read all the screens and when in doubt stick with the default/ok. When you get to the graphics section make sure it reads your card (it should) correctly, and make sure your using the "nv" drivers. Also while your at it make sure it reads right screen and resolution. Then reboot with:

```
sudo reboot
```

It should reboot and you can then do as you like. 

Were you using a 3d manager like Beryl before or something else non-standard? Just curious...

We were posting at the same time and on the same track. Funny.

---

### Post by starcraft.man on 2007-06-19
> **steveneddy said:**
> We were posting at the same time and on the same track. Funny.

Psyonic abilities, I knew it all along :p

---

### Post by Specter043 on 2007-06-19
So, envy worked great, and it's running, but it told me a restricted driver was not in use or something like that.  Is this okay, or should I be worried?

---

### Post by steveneddy on 2007-06-20
Go to 

System --> Administration --> Restricted Drivers Manager 

and check the new nVidia driver you just installed, that is if you haven't done this already in the last 19 hours.

---

### Post by steveneddy on 2007-06-20
> **starcraft.man said:**
> Psyonic abilities, I knew it all along :p

Great minds think alike. 

So....how did YOU get the idea then?

(joking)

:popcorn:

---

