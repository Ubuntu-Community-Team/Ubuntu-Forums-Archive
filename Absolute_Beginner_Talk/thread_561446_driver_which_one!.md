---
title: "driver? which one!?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-09-27
right since my other post is being ignored im gonna try a different one.

well im running an nvidia, enough info.

i can choose 2 drivers,

NV and NVIDIA

NV works without FrameBuffer and has a window manager
NVIDIA works with FrameBuffer but dosent..

which is best to choose?

im swapping back to NV in a sec

---

### Post by CaptainInsaneO on 2007-09-27
Have you actually INSTALLED any drivers? If you haven't, the nvidia driver won't work and you'll have to use nv until you install the proprietary drivers.

---

### Post by skymera on 2007-09-27
yes restricted drvier manager.

---

### Post by Steveway on 2007-09-27
What Nvidia-card do you have?
NV is an opensource driver and has no 3D-support.
Nvidia is the official driver from Nvidia and has all whistles and bells, but there are different ones.
nvidia-glx-new for the fx series cards and later.
nvidia-glx for some pre-fx cards.
and nvidia-glx-legacy for pretty old nvidia-cards.

---

### Post by CaptainInsaneO on 2007-09-27
What window manager are you using? (i.e. metacity, compiz, emerald, etc.)

---

### Post by skymera on 2007-09-27
compiz fusion
i want at least some windows decorator no borders L:(

its a 7900GS 512mb

---

### Post by CaptainInsaneO on 2007-09-27
Have you tried the Alt+F2 and then typing compiz --replace? It's a simple oversight that many people miss. Even I have, and that always fixes it for me.

---

### Post by skymera on 2007-09-27
yes it works.
but i have no borders?
no corss no minimise

---

### Post by Steveway on 2007-09-27
You should use the nvidia-glx-new driver (found in Synaptic).
If you have no Windows-border while using Compiz then check if you have Emerald installed, if yes then do a:
emerald --replace
(Not sure if --replace is needed for emerald)
And give us more information, we can't help you if you don't tell us what is going on.

---

### Post by CaptainInsaneO on 2007-09-27
Basically what he's saying is he has no bar on the top (where the minimize, maximize, and close buttons are). I understand completely what he's saying, it's just an odd problem that I haven't heard much about regarding Compiz Fusion.

skymera, Steveway's advice was pretty, try the driver he recommended, and also try emerald --replace. If it kills your compiz, do a compiz --replace and then do emerald (by itself) and see if that does anything. I can help you more when I get home tonight (I'm at work) and can show you an example of my xorg.conf so you can get an idea of what it should look like to properly run CF. (There's certain things you have to add.)

---

### Post by davedumas0 on 2007-09-27
hi this is kinda off topic but i need to install NVIDIA-Linux-x86-100.14.19-pkg1.run file but i dont know how to open it let alone install and do i need a matching kernel ?i have an geforce 8800 gts SC everything is working fine compiz,emerald,etc but the black windows thing

---

### Post by skymera on 2007-09-27
yeah off topic.
make your own :lol:

well...i sorta ended the service for GDM logon and ermmm no gui at logon...or at all.
is it easy to get it back?

if it aint i might pack my bags and go to windows, or fresh install

---

### Post by CaptainInsaneO on 2007-09-27
> **davedumas0 said:**
> hi this is kinda off topic but i need to install NVIDIA-Linux-x86-100.14.19-pkg1.run file but i dont know how to open it let alone install and do i need a matching kernel ?i have an geforce 8800 gts SC everything is working fine compiz,emerald,etc but the black windows thing


I used to have that card, what I used to do to get it working was this:

Do a ful system update (i.e. kernels, apps, et al)

Install and run ENVY [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install your driver through Envy and restart.

Run nvidia settings as root:

```
gksudo nvidia-settings
```

Configure everything you need in nvidia-settings window (i.e. resolution, refresh, digital vibrance)

Reboot again and

Done!

Trust me, it's a lot more simple than it actually sounds. :popcorn:

---

### Post by CaptainInsaneO on 2007-09-27
> **skymera said:**
> yeah off topic.
make your own :lol:

well...i sorta ended the service for GDM logon and ermmm no gui at logon...or at all.
is it easy to get it back?

if it aint i might pack my bags and go to windows, or fresh install

Not sure, but try this:

```
/etc/init.d/gdm start
```

P.S. Everything is easy in Ubuntu once you get used to it. In all honesty, I was a hardcore Windows fan for many years (since about 1995) until I discovered the *nix terminal. Things are just easier in Linux.

---

### Post by skymera on 2007-09-27
meh done nothing.
when i install and i boot, i have no gui. fasiled to start xserver everytime
where do i get envy from then/ how do i install?

---

### Post by CaptainInsaneO on 2007-09-27
Follow the link I posted, that's where you get it. It will have full information on that page.

Are you getting any error messages when you type startx? Give me more information, I'm really trying to help you. :)

---

### Post by skymera on 2007-09-27
ok lets say i do fresh install.
it wont recognise my card and xserver will fail to start.

so im guessing to stick envy on my usb and install in command line.
but how do i run it?

---

### Post by skymera on 2007-09-27
come on dont leave me hanging here liek this

---

### Post by davedumas0 on 2007-09-27
try ctrl+alt+f2 then log in and type envy -t 
and thats it

---

### Post by davedumas0 on 2007-09-27
you might have to use aptitude i did   but i have the nvidia 8800 gts

---

### Post by skymera on 2007-09-27
done fresh install.

gotta start from scratch :(

but thanks for help.

---

### Post by CaptainInsaneO on 2007-09-27
I'm sorry I couldn't be of more assistance. Stick with it and you'll get the hang of it. :)

---

### Post by skymera on 2007-09-28
all done!
envy worked. got the latest driver.
tada!

---

### Post by CaptainInsaneO on 2007-09-28
Glad to hear it!

---

