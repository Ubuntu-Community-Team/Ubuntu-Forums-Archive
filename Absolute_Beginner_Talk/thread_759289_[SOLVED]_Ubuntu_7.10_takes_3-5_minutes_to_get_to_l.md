---
title: "[SOLVED] Ubuntu 7.10 takes 3-5 minutes to get to login screen"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Justin72 on 2008-04-18
Hi there

I have a Toshiba Tecra S1 and since installing 7.10 it take around 3-5 minutes just to get to the log on screen.  I have loaded 7.04 onto a desktop before and it loaded really quick.  Is this normal for 7.10 or should I check something.  Please note I am very new to linux.

Thanks in anticipation.

---

### Post by Redache on 2008-04-18
Need a little bit more information....

It's probably down to not having enough Ram.

---

### Post by joshrobinson on 2008-04-18
is the bootscreen visible? with the progress bar?
sometimes if thats not showing, it can cause it to hang up

---

### Post by Justin72 on 2008-04-18
I can get Windows XP to load faster on this laptop, should I still investigate the RAM?

---

### Post by Justin72 on 2008-04-18
the boot screen is not visable, any suggestions to fix?

---

### Post by Can+~ on 2008-04-18
Disable services you don't use, bluetooth, anacron/atd, logging, power management if you're on a desktop, cupsys if you don't use a printer.

Install bootchart to check what takes most time.

*notice: I made this comment before noticing the new replies :S.

---

### Post by joshrobinson on 2008-04-18
```
sudo gedit /etc/usplash.conf
```

put your resolution in the fields

```
sudo update-usplash-theme usplash-theme-ubuntu
```
run that command, and reboot, see if it helps anything

heres an example of the resolution part, my resolution is 1280x800, so heres what my settings look like
```
# Usplash configuration file
xres=1280
yres=800
```

---

### Post by Justin72 on 2008-04-18
a big thank you to you josh, that worked a treat!!

---

### Post by joshrobinson on 2008-04-18
> **Justin72 said:**
> a big thank you to you josh, that worked a treat!!

your welcome
so you see the boot screen now? and it boots alot faster right?

---

### Post by Justin72 on 2008-04-18
> **joshrobinson said:**
> your welcome
so you see the boot screen now? and it boots alot faster right?

Yes I see the boot screen for both start up and logging off, and it is much faster for both, thanks again!

---

