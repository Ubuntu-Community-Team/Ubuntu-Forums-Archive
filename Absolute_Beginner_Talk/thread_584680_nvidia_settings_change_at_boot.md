---
title: "nvidia settings change at boot"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-10-21
My normal display settings are 1024 x 768 but when I boot up the machine to my new gutsy install, the settings are at 800 x 600. Is there any way to keep the settings from changing. This happens every time I boot. TIA

---

### Post by Qwerty_ on 2007-10-21
Have you actually gone ahead and installed Gutsy or is this the resolution you are in whilst running off the live cd?

EDIT:

I rushed what you had written and thought your live cd was booting into 800X600.

Have you installed the nvidia restricted drivers?

You can do this from System>Administration>Restricted Drivers Manager.

---

### Post by pdlethbridge on 2007-10-21
This is a new install and I used Envy last night to reinstall the nvidia drivers but the same thing is happening.

---

### Post by Noob4Ever on 2007-10-21
I have the exactly the same problem too

---

### Post by Qwerty_ on 2007-10-21
Well I don't know much about envy I installed my drivers from the restricted drivers manager and have not had any problems.

---

### Post by jevel on 2007-10-21
Same problem here.

I am running a nVidia Quadro video card on a Lenovo T61. When I first boot into my new installation, I get 1280 x 800 (?) resolution, but can change to the correct 1440 x 900. After the next boot it changes to 1280 x 1024 with a virtual screen.

I've checked the xorg.conf and it seems it inserts a lot of bogus things about the monitor causing the resolution to fail. (It lists the monitor as a 4:3 instead of the 16:10 it is supposed to support.)

I was running the beta of 7.10, and before the last update to the nVidia driver, I did not have this problem.

-KJ

---

### Post by pdlethbridge on 2007-10-21
I didn't have this problem with feisty, it would seem to be a gutsy problem. I didn't have a problem with synaptic in feisty, but I do in gutsy. This was a fresh install, not an upgrade.
"I was running the beta of 7.10, and before the last update to the nVidia driver, I did not have this problem." ditto to that as well

---

### Post by Qwerty_ on 2007-10-21
```
sudo dpkg-reconfigure xserver-xorg
```

Might help you.

---

### Post by Perfect Storm on 2007-10-21
First make sure that the nvidia driver is set in the xorg.conf
```
cat /etc/X11/xorg.conf
```

If it is, try
```
gksudo nvidia-settings
```
and set it up.

If it fails,
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by pdlethbridge on 2007-10-21
Art, tried your method and now I'm back up and running feisty. Gutsy died. I'll stick with feisty for a while and see how it goes

---

### Post by jevel on 2007-10-21
Will try the suggestions as soon as I get off work. (Cannot use Ubuntu docked... :( )

-KJ

---

