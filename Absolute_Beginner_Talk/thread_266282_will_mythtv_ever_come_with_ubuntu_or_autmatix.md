---
title: "will mythtv ever come with ubuntu or autmatix"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-09-27
i need it to watch tv but im not smart enough to get it working
or does any1 no how to use a tv card in mplayer?

---

### Post by Jussi Kukkonen on 2006-09-27
Myth is already available for ubuntu, but if you just want to watch tv once in a while on your computer, then Myth is not the right choice -- mplayer or something like it is a lot better.

You didn't give any info on your system, so helping is difficult. The first question is: is it a digital or analog TV card? 

These instructions are for a working digital (DVB) TV card:
* You'll need channel information for mplayer: use e.g. the *scan* application from dvb-utils package. see instructions at [http://www.linuxtv.org/wiki/index.php/First_steps_with_a_budget_DVB_card](http://www.linuxtv.org/wiki/index.php/First_steps_with_a_budget_DVB_card)
* start mplayer with
```
mplayer dvb://<channelname>

```

---

### Post by petri on 2006-09-27
With Synaptic you can get kdetv och tvtime if all you want is just watch tv.

There is a Mythtv installation CD which does the installatin kind of automaticly but that one installs on the first harddisk. 
It's called [KnoppMyth]("http://www.mysettopbox.tv/knoppmyth.html").

---

### Post by GonZo1323 on 2006-09-27
thanx think ill use xine or mplayer but everytime i try to install xine i get 
gonzo@gonzo-desktop:~$  apt-get install gxine
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
gonzo@gonzo-desktop:~

---

### Post by Scorpuk on 2006-09-27
try 

```
sudo apt-get install gxine
```

---

### Post by petri on 2006-09-27
You forget sudo
```

sudo aptitude update
sudo aptitude install gxine
```

What is **aptitude**? It's better than apt-get if you want to uninstall, more about it [here]("http://www.psychocats.net/ubuntu/aptitude").

---

### Post by GonZo1323 on 2006-09-27
gonzo@gonzo-desktop:~$ sudo apt-get install gxine
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
gonzo@gonzo-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
gonzo@gonzo-desktop:~$

---

### Post by Daniel15 on 2006-09-27
> thanx think ill use xine or mplayer but everytime i try to install xine i get
...

You need to run that as root. So, put 'sudo ' before the command:
```

sudo apt-get install gxine

```
;)

EDIT: I'm too slow :P
EDIT2: For your new problem, try running:
```

sudo dpkg --configure -a

```

---

### Post by GonZo1323 on 2006-09-27
ok i got everything installed but when i go and click on dbr in gxine it closes down, any1 no how to watch tv in vlc?

---

### Post by PriceChild on 2006-09-27
i'm using a little program called "tvtime" which will use my FlyVideo tuner card fine :)

---

### Post by GonZo1323 on 2006-09-27
tvtime opens and closes im usin a haupagge or however u spell it. i get this error
gonzo@gonzo-desktop:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/gonzo/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

gonzo@gonzo-desktop:~$

---

