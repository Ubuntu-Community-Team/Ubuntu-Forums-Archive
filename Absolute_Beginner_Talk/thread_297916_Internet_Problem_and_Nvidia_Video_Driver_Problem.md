---
title: "Internet Problem and Nvidia Video Driver Problem"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by slafco on 2006-11-11
Ok, so i have managed to get the internet working. Problem is, after I change DNS servers in the DNS tab to my ISP's IP addresses (System/Administration/Networking). It's only temporary. They automatically get removed and changed back to 10.1.1.1. How do I make it last permanently??

Promblem 2. I have a 6600GT agp running on a 3000+ 64 bit machine. Is there a link some one can send me to download the drivers? Or a guide on how to do it(if it is not that simple)

Thanks guys :)

---

### Post by digby on 2006-11-11
Not sure about your DNS woes, but the nvidia driver is pretty simple.  If you want the older driver, you can simple type 'sudo apt-get install nvidia-glx' in the terminal.

If you plan to try out fancy graphical effects like beryl, you'll need the newer driver which you can install using [these instructions]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29").

The instructions say they're for the beta driver, but they'll install the real thing now that it's been released.

---

### Post by punx45 on 2006-11-11
how are you connecting to the internet?   cable/dsl? with or without router?
and so on.

---

### Post by slafco on 2006-11-12
I am connected to the internet through a router, I changed the IP address to a static one, so far so good, it hasn't changed back yet.

---

### Post by slafco on 2006-11-12
digby, thanks for the help, I tried the command but I do not have the package  installed. It also said the same thing(that i do not have the package) when I tried to install samba. Is there a link to a site where I can download all these packages?

---

### Post by punx45 on 2006-11-12
yeah using manual settings should make it stick.. were you using DHCP to get an IP from the router before?   if so was the router correctly configured for DHCP

---

### Post by slafco on 2006-11-12
Yep, I was using DHCP before, the router is properly configured, and the IP addresses on my XP machines are pretty much constant. 
Ubuntu has been running with a static IP address for about 3 hours now and I have had no problems with it at all.
As for the Nvidia driver I havent had a chance to try get it working yet as I have been busy with trying to get samba working properly(which I have now finally done, thank god!)

---

