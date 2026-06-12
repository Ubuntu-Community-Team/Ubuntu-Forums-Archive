---
title: "NVIDIA 8800 GTS - having driver and Xserver issues"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by graham_m on 2007-06-14
Hi there
firstly i will hold my hands up and say yes i am new to ubuntu, ive dabbled in the past but never really got to grips with it properly, **however** this time i have done a lot more background reading and was finally ready to take the plunge.

Also i will say this is a monster sized post, hopefully it isnt a waste of time and is slightly more helpful than "my 8800gts doesnt work someone fix it lolz rofl plz nub" etc

Installation went without a hitch (good job on the installer!) and so i went about my first task on any operating system, getting some graphics drivers! to my joy, lots of posts on the forums to read about the 8800GTS card and the nvidia drivers, and so i read them all and tried lots of different methods (will mention more later) however, on all occasions, my new friend, the Xserver blue screen popped up and said, "hi, i failed to start properly!" so after numerous dpkg-reconfigure xserver-xorg  resetting the drivers to the vesa ones so i could get back onto the forums and check for the other methods, i have finally admitted defeat and posted on the forums, usually i like to work things out for myself, but this time i need a helping hand i feel!

so far the methods i have tried:
clicking on "desktop effects" and when prompted, activating the nvidia drivers -> reboot -> xserver not working.

sudo apt-get install nvidia-glx-new  -> reboot > xserver not working (also tried with the sudo nvidia-glx-config enable method and it said the driver was installed - also xserver not working)

i also downloaded the latest drivers from the nvidia webby, stuck them on my desktop, booted into recovery mode and performed a sh NVIDIA_latest driver_number_.run   to which i got a message saying i needed to be in initlevel 3 or something similar (sorry cant remember the exact message, but im sure as non linux noobs youl know what i mean!)  so i backed out of the installer, typed that in and it booted my gui with the vesa drivers - wasn't what i expected admittedly!  so i went back and did the same steps again, this time ignoring that message and continuing with the installation, to which i was told i wasnt using the right headers or something, and that it wanted to download some new kernel (which downloaded the 3rd time i tried it) and it asked if it could run the configuration, not a problem i thought and it said it was done ->  xserver not working!
strangely the active driver was nvidia (not nv or vesa) when i next reconfigured xserver.. but still nothing.

i also read this post: [http://ubuntuforums.org/showthread.php?t=412133&highlight=gypsy](http://ubuntuforums.org/showthread.php?t=412133&highlight=gypsy) 
about the restricted drivers, so i followed a lot of those steps (i think i did that right!) and still the same result for me.

hey you, the person reading this, you can wake up now ive nearly finished!

so im waving the white flag, and would love it if someone can help me get on the path to ubuntu 8800gts goodness, my system specs are below if they may help!

Intel Core2 Duo Conroe 6600
3GB Ram (well theres 4 in the machine but thats another story..)
Nvidia 8800GTS (320mb)
ubuntu 7.(oops i forget, its the latest one tho!) installed on a seperate drive.

Oh yes, one other thing, i read on one of the coutless forum posts that i need an nvidia kernel and headers, admittedly im not 100% sure what thats talking about, but couldnt find anything on nvidias website (eek i sound like a total noob!)

I hope someone has read all this and feels sorry for me and will point me right!
Many thanks and i look forward to seeing some replies

also i went a whole post with no smilies. huzzah! the youth of today take note - it can be done!

---

### Post by starcraft.man on 2007-06-14
Ok well... seems you did every hard way there was before trying the easiest way :p.

[Envy]("http://albertomilone.com/nvidia_scripts1.html") is my graphics card installer and its worked for all my nvidia (only 2 so far) cards, and many others. Download the latest stable version, double click the deb to install. Go aplications > System tools > envy, select automatically install nvidia drivers and let it rip. It will select the most appropriate latest drivers that should work, it will prompt you numerous times always answer yes. It will also reconfigure the xorg for you. Then reboot and should be presto.

I have confidence that method should work, assuming the drivers support the 8800 (I'm pretty sure they do). I am a bit worried, I hope all that messing around with your Ubuntu install didn't mess up any important files... might want to do a clean install then Envy just to be sure.

Nice computer btw, no one says Linux has to be just for mid to low range PCs :D.

---

### Post by graham_m on 2007-06-14
thanks
i shall look into that method in a minute.

one other possibly slightly unrelated question, how come in GRUB i now have 3 different kernels? i have something like 15.xx - generic , 16.xx - generic  and .386  or something along those lines!

---

### Post by graham_m on 2007-06-14
you sir, are the king of awesome!

that worked a treat - at least i assume so, im now in full 1680x1050 res goodness and things just seem a lot nicer.

i wish i spoke to you sooner then i wouldnt have been up to the early hours of the morning playing around with it all!

thanks again!!

---

### Post by starcraft.man on 2007-06-14
> **graham_m said:**
> thanks
i shall look into that method in a minute.

one other possibly slightly unrelated question, how come in GRUB i now have 3 different kernels? i have something like 15.xx - generic , 16.xx - generic  and .386  or something along those lines!

[This page will answer any and every question about GRUB. ]("http://users.bigpond.net.au/hermanzone/p15.htm")There are numerous options you can tweak.

You only have 2 kernel version, 16 is the newer one and 15 is the older one left over if a compatibility issue was had. The other one I assume is memtest86, don't use that unless you believe your RAM is faulty.

You have mutlitple options, you can uninstall the old kernel if you know everything works perfect with new one. Do this in synapitc (System > Administration > Synaptic) and search for the name of the kernel, it is easily found and then removed via there. You can also after reading the GRUB page, edit it out so its not an option but remains on your drive. Or you can just leave em there. Up to you. :).

Best of luck with the NVidia card, I hope it works cuz I'm getting a GTX on my new computer >.>.

---

### Post by starcraft.man on 2007-06-14
> **graham_m said:**
> you sir, are the king of awesome!

that worked a treat - at least i assume so, im now in full 1680x1050 res goodness and things just seem a lot nicer.

i wish i spoke to you sooner then i wouldn't have been up to the early hours of the morning playing around with it all!

thanks again!!

LOL! SIR? Are you inferring I'm old? Arrrrgggggg *shakes fist*

Your very much welcome, I am always glad to help out. Envy really is the best method for Graphics card installations IMO. Also glad your 8 series works else I'd be kinda in trouble with my new machine hehe :D.

---

