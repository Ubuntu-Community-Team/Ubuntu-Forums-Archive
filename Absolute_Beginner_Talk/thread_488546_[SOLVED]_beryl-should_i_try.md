---
title: "[SOLVED] beryl-should i try??"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-06-30
ok so i have a dell laptop wit ubuntu fiesty and kubuntu on an external harddrive and i'm wondering if i should try to install beryl. on its site it said something about breaking the system because of nvidia graphics card drivers?? which leads me to my next question.  i know how graphic intensive beryl appears to be and i'm sure it is, soooo should i even bother trying?? i have an nvidia geforce fx go5200 graphics card in this laptop and it rly sucks for playing games on anything other than low quality... so should i even try?? 


thx in advance for the help

---

### Post by JayTee on 2007-06-30
are you using the open source "nv" driver or are you using the closed source Nvidia drivers? Your graphics card should run Beryl fine as long as it has at least 128MB of video ram or you have dedicated enough system ram to the video card. I'd try the latest Nvidia drivers in the repos and once you have them installed and have the correct resolution set and you are satisfied with the results at that point then go ahead and install Beryl from the repos. I have an old laptop that won't run Beryl so I'm not familiar with the specs on your graphics card but on this pc I've got an Nvidia 6200LE and with the 100.14.9 Nvidia drivers Beryl 0.2.1 literally screams it's so fast.

---

### Post by gameman12 on 2007-07-02
thx for the help, i dont' rmember wat drivers i have. i know i dont have that much dedicated video ram but system ram is over 1gb...i thinkk i'll try it thx

---

### Post by Raineer on 2007-07-02
Laptop graphics cards can be a bit weak, and (to me) that doesn't sound like one that will be all that strong although it may have the required 128meg of RAM in it. [Just looked it up on Nvidia's site, it does have 128]

You will need the closed-source "Nvidia" drivers, however Ubuntu 7.04 comes with those available and they will be automatically installed when you choose to enable "Desktop-Effects" from the Administration menu (maybe preferences, not 100% sure)

If you can't enable Desktop Effects and wobble windows and spin the cube, then you won't be able to install Beryl. Clear that hurdle first.

---

### Post by Chris S. on 2007-07-02
I'm using a Dell Inspiron 5150 with a GeForce FX Go5200 also.  Beryl runs pretty darn well on my laptop.  If I'm playing a game that requires OpenGL, then things can start to slow down a little, but you can very easily turn Beryl off and on, so it's no problem.

I'm using the nvidia-glx driver right now.  I tried the nvidia-glx-new driver, which was supposed to be right choice  for my card, but it was not very stable for me at the time.  This was about a month ago.  If you're ever updating your drivers, and you have the choice between the nvidia-glx and nvidia-glx-new drivers, try the nvidia-glx one.  It might work better for the Go5200.

Edit: Raineer's post came before mine, but in response: my Go5200 is the 64MB version, and it does run Beryl fine.  It can even handle blur with only a little slowdown.

---

### Post by pardesi on 2007-07-02
though i don't have a Nvidia card (i have ATI closed source) 64MB still Beryl runs great(till now) go ahead but be careful just back up ur xorg.conf  just in case....;)

---

### Post by Raineer on 2007-07-02
Chris's post makes it sound like you'll be just fine.

And as for the last post, yes definitely backup your xorg

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.BACKUP
```

or just call it whatever you like, once it's running I keep a copy in my home directory too...nothing can be more frustrating that shooting xorg bugs without a working backup.

---

### Post by gameman12 on 2007-07-02
thx everybody i installed it earlier and it works great, still customizing it!! thx for ur help

---

