---
title: "ATI Drivers Easy HOWTO"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-11-15
I have read several Howtoes and I think there is an easy way of doing it all. I am using Ubuntu 7.10 on Dell Inspiron 6400 laptop with ati X1400 but it should work for other versions of Ubuntu and any other ati graphic card as well. So here it is:

1. Download the driver (I have used ati-driver-installer-8.42.3-x86.x86_64.run on a 32 bit platform)
Here is a [link]("http://ati.amd.com/support/driver.html").

2. Launch the terminal and write:

```
sudo -s
cd DIRECTORY OF DRIVER
sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```

Now it should be almost like in windows so I you will manage. I think I used Automatic. Note that [COLOR=blue]ati-driver-installer-8.42.3-x86.x86_64.run[/color] is the name of the driver so if yours has a different name use it instead.

[COLOR="Red"][SIZE="4"]YOU MUST REBOOT NOW[/SIZE][/COLOR]

3. In the terminal type:
```
sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv
```
The second command should display ati

4. Now type:
```
glxinfo | grep direct
```
This one should display yes

[SIZE=3]I have used [this]("http://ubuntuforums.org/showthread.php?t=575843&highlight=Ati+dummies") and [this]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html"). As I said I have combined them because it they are much more complicated and/or waste time and you have to fill in you hard drive with extra libraries and programs. The instructions from ati alone  WILL NOT work. You have to do the bits from the "For dummies Howto" ie do what I have writen. It works for me and it should work for you as well.

PS I just found a bug or something. If you get some 1-1.5" lines at the right bottom of your screen go to: System>Administration>Restricted Drivers Manager and disable the ATI driver. Then reboot enable it again (it will install xorg) and reboot again. It should fix it if you ever get it.[/SIZE]

---

### Post by skymera on 2007-11-15
nice little walkthrough,
but ENVY is also very good.

---

### Post by carlosjuero on 2007-11-15
> **KOTAPAKA said:**
> I have read several Howtoes and I think there is an easy way of doing it all. I am using Ubuntu 7.10 on Dell Inspiron 6400 laptop with ati X1400 but it should work for other versions of Ubuntu and any other ati graphic card as well. So here it is:

1. Download the driver (I have used ati-driver-installer-8.42.3-x86.x86_64.run on a 32 bit platform)
Here is a [link]("http://ati.amd.com/support/driver.html").

2. Launch the terminal and write:

```
sudo -s
cd DIRECTORY OF DRIVER
sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```

Now it should be almost like in windows so I you will manage. I think I used Automatic.

[COLOR="Red"][SIZE="4"]YOU MUST REBOOT NOW[/SIZE][/COLOR]

3. In the terminal type:
```
sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv
```
The second command should display ati

4. Now type:
```
glxinfo | grep direct
```
This one should display yes

I have used [this]("http://ubuntuforums.org/showthread.php?t=575843&highlight=Ati+dummies") and [this]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html"). As I said I have combined them because it they are much more complicated and/or waste time and you have to fill in you hard drive with extra libraries and programs. The instructions from ati alone  WILL NOT work. You have to do the bits from the "For dummies Howto" ie do what I have writen. It works for me and it should work for you as well.

PS I just found a bug or something. If you get some 1-1.5" lines at the right bottom of your screen go to: System>Administration>Restricted Drivers Manager and disable the ATI driver. Then reboot enable it again (it will install xorg) and reboot again. It should fix it if you ever get it.
Note: It is advised by ATI to run the aticonfig utility BEFORE rebooting, otherwise you might have display issues.

---

### Post by KOTAPAKA on 2007-11-15
I started using Linux 2 weeks ago and I have been installing programs and drivers everyday ever since. So I sometimes discover a shorter and easier way. I decided to post this one. Hope it helps.

---

### Post by DooX on 2007-11-15
sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv

then reboot,and everything else is same?I will try this manual for install drivers,every other i couldnt go in X after reboot

---

### Post by KOTAPAKA on 2007-11-15
[QUOTE=carlosjuero]Note: It is advised by ATI to run the aticonfig utility BEFORE rebooting, otherwise you might have display issues.[/QUOTE]
Man I think you forget that it is Absolute beginner talk. We are noobs. I am a noob - I just found this way by accident and by experimenting but it works I can perfectly well adjust all my graphics effects on my computer . It will be much easier to configure ati after you have done everything I've said. You just go to: Applications>ATI Catalyst Control Centre which is now there. Besides you wont be able to do aticonfig after the reboot anyway, you have to do the second part as well. That is the problem with ATI's installation manual.

---

### Post by DooX on 2007-11-15
Well something passed good something not...I tried first sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv then reboot,it rebooted ok,but when i try then to type glxinfo | grep direct i get this error Error: couldn't find RGB GLX visual...And also Ati center i cant start,its not finished instalation,it seems like that.
When i do glxinfo i get this:
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None

This means Ati drivers are not used i believe

---

### Post by KOTAPAKA on 2007-11-16
> **DooX said:**
> Well something passed good something not...I tried first sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv then reboot,it rebooted ok,but when i try then to type glxinfo | grep direct i get this error Error: couldn't find RGB GLX visual...And also Ati center i cant start,its not finished instalation,it seems like that.
When i do glxinfo i get this:
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None

This means Ati drivers are not used i believe

You are rebooting at the wrong time. Read what I have written and do EXACTLY the same. I worked for me and I didnt reboot after aticonfig commands.

---

