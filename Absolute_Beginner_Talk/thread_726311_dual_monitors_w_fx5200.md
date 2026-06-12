---
title: "dual monitors w/ fx5200"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-16
I've read all kinds of threads on Dual monitors but I still can't get mine working.
I have a Chaintech video card chipset Nvidia fx5200. 
i think the problem is I can't get the nvidia driver loaded.
I downloaded the driver from nvidia site & it gave me an error installing , something about the kernel. It asked me if I wanted to search for the kernel online & I said yes but it gave me another error saying it could'nt find a kernel patch or something like that. 
Does anyone have any ideas on what I might need to do. I'm running gusty with ubuntu studio kernel.

---

### Post by janarene on 2008-03-16
Garyed, I too have the FX5200.  Hopefully nothing really got installed when you tried - if something did, you might have to remove it.  Anyhow, the solution is to download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") and install it.  Go ahead and run it and let it install the Nvidia driver automatically.  It's going to need to modify your xorg.conf file so you might want a backup of it before you run Envy.

---

### Post by garyed on 2008-03-16
> **janarene said:**
> Garyed, I too have the FX5200.  Hopefully nothing really got installed when you tried - if something did, you might have to remove it.  Anyhow, the solution is to download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") and install it.  Go ahead and run it and let it install the Nvidia driver automatically.  It's going to need to modify your xorg.conf file so you might want a backup of it before you run Envy.

Thanks for the reply but I already tried Envy before I tried to install the Nvidia drivers & it wouldn't work. I've been working on this a few days now & I think my problem is in my hardware set up. I'm using a KVM switch & I forgot how much trouble it caused the last time I installed Feisty on one of my computers. Gusty ran just fine with no set up until I tried to get dual monitors working. Once I tried Envy or installed any other drivers all hell broke loose. 
Its a pain pulling out all these wires but I can now get one monitor working with the new nvidia driver as long as its not hooked up to the KVM switch. I don't know if dual will work but I'm giving it a try. I'll post back if I can get both working.
Thanks again

---

### Post by garyed on 2008-03-16
It was the KVM switch  that was the problem.

---

