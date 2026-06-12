---
title: "Black screen after restarting"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Rick789 on 2006-12-27
Ok what I did was installed ubuntu from a live cd it did it then i restarted it loged on the first time then i restarted it then it loads to the load bar finishs it then goes to a black screen what can i do i need help please

---

### Post by Jorge32 on 2006-12-27
In the black screen appears something as "Sync. out of range"?
Do you hear the sound of something like drums?

---

### Post by harrington on 2006-12-27
I am having the same problem and have posted it a few times. I get a black screen also with no signal. I also hear the drums in the backround, just the graphics dont load

---

### Post by Jorge32 on 2006-12-27
Again, I recommend trying to enter the configuration of xserver-xorg, just type ctrl+alt+f4 (If nothing happens try with ctrl+alt+F1)  then enter your username, then your password, and then enter the following:
```
sudo dpkg-reconfigure xserver-xorg
```
this should take you to the configuration of your screen.
what I did was that I changed the range (horizontal and vertical) or try changing to vesa mode at the beginning. 
Then try searching about problems with your video card.
By the way, after finishing the configuration type the following:
```
sudo /etc/init.d/gdm restart
```
to boot to log-in screen

---

### Post by wpshooter on 2006-12-27
First, did you test the integrity of your CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you try installing using the safe video mode parameter ?

---

### Post by harrington on 2006-12-27
I have not yet tried to use the ctrl-alt F4 but I will as soon as I get home from work. Remember also I am just trying a live cd boot its not installed. I cant get to the graphical desktop to try to install

---

### Post by Rick789 on 2006-12-27
um there is still nothing but where can i type in the sudo dpkg thing

---

### Post by wpshooter on 2006-12-27
How much memory does your computer have ?

You MAY need to install using the ALTERNATE CD.

---

### Post by harrington on 2006-12-27
I am fine for ram, I have a gig

---

### Post by Rick789 on 2006-12-27
and the live cd is fine

---

### Post by Rick789 on 2006-12-27
i have a 1gb of ram

---

