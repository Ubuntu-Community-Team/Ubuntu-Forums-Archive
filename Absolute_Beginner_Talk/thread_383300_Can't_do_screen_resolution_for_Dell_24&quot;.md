---
title: "Can't do screen resolution for Dell 24&quot;"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by rogersausages on 2007-03-13
Hi, I'm brand new to Ubuntu Dapper 

I have partitioned a slaved 120GB seagate for 60GB to run Ubuntu

After an install I noticed that the highest screen resolution attainable was 1280x1024.

I have a Dell 24" with a native resolution of 1920x1200.

I googled a little bit and found this link: [http://www.thestudentroom.co.uk/showthread.php?t=349455]("http://www.thestudentroom.co.uk/showthread.php?t=349455")

I tried the advice adding "1920x1200" to the config file, but nothing changes when I pull up the screen resolution options.  The max I can go is still 1280x1024.

That's not quite the half of it.

I decided to try bumping my res down to 1024x768 for kicks to see if my screen wouldn't look so squatty.  BAD MOVE! Ubuntu took me to a screen saying something to the effect of the selected resolution wouldn't work.  

The problem is I can't just go back and swap back to 1280x1024, i seem to be locked out of the system and have to now deal with a "Dos-like" prompt.  

I have no idea what to do about either of these problems.

Normally I would just reinstall it, and I even looked into that, but now Ubuntu wants to reformat my whole 120GB drive instead of just the partition I made upon install.  I don't really want to lose that other 60GB that I am using for extra storage on Windows.

Any thoughts would help and I greatly appreciate your time.  I'm not too familiar with the terminal but I can follow good directions.

BTW

I have an Nvidia 7600GT video card ( I also did a "get"? command that supposedly downloaded the drivers for the card, but I don't know how to know if it worked or can verify this)

Opteron 1.6 x2 
1GB Ram 
250 GB Western Digital with
120 GB Seagate Slaved to it.

If you need more info I will try to monitor this thread the best I can.  I just signed up this morning though.

---

### Post by chuckyp on 2007-03-13
You can sudo dpkg-reconfigure xserver-xorg to reconfigure X and set the max resolutions in there.  The /etc/X11/xorg.conf is pretty straight forward as far as adding options for higher resolution in the screen section.  Just giving you an alternate route.

To install drivers for your card you just enable the universe repository Administration > Software Sources and sudo apt-get install nvidia-glx from a terminal.  To verify if its working you should get the nvidia logo when loading X or you can glxinfo | grep render in a terminal and it should display a True or Yes value.

---

### Post by rogersausages on 2007-03-15
I don't know if this makes a difference but when booting from the live cd I must boot in safe graphics mode.

---

### Post by hashimoto on 2007-03-15
rogersausages, 
find the technical data of your monitor (resolutions & vertical and horizontal refresh rates). You will need that information.

Open terminal window and run:

```
sudo dpkg-reconfigure xserver-xorg
```

answer the questions (select defaults if in doubt) and when allowed selecct option "advanced" . This will let you fill in all relevant data for the monitor. When done restart X (CTRL-ALT-Backspace)

Alternatively, if you can't run X, reboot the computer to safe mode and run the command above (without the "sudo"). After finishing, reboot.

---

### Post by rogersausages on 2007-03-16
> **hashimoto said:**
> rogersausages, 
find the technical data of your monitor (resolutions & vertical and horizontal refresh rates). You will need that information.

Open terminal window and run:

```
sudo dpkg-reconfigure xserver-xorg
```


Fantastic Hashimoto, I took some doin, but your way worked thanks a ton!:)

---

