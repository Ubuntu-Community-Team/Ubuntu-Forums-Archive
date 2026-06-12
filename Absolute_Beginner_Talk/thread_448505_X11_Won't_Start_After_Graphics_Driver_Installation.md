---
title: "X11 Won't Start After Graphics Driver Installation"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-05-19
Hi everyone, I have posted about this problems a [couple of days ago]("http://ubuntuforums.org/showthread.php?p=2667873#post2667873"), but have realized that I probably posted in the wrong category. And since I am very much a beginner with Linux I thought this might be a better place to start.

I have a question regarding my 7950gt geForce Graphics card, it seems like it is hard to get working in any Linux Distro. A couple of month ago I tried to install openSUSE 10.2 but because the driver from nVidia at the time didn't support 7950gt properly I decided to wait and now as far as I understand they have released a new version of their driver.

I then decided to move away from openSUSE mainly because my dad did as well and try out Ubuntu. I had everything installed and it all seemed good until ubuntu asked me, if I wanted to install the driver for my nVidia Graphics card because Ubuntu had noticed that it supported some 3D things and to get the most out of it, it was recommended that I installed the driver. Ok I thought this sounded good because before I messed around with trying to install it manually and it did'nt work out for me, so hopefully Ubuntu could do the job. But when it was installed and I restarted the System i got the following screen:
[[IMG]http://img234.imageshack.us/img234/2235/01startupdo8.th.jpg[/IMG]](http://img234.imageshack.us/my.php?image=01startupdo8.jpg)

When I say no to view the eserver outpu (which I by the way understand nothing of) I get the following screen sying that X has been disabled:
[[IMG]http://img66.imageshack.us/img66/7339/02xdisabledzl0.th.jpg[/IMG]](http://img66.imageshack.us/my.php?image=02xdisabledzl0.jpg)

I now have no idea how to configure it, when I click ok I just get back to a normal command prompt:
[[IMG]http://img218.imageshack.us/img218/4108/03cmdpromptps7.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=03cmdpromptps7.jpg)

And from my experiences on SUSE I knew that the command startx would try and run the X Server, but when I do so, I get a familiar screen which I remember from my SUSE time and it looks something like this (and yes I have checked all my power cables and everything)
[[IMG]http://img230.imageshack.us/img230/535/04startxrg2.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=04startxrg2.jpg)

I hope someone will be able to help as I can't get anywhere, and is pretty much stuck.

Thanks

---

### Post by Najand on 2007-05-19
First login in the console and stop annoying X session by:
```

sudo /etc/init.d/gdm stop

```
Then try to backup your xorg.conf file
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken

```
Then edit /etc/X11/xorg.conf
```

sudo nano /etc/X11/xorg.conf

```
If you are familiar with "vi" or other editors you may use them also.
FInd the this line:
```

Section "Device"
        Identifier      "NVIDIA" # might be also a different name
[COLOR="Red"]        Driver          "nvidia"[/COLOR]

```
change it to:
```

Section "Device"
        Identifier      "NVIDIA" # might be also a different name
[COLOR="Blue"]        Driver          "nv"[/COLOR]

```
save using Ctrl+X and then pushing Y and then reboot your system.... See if it works or not.

---

### Post by kasperbs on 2007-05-19
Thank you very much that worked like charm. Do you have any suggestions to how I might try and install my driver or should I just try one of the methods described here on Ubuntu forums

---

### Post by Najand on 2007-05-21
Hmm, NVIDIA usually works better than ATI, however sometimes, there are some stuff you need to know, which can be found here on the forum...

---

