---
title: "Need help with installing nvidia card manually - without using apt-get"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Slyth100 on 2006-11-05
Hi,

I am trying to figure out how to turn off x so I can update my nvidia driver - as I don't have the internet on the computer I am using. I have to use another computer to access the internet - i know it sucks!

Anyway, will I think  I will need the kernel-source file and I don't know where to download this from or what version I need!

Anybody got any ideas, suggestions?

Thanks

---

### Post by chriscando on 2006-11-05
You can download the kernel source by using Synaptic. To find out which kernel source you need type 'uname -r' in a terminal. This will be the kernel version you are currently using. Once you know that you can search Synaptic for 'kernel' and download the source and headers packages for your specific version.

To get out of X you can logout (without shutting down) and then goto a virtual terminal by pressing (Ctrl+Alt+F1). Type 'sudo /etc/init.d/gdm stop' to stop X. Then just continue from there to install your new nvidia driver.

Hope this helps, good luck

---

### Post by chriscando on 2006-11-05
Hmmm, sorry I just read that you dont have internet on that computer. You could probably find your kernel version somewhere like [www.kernel.org](www.kernel.org) and then install it on your system, but it would be far easier if you just temporarily connected that computer to the internet and use Synaptic.

---

### Post by Slyth100 on 2006-11-05
Thanks for your help!!! :)

---

