---
title: "Dual Boot at this point?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-20
Hello all
I have a single 250GB partition on one of my boxes which has Gutsy amd64 on it. I do have a handsome amount of space free. Here's the config:
T5500, GMA950, 1GB DDR2, 250GB SATA-II

Now, with that, Gutsy is fast, but I would like something to be faster. What if I shrunk the partition and installed Puppy or something. Would that be lightening fast? How do I proceed? What is the guarantee that gparted would not screw up my data (I cant afford to lose it, neither can I back it up here at my college)

---

### Post by sandysandy on 2008-04-20
gparted is pretty reliable. have used it a number of times with no issues. 

puppy is basically for using as a live CD.

regards

---

### Post by m0rphex on 2008-04-20
I don't know if shrinking the partition would make it any faster, but puppy would. If you have important data on the partition maybe you should backup somehow before anything.

---

### Post by cotcot on 2008-04-20
If you cannot backup, please wait until you can.
If you want something fast then try gentoo 64 bit with xfce and select carefully the use-flags. Note that this is not done within a couple of hours. 
All by it i do think that with the computer specs you give you will gain much speed in time. (30 % speed gain does mean nothing on a fast computer that loads an application within seconds).
Is there any specific application you would like to see work faster ?

---

### Post by sayakb on 2008-04-20
> **sandysandy said:**
> gparted is pretty reliable. have used it a number of times with no issues. 

puppy is basically for using as a live CD.

regards

So puppy can't be installed? Is there any equivalent lightening fast distro (I have tried XFCE. Need something different)

---

### Post by freduardo on 2008-04-20
Personally, I wouldn't shrink the partition when you have no backup. 
Seriously, the risk of losing your data is still pretty big (imho).

So try to backup first. Maybe you can borrow and external drive for a few days from a friend or so?


As for dualbooting: Sure!
Why not try your hand at a little more complex distribution and try to setup your system bit by bit? 
I'd recommend ArchLinux with a lightweight WM like Openbox or PekWM, but that's a personal preference. 

Anyway, you'll learn heaps during the process and you'll still have your Ubuntu install to fall back on if everything goes to pieces :).

---

### Post by Sef on 2008-04-20
> So puppy can't be installed?

Puppy can be installed.  Many people have installed it and use it as their distro.

---

### Post by sayakb on 2008-04-20
Even with a Q6600 on my desktop, folders open really slowly with Gnome (though, I have used KDE4, but its extremely fast), So there's no specific app, but the overall OS should be faster on the laptop (which has very low config as compared to my desktop :( )

---

### Post by sayakb on 2008-04-20
Arch and slackware sound really complex to me (just 8 months on linux), I would try them on a VBox to ensure that I don't screw up anything :D

---

### Post by sayakb on 2008-04-20
> **Sef said:**
> Puppy can be installed.  Many people have installed it and use it as their distro.
Does the CD provide an installer? Or do I have to choose some complex way.?

---

### Post by bumanie on 2008-04-20
Puppy linux is fast and is designed, in part, to run on older/lower spec. computers. You can install to your hard drive or run it from a live cd. From the live cd, once 'loaded', puppy will run from ram and you can take out the live cd so that you have your optical drive free for burning etc.

---

