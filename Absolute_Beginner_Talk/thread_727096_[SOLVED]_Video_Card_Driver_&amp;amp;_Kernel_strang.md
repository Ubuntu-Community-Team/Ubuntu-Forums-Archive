---
title: "[SOLVED] Video Card Driver &amp;amp; Kernel strange behavior"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by bioShark on 2008-03-17
Hi

I have recently installed kubuntu 7.10. I've installed the legacy drivers without problem. A lot of re-boots, whithout problem. Yesterday I tried to install compiz, without success. Shutdown went smoothly. 
Now, today, when I fired up the pc, it entered text mode saying that NVIDIA driver 7xxx detected and kernel has 9639. Ok, the driver I've installed was 9639. I re-installed the driver from the command line (a good thing i kept the file), then run: 

> startx 

and kubuntu strated up perfectly. I uninstalled all the packages about compiz, thinking that this might have caused the crash, and rebooted trying to see if I solved the problem. At log-out, I only had the option to "Log-out", but anyway, I shutted down kubuntu from the command line:

> sudo shutdown -h now  

After re-boot, the exact same problem happened. Now, I know that it takes me less then 3 minutes to re-install the driver and fire up kubuntu, but I don't really want to dio this every time I start up my pc.

Solutions are apreciated, thx.

---

### Post by Supergoo on 2008-03-17
Just wondering if you might have updated the system and it is causing problems with the driver ? I once had a driver issue like that after I updated a system, then again I tend to break my systems poking around in the inner workings too much :)






Supergoo

---

### Post by bioShark on 2008-03-17
I made a full update of "the updates" right after the installation of kubuntu was ready, before I first installed the legacy driver. Also, I did a lot of re-booting since then. The problem arrived only since I've played with the compiz packages, yesterday.
 Now, there is no trace of any compiz package on my pc.

By update the system you mean:

> sudo apt-get update

or something like this? Because, if I recall, I did something like this....., not sure though

---

### Post by Supergoo on 2008-03-18
Yeah that was what I ment, Just thinking outloud is the compiz theme manager running, that darn thing always drove me nuts. Like I said I am just thinking outloud, I will keep thinking, if I come up with anything I will let you know.




Supergoo

---

### Post by linuxtoindia on 2008-03-18
after installing edubuntu , using it for some days
, when an application crashed< i was also using hybernation at that time >
i restarted pc .
it gave an error'' no image found., cud not resume /sda ,,,....somethg

i reinstalled again the whole os., then tried ubuntu,, same problem,, wiped and installed kubuntu.. same again ,,
now am on edubuntu!

i tried some where

sudo dpkg-reconfigure xserver-xorg
then gdm


it worked
,, but showed ;''running on low graphics.''
and maximum resolution 800x600

agian whenever i boot in edubuntu
it shows the same error''
no resume image ,, then startx error ,, some blue screen
some logs...

and after trying
sudo dpkg-reconfigure xserver-xorg

it works ,, but i have to do it again and again,, creating a new headache!!
i have via chipset
unichrome K8M800 s3,unichrome


please help


thanks in advance..

---

### Post by bodhi.zazen on 2008-03-18
How did you install the nvidia drivers ?

I have seen the problem you are having when nvidia-glx is installed and then the propriatry nvidias drivers are added. The solution (for me) was to remove nvidia-glx and re-install the nvidia driver.

Now in you installed the nvidia-glx-new driver there is an additional but I can walk you through ...

---

### Post by bioShark on 2008-03-18
This is how I've installed the nvidia driver:

Manual download to the Nvidia 9639 driver, directly from [www.nvidia.com](www.nvidia.com) .
After installing the build-essential :

```
sudo apt-get install build-essential
```

then closed X server an run

```
sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run
```

Then it makes an install of about 2 minutes, and the next time I started X, everything looked great.

I can't recall installing any nvidia-glx-new drivers, but maybe they've got installed with the compiz packages. In any case where's this driver, and how can I remove it.

Thx.

---

### Post by bioShark on 2008-03-18
I've looked in Adept Manager, and the nvidia-glx-new is not installed.

Searching after nvidia there, I find only one package installed: nvidia-kernell-common

---

### Post by bodhi.zazen on 2008-03-18
All you should need to do is :

```
sudo apt-get remove --purge nvidia-glx
```And then re-install the Nvidia driver.

You will need to re-install the Nvidia driver each time you update the kernel.

If you do not have nvidia-glx installed, open synaptic and search for nvidia.

You may have nvidia-glx-legacy or other nvidia packages installed. Remove them all, then re-install the Nvidia (proprietary) driver.

EDIT: I see you psted additional information while I was typing.

Yea, remove nvidia-kernell-common & search to see if you have nvidia-glx-legacy, or any other ubuntu nvidia package installed.

---

### Post by bioShark on 2008-03-18
Thanks, it worked.

Even though not nvidia-glx was needed to be removed, it was nvidia-kernell-common.

I will still read that link you have posted, and then make a decision weather to re-install the whole thing.

thx again

---

