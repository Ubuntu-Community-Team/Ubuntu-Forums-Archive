---
title: "im having trouble installing ubuntu on my home system"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-03-01
i am having trouble understanding how to fix the ati driver for ubuntu. i loose signal to my screen while booting. i have read into it a little, but i dont understand. i had no probs running with my laptop. its got a ati radeon too. WTF! i guess im asking for help. thanx

---

### Post by overdrank on 2008-03-01
> **cpu_medic said:**
> i am having trouble understanding how to fix the ati driver for ubuntu. i loose signal to my screen while booting. i have read into it a little, but i dont understand. i had no probs running with my laptop. its got a ati radeon too. WTF! i guess im asking for help. thanx

HI and what is the model of the ATI graphics card?

---

### Post by cpu_medic on 2008-03-01
it is an ati radeon x1650 256 mb

---

### Post by overdrank on 2008-03-01
> **cpu_medic said:**
> it is an ati radeon x1650 256 mb

Hi and you may look a Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cpu_medic on 2008-03-01
ok um, so i am using a live cd for installing ubuntu on my desktop(the issued compy). how do you install with just the command line? then envy might work

---

### Post by overdrank on 2008-03-01
> **cpu_medic said:**
> ok um, so i am using a live cd for installing ubuntu on my desktop(the issued compy). how do you install with just the command line? then envy might work

Ok I misunderstood, I was understanding that ubuntu was installed. Have you considered using the alternate cd and then you can hopefully use envy with a GUI to install the drivers.

---

### Post by cpu_medic on 2008-03-01
ok its installing, but im afraid that when i boot for the first time, the video card wont be seen. how to i get to envy from a console? or am i just dumb and it will work?

---

### Post by overdrank on 2008-03-01
> **cpu_medic said:**
> ok its installing, but im afraid that when i boot for the first time, the video card wont be seen. how to i get to envy from a console? or am i just dumb and it will work?

Hi and the FAQ may help
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)
But you may be able to reconfigure you xorg from the command line if you don't receive a desktop
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by cpu_medic on 2008-03-02
ok im at the console and it has poped up with a bunch of choices (drivers?) um would you know what one to choose?

---

### Post by cpu_medic on 2008-03-02
i have tried the ati but that diddnt work.

---

### Post by cpu_medic on 2008-03-02
it just said " xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf .20080301224342 


and went back to the command line...  CONFUSED

---

### Post by overdrank on 2008-03-02
> **cpu_medic said:**
> it just said " xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf .20080301224342 


and went back to the command line...  CONFUSED

Ok try the command startx. Did you boot into recovery mode or reach a virtual terminal?

---

### Post by cpu_medic on 2008-03-02
i booted in recovery mode and selected ati, and i tried startx, and it gives me " fatal server error: no screens found. xio: fatal io error 104 (connection reset by peer) on x server ":0.0"  after 0 requests (0 known prossesed) with 0 events remaining.
root@ubuntu:~# _

i dont know what to do, i have a screen pluged in, its in the DVI port, if that matters, it is a NEC LCD 1770GX

---

### Post by overdrank on 2008-03-02
> **cpu_medic said:**
> i booted in recovery mode and selected ati, and i tried startx, and it gives me " fatal server error: no screens found. xio: fatal io error 104 (connection reset by peer) on x server ":0.0"  after 0 requests (0 known prossesed) with 0 events remaining.
root@ubuntu:~# _

i dont know what to do, i have a screen pluged in, its in the DVI port, if that matters, it is a NEC LCD 1770GX

Ok have you tried to boot normally?
You may try booting normally after the reconfigure and if you still receive the command line the reconfigure you xorg and choose the driver vesa.

---

### Post by cpu_medic on 2008-03-02
i have rebooted and it diddnt work. so i tried vesa and it diddnt work ether.

---

### Post by cpu_medic on 2008-03-02
what if i were to burn envy.deb to a cd? could i install it and run it from the console?

---

### Post by overdrank on 2008-03-02
> **cpu_medic said:**
> what if i were to burn envy.deb to a cd? could i install it and run it from the console?

From the command line
```
 wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu4_all.deb

```
This will download Envy
Then to run Envy
```
envy -t
```

---

### Post by cpu_medic on 2008-03-02
so i tried the first code, and it failed. because i have wireless internet that requires a wep key. how do you connect to a wireless network in the console?

---

### Post by overdrank on 2008-03-02
> **cpu_medic said:**
> so i tried the first code, and it failed. because i have wireless internet that requires a wep key. how do you connect to a wireless network in the console?

Sorry but wireless it my downfall, can you hardwire for the installation?

---

### Post by cpu_medic on 2008-03-02
no, because the router is in my roomate's (locked) room:(

---

