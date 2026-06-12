---
title: "Graphics crash"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2007-02-01
I just installed Kubuntu, but as soon as it gets past the loading screen, my screen turns off.  I assume this is due to a lack of drivers for my X1900 graphics card, but i have been off ubuntu for 6 months since i got my new computer, so i have no idea what to do.  The same problem occured with the live CD, loading and then crashing, so i installed it with the text interface
can somebody point me to somewhere that will halp me fix these problems.

One complication is that i dont think it has drivers for my onboard Marvell lan adapter, since the setup complained of no internet connection

---

### Post by carlosfocker on 2007-02-27
When you receive the black screen press ctrl + alt + F1 to bring up a prompt.  Then type

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
```

Install envy

```
sudo dpkg -i envy_0.8.2-0ubuntu1_all.deb
```

Run envy

```
envy
```

install you ati drivers.

---

### Post by ljpm on 2007-02-27
The problem might also be with the hscan and vscan ranges for your monitor. If you have the wrong ranges set then your monitor will shut down to avoid damage.

you can try reconfiguring xorg-xserver if the previous suggestion does not help.

---

