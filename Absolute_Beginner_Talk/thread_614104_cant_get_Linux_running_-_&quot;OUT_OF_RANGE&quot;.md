---
title: "cant get Linux running - &quot;OUT OF RANGE&quot;?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Syarmin on 2007-11-15
I have downloaded  a copy of Ubuntu Linux and burned the image on a CD. It was all fine when I use it with my ACER laptop, but everytime i tried using it with my desktop (boot from the CD), first it will display the boot display (where i make the selection START OR INSTALL...., and at the bottom of the screen there are some F1 to F6 selections (F4 is VGA, 600*400... etc etc). 
When i hit enter at that screen, it will show :-
1. first = "Loading Kernel 100%"
2. second = the running bar as it is starting up
3. then, comes the "OUT OF RANGE" message, and my screen will just go blank...
so, what can i do? i have selected the F4 and change from VGA to 1024*768*32... still nothing... and i have also selected "start with safe graphics mode"... still nothing....
your assistance are very much appreciated.

---

### Post by Tyke91 on 2007-11-15
if you want to install ubuntu, you might be able to use the alternate CD, it would install and then you could configure your settings afterwards.

---

### Post by overdrank on 2007-11-15
> **Syarmin said:**
> I have downloaded  a copy of Ubuntu Linux and burned the image on a CD. It was all fine when I use it with my ACER laptop, but everytime i tried using it with my desktop (boot from the CD), first it will display the boot display (where i make the selection START OR INSTALL...., and at the bottom of the screen there are some F1 to F6 selections (F4 is VGA, 600*400... etc etc). 
When i hit enter at that screen, it will show :-
1. first = "Loading Kernel 100%"
2. second = the running bar as it is starting up
3. then, comes the "OUT OF RANGE" message, and my screen will just go blank...
so, what can i do? i have selected the F4 and change from VGA to 1024*768*32... still nothing... and i have also selected "start with safe graphics mode"... still nothing....
your assistance are very much appreciated.

HI and welcome, what is the model of the graphics card?

---

### Post by Syarmin on 2007-11-16
my graphics card is NVIDIA RIVA TNT2 MODEL 64/MODEL 64 PRO.
TQ.

---

### Post by FuturePilot on 2007-11-16
When you first boot the CD and you see the initial menu come up with all the options on it, press F5 for more options and a line of some text should appear. Try removing "quiet splash" from that line. Then hit Enter and see if it boots.

---

### Post by Syarmin on 2007-11-16
F5 is 'ACCESSIBILITY'.
F6 is 'OTHER OPTIONS'
when i press F6, then some boot commands came out, changing respectively to the boot up selection (example : "Start or Install Ubuntu", or "start Ubuntu is safe graphics Mode", or "install with driver update CD" or "OEM install").
i can see the words "quiet splash" in some of the selections, but how do i go and remove that? when i hit enter and select "start or install Ubuntu", it gives a message "you're leaving the boot display and enter test message, agree or cancel?" then i click OK, it'll just give a blank display, with only "BOOT:" at top left corner.
what next? can i type something at the BOOT: cursor?

---

### Post by overdrank on 2007-11-16
> **Syarmin said:**
> F5 is 'ACCESSIBILITY'.
F6 is 'OTHER OPTIONS'
when i press F6, then some boot commands came out, changing respectively to the boot up selection (example : "Start or Install Ubuntu", or "start Ubuntu is safe graphics Mode", or "install with driver update CD" or "OEM install").
i can see the words "quiet splash" in some of the selections, but how do i go and remove that? when i hit enter and select "start or install Ubuntu", it gives a message "you're leaving the boot display and enter test message, agree or cancel?" then i click OK, it'll just give a blank display, with only "BOOT:" at top left corner.
what next? can i type something at the BOOT: cursor?

Hi and when you see the quiet splash like FuturePilot mention then use the arrow keys to get past -- and then the backspace key to delete the quite splash that will enable you to see any errors.

---

### Post by Syarmin on 2007-11-16
Hi.
I've tried deleting "quiet splash".
result is still the same. it starts with all these texts. i think most of the test are indicated with "[OK]".
then after all that, it displays the message "OUT OF RANGE" in a red box, with a grey background display, for about 2 second, and the screen goes blank, meanwhile my CD-ROM where I boot the CD is still running, and after a while, nothing.
the only difference this steps do are, instead of giving the display where it shows the running bar, it shows all the texts of the windows starting.

emmm.... BTW my desktop are pentium4 1.4Ghz, RAM 256 MB of rdram. what else can i do?

---

### Post by 11hjpphty76lkjj on 2007-11-16
I could be wrong but this sounds like a monitor display message.  

I'm thinking you installing using the alternative cd as suggested you can then more finely tune the display settings to work with your system.

Edit:  Go here [http://www.ubuntulinux.org/getubuntu/download](http://www.ubuntulinux.org/getubuntu/download) and click the checkbox for next to: "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

---

### Post by Syarmin on 2007-11-16
if i checked the box for "Alternate Desktop CD", it will used a text-based installer. does this means that instead of running Linux through the boot CD, i'll be installing Linux onto the computer?
thanks.

---

### Post by 11hjpphty76lkjj on 2007-11-16
Yes.  Although if you only want to try it would that could be a problem.  But really you should have a problem..what video card and monitor do you have?

---

### Post by Syarmin on 2007-11-16
video card = Nvidia Riva TNT2 model 64
monitor = a normal looking CRT monitor 15", usually the resolution are set at 800 * 600

---

### Post by Charco on 2007-12-04
I have the exact same problem with gusty. My computer works with the Dapper liveCD flawlessly. I do not understand this at all.

---

### Post by discoade on 2007-12-04
I would say its definatly a monitor problem!  its probably the refresh rate is to high or the resolution. when i first installed ubuntu it booted up as  1280x1024 with a refresh rate of 85hz! thats without the nvidea drivers installed! luckily my monitor could handle it! but an older crt may not!

sounds like a monitor message! does your monitor go into stand by a few seconds after the message appears?

---

### Post by 11hjpphty76lkjj on 2007-12-05
It's definitely a monitor error. Although it is a configuration problem with Ubuntu.  You just need to reconfigure x using;

```
sudo dpkg-reconfigure xserver-xorg
```

and it should work thereafter.  

Course to get to a terminal you press Control-Alt-F1 (or f2, etc.)

Login.

Run the command:

```
sudo dpkg-reconfigure xserver-xorg
```

then

```
sudo /etc/init.d/gdm restart 
```

(or sudo /etc/init.d/kdm restart if using kde/kubuntu)

Of course during the dpkg-reconfigure you want to select the options that work best with your system.  and I always configure the monitor using the 'medium' option, which will let you select the resolution and refresh rate in a method that makes sense to me.  Easy might work better for others.

Hope this helps!

A

---

