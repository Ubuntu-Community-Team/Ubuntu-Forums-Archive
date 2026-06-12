---
title: "nvidia update trashes my ubuntu kernels"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Psyphre on 2007-02-16
Hi, I was updating my nvidia drivers from this thread:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

it was all going fine, but when i got to the part i needed to restart... thats where it all when wrong.

All my kernels will no longer work. It wont load up the GUI anymore. I think it said there was a problem with either xorg or xserver.

I have also noticed a new kernel in the grub list:
Ubuntu, Kernel 2.6.17-10, 386
This one DOES actually work, except now my internet doesnt work. 
(Ive asked this question earlier today when my wifi didnt work on a new kernel, and was told to reinstall the drivers, which solved it). When i try in "Ubuntu, Kernel 2.6.17-10, 386" it refuses to reinstall!! 

I dont understand whats going on. Why has updating nvidia drivers trashed my ubuntu kernels apart from the one which wont install my wifi. More importantly, how can i get everything back??

Thanks!

---

### Post by justin whitaker on 2007-02-16
> **Psyphre said:**
> Hi, I was updating my nvidia drivers from this thread:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

it was all going fine, but when i got to the part i needed to restart... thats where it all when wrong.

All my kernels will no longer work. It wont load up the GUI anymore. I think it said there was a problem with either xorg or xserver.

I have also noticed a new kernel in the grub list:
Ubuntu, Kernel 2.6.17-10, 386
This one DOES actually work, except now my internet doesnt work. 
(Ive asked this question earlier today when my wifi didnt work on a new kernel, and was told to reinstall the drivers, which solved it). When i try in "Ubuntu, Kernel 2.6.17-10, 386" it refuses to reinstall!! 

I dont understand whats going on. Why has updating nvidia drivers trashed my ubuntu kernels apart from the one which wont install my wifi. More importantly, how can i get everything back??

Thanks!

The error you saw was a problem with X. I assume you are using Nvidia...the video drivers need to hook into the kernel, so when you installed that, it broke your current drivers.

If you have envy installed, use that to reinstall the drivers. If you don't have envy installed....um, I don't know how to do it, since I always take the easy way out. :lolflag:

---

### Post by mikewhatever on 2007-02-16
One way of fixing it is to try to reinstall nvidia driver one more time. I would also recommend envy because of its easiness and efficiency.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Your kernels are not trashed in any possible way. The error you get is purely driver related, and you yourself said you've tried reinstalling it.

---

### Post by rocknrolf77 on 2007-02-16
If you don't have envy installed you can get it with wget from rescue mode. :) 

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

Then you can install it with ```
sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb

```

Edit : How can you get the whole url to show to write it on a paper?

---

### Post by Psyphre on 2007-02-16
sorry i dont have envy (As far as im aware). Infact i dont even know what envy is :confused:  .
What i dont understand is, if I was supposed to do something in order to make the nvidia driver hook onto some kernel, how come this wasnt mentioned in the guide?

edit: 
i cannot access the internet, so i cant install envy im afraid. Also even in the normal kernel I use, its a pain to get the internet working. I have to go thru a whole process everytime i turn on the computer just to get the internet working. I have no idea how to do it in rescue mode....

---

### Post by rocknrolf77 on 2007-02-16
You can read about envy in the link given : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Edit : didn't see your edit until now.

---

### Post by JamieC on 2007-02-16
I have a feq questions for you:-

[list=1]
[*] What were your previous kernel versions? 386? generic? SMP?
[*] Is the 'new' kernel actually the newest?
[*] Have you tried re-installing the restricted modules for an 'older' kernel version?
[/list]

---

### Post by mikewhatever on 2007-02-16
"http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb"

hope it works :)

---

### Post by rocknrolf77 on 2007-02-16
Go into rescue mode - log in with your username and password : type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then select the nv driver. If that will not work try the vesa driver. Type "exit" can't remember if it's one ore two times. I think that will get you out from rescue mode and into gdm, where you can log in. If I remember wrong try to type ```
startx
```  At least then you will get a gui to work from.

---

### Post by Psyphre on 2007-02-16
[I]I have a feq questions for you:-

   1. What were your previous kernel versions? 386? generic? SMP?
   2. Is the 'new' kernel actually the newest?
   3. Have you tried re-installing the restricted modules for an 'older' kernel version?[/I]

Ok ill list it out to answer 1. and 2.

ubuntu, kernel 2.6.17-11-generic     <-- new one that popped up after an update yesterday
ubuntu, kernel 2.6.17-11-generic (recovery mode)
ubuntu, kernel 2.6.17-10-386          <-- the last one to pop up, happened after trying nvidia update
ubuntu, kernel 2.6.17-10-generic     <-- original
ubuntu, kernel 2.6.17-10-generic (recovery mode)

only 386 will work (i.e the GUI works). However I cant get my wifi drivers working on it.
I have no idea what its doing there anyway, what is it?

For you 3rd question I am afraid thats above me. Are you saying have i tried reinstalling the wifi drivers on the other kernel drivers?

mikewhatever: afraid I have no internet access on the comp with the problem so im not sure how I could use envy.

rocknrolf77: Actually I can use the GUI on some new kernel that appeared after trying to update my nvidia drivers. Its only the ones I usually use (generic kernels) that wont work. Unfortunately the kernel whihc DOES work, doesnt want to install my wifi drivers. I was hoping someone could explain how I can undo all this.

---

### Post by JamieC on 2007-02-20
Boot into recovery mode (with the newest kernel) and run the following command:
```

sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

```

---

