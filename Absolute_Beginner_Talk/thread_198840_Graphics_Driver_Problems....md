---
title: "Graphics Driver Problems..."
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Jesus_Christ on 2006-06-17
I am currently attempting to install Ubuntu Linux off the LiveCD. However, about half way through it's installations, it tells me I have a "Graphics Driver X" problem or something. It asks if I want to resolve the problem, but I can't go yes or no, because a bunch of randomly assorted code flies all over the screen, preventing me from doing anything.

I am using a NVIDIA GeForce 4 MX440 graphics card.

Any help with this problem would be greatly appreciated.

---

### Post by master5o1 on 2006-06-17
sup JC...lol

you know I cant help :D

---

### Post by Patrick-Ruff on 2006-06-17
wth, that was a really useless and stupid post master5o1.... why not download an alternate cd and do a text based install?

---

### Post by Jesus_Christ on 2006-06-19
How would I go about doing that?

---

### Post by tseliot on 2006-06-20
You can do 2 things:
1) Using the livecd you can choose the Safe Mode as soon as the CD boots (you will see a menu)

2) Or you can download the alternate installer:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/")



Then after you manage to install it, if you have problems such as graphical corruptions, etc. you can set the driver to "vesa"
```
sudo dpkg-reconfigure xserver-xorg
```

and set the driver to "vesa" (press ENTER if you don't know the other answers)

then
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

OR you could just follow my guide to install Nvidia's proprietary driver and make the most of your card:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by Jesus_Christ on 2006-06-22
Neither the live or installation CDs seem to allow me to boot in Safe Mode.

---

### Post by tseliot on 2006-06-22
[QUOTE=Jesus_Christ]Neither the live or installation CDs seem to allow me to boot in Safe Mode.[/QUOTE]
You can select Safe Mode ONLY from the live-cd (as soon as you boot it)


Alternate installation does not have a Safe mode. It doesn't start the Xserver and therefore it should not crash.

Please try those options

---

### Post by Jesus_Christ on 2006-06-22
[QUOTE=tseliot]You can select Safe Mode ONLY from the live-cd (as soon as you boot it)


Alternate installation does not have a Safe mode. It doesn't start the Xserver and therefore it should not crash.

Please try those options[/QUOTE]

I have tried the alternate installation, but I still encounter the very same error. I have not attempted the safe mode as, from what I can see, it does not give me the option when I boot it. I am trying to install Ubuntu 5.10...I probably should have mentioned that.

---

### Post by jimrz on 2006-06-22
[QUOTE=Jesus_Christ]I am currently attempting to install Ubuntu Linux off the LiveCD. However, about half way through it's installations, it tells me I have a "Graphics Driver X" problem or something. It asks if I want to resolve the problem, but I can't go yes or no, because a bunch of randomly assorted code flies all over the screen, preventing me from doing anything.

I am using a NVIDIA GeForce 4 MX440 graphics card.

Any help with this problem would be greatly appreciated.[/QUOTE]

i have 1 machine with the same vid card...installed dapper from the "alternate" with no problem, then installed the nvidia-glx driver using synptic, followed one of the many "how to's" on this subject from these forums. all is working nicely, even getting descent 3D accelleration.

---

### Post by CarpKing on 2006-06-22
[QUOTE=Jesus_Christ]I am trying to install Ubuntu 5.10...[/QUOTE]

I don't remember Breezy having the option to install from the live CD... Are you sure you don't have the install CD instead?

---

### Post by Jesus_Christ on 2006-06-22
Well, what I mean is, I have tried running it off the Live CD and it has come up with the error. I have also tried installing it and it has also reached this error after a while.

Do you think that if I switch the graphics card my monitor is running off I may have hope?

---

### Post by tseliot on 2006-06-23
[QUOTE=Jesus_Christ]I have tried the alternate installation, but I still encounter the very same error.[/QUOTE]
Here's how it should work:
1) you install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

