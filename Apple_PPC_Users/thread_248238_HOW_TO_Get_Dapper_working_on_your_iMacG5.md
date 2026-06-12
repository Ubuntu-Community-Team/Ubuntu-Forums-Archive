---
title: "HOW TO: Get Dapper working on your iMacG5"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by Torrance on 2006-08-31
**The Hardware:**

iMac G5 Rev A (flat/squarish back). The Rev B (curved back) and Rev C (iSight) will also likely work but this hasn't been tested yet.

[Update: The iMacG5 Rev C (iSight) does not have thermal control available yet in the 2.6.18 kernel.The fans will run at full speed. This is perfectly safe, but annoying.] 

**Symptoms:**

LiveCD does not boot. Alternative text-based installer works, but system freezes at log in screen. Fans rev to full speed after a couple of minutes.

**The Problem:**

There is an incompatible sound module in the kernel that is being loaded. This is causing the system to freeze everytime a sound is played - such as at the log in screen, or if you generate a system beep in the terminal.

My previous work-around with Breezy was to stop the start up sounds, but this meant no sound at all. Other distributions have similarly disabled the sound to stop the log in freeze.

The fans are caused by a lack of thermal control. This is present in most other distributions.

**The Solution:**

Simple - install a new kernel that fixes the sound problem, and includes fan control!

1) Install Dapper with the alternative text-based installer.

2) Run the system. Note the freeze at the log in screen. Hard reboot.

3) Stop X Windows from loading (thus delay any sound-based system freezes).

a. Start up as per normal.
b. Moments before the log in screen appears, you'll notice the start-up image disappears, the screen goes black and the 'thinking' mouse curser appears. Quickly press control-alt-backspace to kill X Windows.
c. X Windows is persistant. It'll try loading itself again. Kill it again. In fact, it'll try loading itself 6 times, waiting a little longer each time, before it finally notifies you that it's going to take a break for 2 minutes. Each time kill it with control-alt-backspace.
d. Now log in and type
```
sudo /etc/init.d/gdm stop
```
e. You now have a fully functioning terminal. Just don't press backspace when there is no text to backspace - this will generate a system beep and the terminal will freeze. You'll have to repeat the above process if this happens!

4) Install the components you'l need for this kernel compile.
```
sudo apt-get install links build-essential kernel-package libncurses5-dev
```

5) Download the kernel source. We want the 2.6.18 kernel, as this has sound support, and this is about 45mb in total.
```
cd /usr/src/

sudo links www.kernel.org
```
...and downlaod the link to the full 2.6.18 kernel (press return/enter once the cursor is hovering over the first 'F').

To check it has downloaded, quit links and from the terminal type "ls" and see that the file "linux-2.6.18.tar.bz2" is there.

6) Now we need to decompress the kernel and set up our directory structure properly.
```
cd /usr/src

sudo tar -xvjf linux-2.6.18.tar.bz2

sudo ln -s /usr/src/linux-2.6.18 linux && cd /usr/src/linux
```
7) Configure the kernel.
```
sudo make g5_defconfig
```
If you'd like to make any changes to the default configuration for G5's, then have a play:
```
sudo make menuconfig
```
The defaults are probably best, except it might be helpful under Kernel to change the preemption model to "Voluntary Kernel Preemption", and change the kernel frequency to 1000Hz. Also, under "Block Devices" make the CFQ I/O scheduler the default. These changes aren't essential but may add a tiny bit to your performance.

8.) Now compile!
```
cd /usr/src/linux

sudo -s -H

make-kpkg clean

make-kpkg -initrd --revision=g5 kernel_image kernel_headers modules_image
```
You can call the revision whatever you like - I've called it 'g5' for convenience. This will take about half an hour - go grab a coffee. :D

9) Now install the kernel.
```
cd /usr/src

dpkg -i kernel-h*

dpkg -i kernel-i*
```
10) Log out and restart. Fingers crossed this works! =D> =D> =D> 

**Caveats**

The only limitation I have found is that video is quite jerky. I used the gstreamer codecs from the Edgy sources and this brought everything to run smoothly (ie. its not a kernel problem).

Please also note that there may be problems compiling the 2.6.18 kernel with Edgy Eft. This is a problem with "make-kpkg" in Edgy.

---

### Post by DylanRE on 2006-08-31
I found the 2.6.17 kernel with the Ubuntu drivers in Synaptic (I'm running Edgy). Maybe enabling the fan drivers would create a suitable kernel? I'm new to this as well.

Or possibly download the latest kernel with Ubuntu drivers via apt-get from within Dapper (rather than Edgy) and configure it.


This could all be completely wrong... If it sounds right, I guess it's worth a try, but don't take my word for it.

---

### Post by Torrance on 2006-08-31
> **DylanRE said:**
> Or possibly download the latest kernel with Ubuntu drivers via apt-get from within Dapper (rather than Edgy) and configure it.

I downloaded the source code for the Edgy kernel - all 150mb of it I think - and tried to compile it using the config file from /boot in the Edgy liveCD, making only a couple of changes (such as enabling the fan support). Unfortunately this compile failed after about 40 minutes, likely because I did something wrong.

I may have another go, but at the moment the kernel I have is perfectly fine just minus smooth movie playback which I can live with in the meantime (and prefer over having fans on full speed as with edgy).

---

### Post by DylanRE on 2006-08-31
I'm compiling it right now, and I've gotten quite a few errors. I guess it's possible it's just the kernel and not us.

---

### Post by Torrance on 2006-08-31
Cool - let me know how that goes.

This page may be helpful: [https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28CategoryKernel%29%3E](https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28CategoryKernel%29%3E)

---

### Post by Torrance on 2006-09-01
Oh, it turns out I was wrong. The smooth playback in Edgy isn't a result of a better kernel, but a better gstreamer system. So, I just added the Edgy sources to my apt list, upgraded the relevant gstreamer components, and then reverted my source list back to standard Dapper sources. As a result, my movies now all play smoothly. Yay! :D

---

### Post by Torrance on 2006-09-01
Oops! Ok, so it turns out you can't use those packages to install a new kernel.

I'll rewrite the first post tomorrow to describe how to do the whole process - including the kernel compile. It's a little bit more tricky but still doable.

---

### Post by DylanRE on 2006-09-01
Sorry for not responding last night. My kernel compile failed, so I got frustrated and went to sleep, ha.

If I can't find Knot 2 in the next hour or so, I'll go ahead and install Dapper and see what I can do.

---

### Post by Torrance on 2006-09-01
Ok, I've updated it to describe the entire kernel compiling process. It's sweet now. :D

---

### Post by Torrance on 2006-09-01
Edgy Eft Knot 2 is out. Does anyone know if fan control is enabled on it yet?

---

### Post by DylanRE on 2006-09-01
Fan control doesn't look to be enabled in Knot 2.

Life would be a lot easier if the kernel would compile.:-\

---

### Post by kulath on 2006-09-04
When you say fans are not enabled in Edgy Knot 2, which iMac exactly do you have - if it's Rev C, it may be it's not a question of whether it is enabled, but rather that it doesn't work anyway.

---

### Post by Torrance on 2006-09-11
Just updated the How To to include the latest kernel patch, ie. rc6 rather than rc5.

---

### Post by Torrance on 2006-09-15
Edgy Eft Knot 3 has just been released: [http://cdimage.ubuntu.com/releases/edgy/knot-3/](http://cdimage.ubuntu.com/releases/edgy/knot-3/)

Anyone tried this and know if they've sorted the G5 fan issue yet?

---

### Post by localzuk on 2006-09-23
Can anyone provide confirmation that fan control is working properly on the Rev C iMac G5? I don't fancy going through all that to end up with a jet engine sat in my room...

Cheers

---

### Post by Torrance on 2006-09-24
Fan control almost certainly does not work (there is no kernel option for powermac 12,1 - which is what the rev c iMac is based on), though I have not seen it tested.

In other news, the final version of 2.6.18 has been completed, though I have not been able to get it to build based on a standard g5_defconfig. Anyone else had luck with this?

---

### Post by Torrance on 2006-10-11
I have updated the How To for the final 2.6.18 kernel. This compiles fine in Dapper, but you'll have problems compiling it on an Edgy Eft system.

---

