---
title: "request for nvidia"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-31
hey, this is a request for the latest nvidia drivers to be put in the repo. I've tried manually installing them but in the past it created more problems than it solved, i'm now sticking only to repo stuff.

But my cards arent properly detected by the current repository (Says default NVIDIA card crap) in my xorg files. I know this is not the normal correct result because i tried it at work on another box and the nvidia auto detects my card as its exact model in the xorg.conf .. (different cards, more standard one at work). the cards in question are EVGA 6800 XT (the XT line is rather new)

so anyways. i'm hoping the newest nvidia will work their way into the mix and hopefully it will solve my auto detection problems and hopefully solve my graphical woes.

---

### Post by Kimm on 2006-05-31
It would be nise to allways have the latest NVIDIA driver in the repos.

But if you need too, you can install it manualy and that will work untill you upgrade your kernel (you can lock the kernel version in Synaptic, Update manager will see this, apt-get however, wount)

---

### Post by sotonin on 2006-05-31
the last time i manually upgraded it caused all kinds of problems and i dont know enough about linux to do it safely. i ended up wanting to go back to repo drivers and when i did it fubared everything up and i didnt know how to recover from it... i ended up reformatting

---

### Post by Dr. Nick on 2006-05-31
What do you mean autodetection?

Is this what your talking about?
 Device          "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"

That is detected by xorg I belive, If you would like you can change whatever yours appears as. Mine was autodetected even before I installed the nvidia-glx package.

Now with a new line of cards though it may not work until xorg adds it as a known device. 

The new cards may have functionality beyond the latest repo drives though, I am not sure since I dont have one.

If you find you need the latest then you can get it from the nvidia site but be sure to remove the repo versions else they will conflict

---

### Post by Dr. Nick on 2006-05-31
[quote=sotonin]the last time i manually upgraded it caused all kinds of problems and i dont know enough about linux to do it safely. i ended up wanting to go back to repo drivers and when i did it fubared everything up and i didnt know how to recover from it... i ended up reformatting[/quote]

To get back to the repo version install nvidia-glx. I think in the nvidia readme they have provisions for removing it. If all else fails then edit xorg.cong and change "nvidia" to "nv" and it should get a gui back

---

### Post by Perfect Storm on 2006-05-31
There's a thread in ubuntu Dapper Development forum on howto install the latest Nvidia driver, you might head over and look at it.

---

### Post by sotonin on 2006-05-31
yeah ive read all those threads and done it. then when i wantd to go back i installed nvidia-glx and i could no longer start x server it started freaking out about conflicting versions, etc. anyways.. i have to stick to repo if i dont wanna break my system.

yeah... so its a xorg issue not nvidia issue? hmm... i know i can rename it to whatever i want in xorg but the fact that it doesnt detect it leads me to beleive its not utilizing it properly. that and the fact that my games run like crap :(

---

### Post by Perfect Storm on 2006-05-31
But did you read howto uninstall the latest nvidia before going back to default? Which could be the problem.

---

### Post by nudnik on 2006-05-31
Nvidia glx was updated within the last few days, hope it helps.

NVIDIA Linux x86 Kernel Module  1.0-8762

---

