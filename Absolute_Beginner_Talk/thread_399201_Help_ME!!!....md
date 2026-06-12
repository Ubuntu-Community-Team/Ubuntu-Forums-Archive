---
title: "Help ME!!!..."
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by nonmi9 on 2007-04-02
Ok, so I've installed ubuntu...pain in the you know what! i need to get drivers for lots of things here, i need sound drivers, video drivers. I own a dell dim 2300, i can't seem to find the drivers for it. im a n00b when it comes to Linux...so talk to me like im a baby! oh and i need to know how to dual boot windows and ubuntu. 

thanks guys.

---

### Post by Lucifiel on 2007-04-02
By default, your sound card and graphics card drivers should already have been installed. This applies to most of your other drivers too.

---

### Post by slayerboy on 2007-04-02
> **Lucifiel said:**
> By default, your sound card and graphics card drivers should already have been installed. This applies to most of your other drivers too.

should is the key word...:lolflag:

nonmi9, what are your system specs/hardware?  Is it a custom made computer or something from the likes of Dell/HP/Emachines/etc?

And BTW welcome to Ubuntu!

---

### Post by nonmi9 on 2007-04-02
its a Dell dimensions 2300, with an integrated graphics card: Intel extreme  something...and integrated sound as well...i can't remember what its call though... i have a Nivida gforce FX 5200, but linux/ubuntu will not run with two cards at once, and i can't turn off my internal graphics card.

---

### Post by slayerboy on 2007-04-02
ok so you have an INtel video card.  Stupid question, how do you know you need drivers for your hardware?  This is not like windows where you need to install drivers when you reinstall the OS.

Also, if you lookin your computer's Bios (usually can be achieved by pressing a key like F2 or Del at boot, you might even see a prompt tellikng you what key to press)  You should have the option to turn off your intel card from within there.  You're going to have much better results with the Nvidia card IMHO.  But, it's going to take a litle more to get your Nvidia driver installed, but nothing we can't walk you through.

Back to my stupid question...how do you know you need drivers?  What's not working?:)

---

### Post by nonmi9 on 2007-04-02
yea i've tried to disable it but there isn't an option for it. ubuntu gets stuck at some loading screen when i have my nivida in. so i was hopeing it just needs the driver for it, oh and for the intel driver, i thought that because i dont have a good screen resolution i needed the divers for it, like windows, i'm a windows guy and this is my first time with linux so i have no idea what im doing here!?

---

### Post by nonmi9 on 2007-04-02
so yea any ideas i would really like to use my 5200 but i can't turn off my mobo's Graphics card!?

---

### Post by trent dillman on 2007-04-02
...

---

### Post by zvacet on 2007-04-02
```
sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv**

---

### Post by nonmi9 on 2007-04-02
PCI, and whats the code you gave me???

---

### Post by nonmi9 on 2007-04-02
so yea any idea on what i should do?

---

### Post by Razorback on 2007-04-02
> **nonmi9 said:**
> so yea any idea on what i should do?

The code he gave you is for getting your video setup for the nvidia card.  Running that string takes you into configuring the pc.  Is your monitor going blank when it is booting up?

---

### Post by nonmi9 on 2007-04-02
no it gives me some code and the computer locks up, and i can't do anything, now when i take the 5200 out it boots up.

---

### Post by trent dillman on 2007-04-06
...

---

