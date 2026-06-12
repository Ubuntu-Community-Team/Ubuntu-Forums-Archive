---
title: "32bit or 64bit"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-12
im downloading ubuntu. 32 bit.. but my processor is amd turion 64 x2 mobile
so my ques is .. is my  processor 64 bit  ?

this my spec for your info
# AMD Turion 64 X2 Mobile TL-52 (1.60GHz/512KB)
# 14.1" WXGA BrightView Widescreen (1280 x 800)
# NVIDIA GeForce Go 6150
# 512MB DDR2 SDRAM (2x256MB)*
# 60 GB 5400 RPM Serial ATA Hard Drive
# Super Multi 8X DVD+/-R/RW w/Double Layer Support
# 802.11b/g WLAN

---

### Post by Dr. Nick on 2007-03-12
Looks like a 64 bit to me, you can however run the 32  **or** 64 bit version of 64 bit

you cant run the 64 bit on a 32 bit though

---

### Post by HunkieChan on 2007-03-12
> **Dr. Nick said:**
> Looks like a 64 bit to me, you can however run the 32  **or** 64 bit version of 64 bit

you cant run the 64 bit on a 32 bit though

so if mine is 64bit.. and im downloading 32 bit..will it effect my system.. like slow down the comp or graphics or anyother problem like that ..

---

### Post by russell.h on 2007-03-12
If you're new to Ubuntu I recommend going with the 32 bit as it will give you more functionality out of the box. Later you might decide to move to 64 bit, but if you're new to Linux it probably isn't worth it.

Edit: And no, it shouldn't slow much of anything down. Certain programs would run *faster* in 64 bit than in 32 bit, but thats mostly certain computationally intensive operations like encoding audio or video. In general you would probably notice no difference, its just that in 64 bit you have to do a few extra things (install a new web browser for example) before your computer is really ready for everyday use. And graphics shouldn't be effected at all really.

---

### Post by HunkieChan on 2007-03-12
> **russell.h said:**
> If you're new to Ubuntu I recommend going with the 32 bit as it will give you more functionality out of the box. Later you might decide to move to 64 bit, but if you're new to Linux it probably isn't worth it.

Edit: And no, it shouldn't slow much of anything down. Certain programs would run *faster* in 64 bit than in 32 bit, but probably not enough so to notice. And graphics shouldn't be effected at all really/

i meentioned graphics cauuse.. i actually had ubuntu for last two days.. then i installed nvidia manually through terminally.. cause my screen was lagging whenever i scrolled, minimiize and etc.. but it crashed.. so im in mepis... now trying geet the imageof ubuntu aand reinstall it.. any suggestion ?

---

### Post by Dr. Nick on 2007-03-12
I have a 64 bit chip with a 32 bit install.

Did you just install the nvidia-glx package, or try the nvidia installer?

a simple 

sudo apt-get install nvidia-glx

then editing /etc/X11/xorg.conf from "nv" to "nvidia" has worked well for me

---

### Post by HunkieChan on 2007-03-12
> **Dr. Nick said:**
> I have a 64 bit chip with a 32 bit install.

Did you just install the nvidia-glx package, or try the nvidia installer?

a simple 

sudo apt-get install nvidia-glx

then editing /etc/X11/xorg.conf from "nv" to "nvidia" has worked well for me

ill try it when i install it.. but im scared.. what if i crash it again... you know when the os boots a black screen and says your x server is messed up.. .. uggh.. do you have a contact.. cause im new here.. i constantly need help.. thanks

---

### Post by Dr. Nick on 2007-03-12
If you have any problems just post here and someone should be able to help.

If it gives you the screen saying the xserver is messed up just click through it until you get a command line. Then type

**sudo nano /etc/X11/xorg.conf** and look for the device section, If the driver line says nvidia then change it to "nv" or maybe "vesa" and then push ctrl+x to save and exit, then type **startx** or just reboot using the command **reboot** and you should be back into graphical mode

---

### Post by HunkieChan on 2007-03-12
> **Dr. Nick said:**
> If you have any problems just post here and someone should be able to help.

If it gives you the screen saying the xserver is messed up just click through it until you get a command line. Then type

**sudo nano /etc/X11/xorg.conf** and look for the device section, If the driver line says nvidia then change it to "nv" or maybe "vesa" and then push ctrl+x to save and exit, then type **startx** or just reboot using the command **reboot** and you should be back into graphical mode

how do i go throught it cause its a blue screen and the ask me to put name what brand and size and all those stuffs.. do i just keep pressing enter until the end ?

---

### Post by Dr. Nick on 2007-03-12
Hmm, Im thinking about a different thing then, what you say sounds like the 

sudo dpkg-reconfigure xserver-xorg program, If its asking stuff about the size of memory just try pressing enter. The part that really matters is the driver and monitor sections, IF you have nvidia then pick 'nv" to start off with.

---

