---
title: "nvidia drivers????"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by hangdogdaddy38 on 2007-05-05
I have a monitor that is widescreen. I can achive resolutions of 1368 by 784. but in the vidio monitor settings it only goes to 1024 by 768. How do i download, and where, to install drivers for geforce 6100. I would apreciate any help i could get. Yes i am new to linux but I think it's the way to go and so far ubuntu is what i've been looking for. Thanks, Mike

---

### Post by Schalken on 2007-05-05
System > Administration > Restricted Drivers Manager to enable the nvidia drivers. If its not there then go to Admin > Synaptic Package Manager and install "nvidia-glx"

---

### Post by hangdogdaddy38 on 2007-05-06
Yes thank you for the reply. I went to system restricted drivers and yes it is there and in use. But it still only lets me go to 1024 by 768. Since this is the case, do i need to install the nvidia drivers from nvidia's site for G-force and if so could you please help me on how to do that? And remember, I don't know crap, lol, on how to do that yet so please step by step. lol. I really appreciate any help you or anyone else could give me. So far that is really the only thing that's bugging me about this operating system. If I can get that I'm good to go. Well at least for now anyway. lol Thanks, Mike.:confused:

---

### Post by darkrose on 2007-05-06
The driver's on nvidia's site are the same ones you have installed now.
open a terminal
applications --> accessories --> terminal
and run:
nvidia-settings
a window will pop-up where you can adjust the resolution, and you should be able to achieve 1368x784 from in there.

---

