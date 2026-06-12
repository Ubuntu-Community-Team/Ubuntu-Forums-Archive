---
title: "Help help i can't do anything..."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-19
i was just palying along with my xorg.conf file and and had uninstalled fglrx ...and the added AIGLX and since i got no rendering i again added fglrx to xorg.conf without installing it and restart X ...now the computer tells me reconfigure my x-server or the graphics can't be loaded what to do i am only able to use terminal that also without entering ubuntu screen just agblack screen full of data 

i am noob helpppppppp:(:(:(:(

---

### Post by pardesi on 2007-06-19
come on i am dying...surely the problem is with my xorg.conf i checked taht when the screen to see why it couldn't start x-server

---

### Post by FleetAdmiral74 on 2007-06-19
Please give the post at least a day before bumping. Plus by replying, you have removed your post from the unanswered post list which lots of people check. Just let us do our work, its kinda busy in these forums.

---

### Post by pardesi on 2007-06-19
sorry i just goofed up so should i repost i am in serious need of assistance

---

### Post by p_quarles on 2007-06-19
Did you say that you never reinstalled fglrx? If you can still access the terminal, you can do that from there.

---

### Post by pardesi on 2007-06-19
yes how do i should i go to the recovery mode or in general to the terminal

---

### Post by p_quarles on 2007-06-19
Any way that works. The command is going to be ```
sudo apt-get install {exact name of driver} 
```

Hope it works.

---

### Post by pardesi on 2007-06-19
so what is the exact name of the driver...only xglrx or something else

---

### Post by lazyart on 2007-06-19
to get to the terminal, just log in after the xserver error message (it should be asking for you login anyway, just in text).

Then reconfigure your xserver```
sudo dpkg reconfigure xserver-xorg
```

---

### Post by pardesi on 2007-06-19
> **p_quarles said:**
> Did you say that you never reinstalled fglrx? If you can still access the terminal, you can do that from there.

you just made my day:guitar::lolflag:=D>=D> (i fall short of words:mrgreen:)

---

### Post by p_quarles on 2007-06-19
> **pardesi said:**
> you just made my day:guitar::lolflag:=D>=D> (i fall short of words:mrgreen:)
You got it working again? Cool.

---

### Post by pardesi on 2007-06-19
well the exact command for any future refrences is

```
sudo aptitude install xorg-driver-fglrx
```
:p

---

