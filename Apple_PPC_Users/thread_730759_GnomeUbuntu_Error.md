---
title: "Gnome/Ubuntu Error"
date: 2008-03-21
forum: Apple PPC Users
---

### Post by LinuxRT on 2008-03-21
Right when I start my new session:

1. The ubuntu loading black screen never shows up (even when I eject the CD)
2. After login the wallpaper is completely black. ( So when I tried to boot it again using Ubuntu live CD, the install icon won't show up). 
3. And a follow up of errors. e.g. Gnome, Bonobo, Nautilus, problem loading applets. Asking me to delete or don't. I already tried to reboot but the same thing will happen again! 


I've read some threads, but nobody specifies the commands for the terminal.

Please help, I'm loosing it!

Thanks RT

---

### Post by adelahunty on 2008-03-21
Could you provide information about your machine?  Reason I ask is that I have seen this issue on a couple of types of Mac, depending upon things like RAM and processor.

Also, you don't say for certain, but I am guessing this is from a live CD boot...?

Quick response is that it could very well be a memory / processor issue, as I have seen this on clamshell iBooks and one or two unexpanded G3 PowerMacs (Blue and Whites, if I recall).  If you are using Ubuntu, try switching to Kubuntu or (even better) Xubuntu live CDs.

---

### Post by maddog39 on 2008-03-21
I had this same problem on my 12" TI PowerBook G4 and I worked around the problem by simply just using Xubuntu.

---

### Post by adelahunty on 2008-03-21
As a quick additional, if you *do* install Xubuntu, and then want to switch to a more Ubuntu-esque interface (or to put it another way, you want Gnome, and not XFCE), once you're up and and running, just install the ubuntu-desktop package with apt / synaptic, and you're laughing.*

```
sudo apt-get install ubuntu-desktop
```

Just been experimenting with a B&W PowerMac, and it was having the same issues as the original poster.  An upgrade of RAM sorted it out.



*Probably - assumes that your machine can actually handle the complexities of something like Gnome.  I still recommend XFCE, IceWM, or one of the Black/Open/Fluxbox managers if you're having trouble with the default Ubuntu.

---

### Post by stream303 on 2008-03-22
> **adelahunty said:**
> 
Just been experimenting with a B&W PowerMac, and it was having the same issues as the original poster.  An upgrade of RAM sorted it out.

Just a reminder for those upgrading their ram after install - you'll probably want to make sure your swap partition is at least 1, 1.5, or 2 times the amount of new ram.  If you are uncomfortable with repartitioning, and don't mind reinstalling, the new install will calculate it properly for  you.

---

