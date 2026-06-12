---
title: "mac mini G4 dvi"
date: 2008-04-16
forum: Apple PPC Users
---

### Post by kingmoffa on 2008-04-16
Hi, 

Ever since upgrading from feisty to gutsy my graphics have been shagged. Common problem as everyone knows. 

Im currently working with the fbdev driver not radeon. Although it works, X is slow. I want the radeon driver back. 

The solutions around don't seem to work with a DVI connection. These are the ones suggesting moving back to feisty xorg ati module. 

 I was wondering if anyone had any ideas? Upgrading to herdy perhaps?

Thanks

---

### Post by BladeMelbourne on 2008-04-16
Whilst running Gutsy, I needed to use the Feisty ati driver (I was using the DVI to analogue adapter back then). Since you have tried it without success I will move right onto Hardy.

When I installed it in January, I couldn't get the driver to work.
[http://bugs.freedesktop.org/show_bug.cgi?id=13942](http://bugs.freedesktop.org/show_bug.cgi?id=13942)
This was fixed in Git source, so I compiled my own driver for Hardy.

Finally X would start and my display worked fine. The only problem was, whenever I logged out of X or went to shutdown, my system would freeze.

I came across a solution (modifying yaboot.conf) that seems to work well.
[http://bugs.freedesktop.org/show_bug.cgi?id=14446](http://bugs.freedesktop.org/show_bug.cgi?id=14446)

[COLOR="Red"]**-- Compile your own Mac Mini radeon driver for Hardy --**[/COLOR]

Use these instructions at your own risk.

**1. Remove "xserver-xorg-video-ati" using Synaptic.**

**2. Compile new driver from the latest source.**
If you have the required development libraries and compiler installed, the following will compile a new driver for you:

```
git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati
cd xf86-video-ati/
./autogen.sh
make clean
make
sudo make install
```

**3. Install new driver.**
If you are using X and X is currently using the ati radeon driver, you need to do this whilst X isn't running. If you are using fbdev, you could probably do this whilst X is running.

```
sudo cp --verbose /usr/local/lib/xorg/modules/multimedia/* /usr/lib/xorg/modules/multimedia/
sudo cp --verbose /usr/local/lib/xorg/modules/drivers/* /usr/lib/xorg/modules/drivers/

```
This will copy the drivers from where they were compiled to to where X is looking for them.

**4. Modify /etc/yaboot.conf**

```
sudo nano /etc/yaboot.conf
```

For each boot option in this file, modify the append line:

```
append="nosplash video=radeonfb:1280x1024-24@60"
```

Replace 1280x1024 with your resolution, the 24 is for the colour depth and 60 is the refresh rate of your monitor. Adjust as necessary.

Save the file, exit nano and run:

```
sudo ybin -v
```

(You need to do this whenever you modify /etc/yaboot.conf)

**5. If you are using the fbdev driver, you need to modify /etc/X11/xorg.conf and change the driver to "ati" or "radeon".**

For the yaboot changes to work, you need to reboot.

I'm going to compile the latest driver from source and upload them.

---

### Post by BladeMelbourne on 2008-04-16
The compiled driver seems ok.
Under the Hardy 2.6.24 kernel, glxgears reports 850 fps.
Under the Gutsy 2.6.22 kernel (although the rest of the system is Hardy), glxgears reports 1250 fps.

[COLOR="Red"]**-- Download my Mac Mini radeon driver for Hardy (no compilation required) --**[/COLOR]

Use these drivers and instructions at your own risk.
[http://tmodev.imxsoftware.com/modules.tar.gz]("http://tmodev.imxsoftware.com/modules.tar.gz")

**1. Remove "xserver-xorg-video-ati" using Synaptic.**

**2. Extract the files from the above archive, then install them to the correct location.**
The files in the multimedia directory go here:
/usr/lib/xorg/modules/multimedia/
The files in the drivers directory go here:
/usr/lib/xorg/modules/drivers/
You need root privs to do this. If you are using X and X is currently using the ati radeon driver, you need to do this whilst X isn't running. If you are using fbdev, you could probably do this whilst X is running.

**3. Modify /etc/yaboot.conf**

```
sudo nano /etc/yaboot.conf
```

For each boot option in this file, modify the append line:

```
append="nosplash video=radeonfb:1280x1024-24@60"
```

Replace 1280x1024 with your resolution, the 24 is for the colour depth and 60 is the refresh rate of your monitor. Adjust as necessary.

Save the file, exit nano and run:

```
sudo ybin -v
```

(You need to do this whenever you modify /etc/yaboot.conf)

**4. If you are using the fbdev driver, you need to modify /etc/X11/xorg.conf and change the driver to "ati" or "radeon".**

For the yaboot changes to work, you need to reboot.

Good luck, let us know how you go.

---

### Post by slacka-vt on 2008-04-16
> I was wondering if anyone had any ideas? Upgrading to herdy perhaps?

I feel very confident that if you installed Hardy at this point, you would not have that problem.

~s

BTW, I'm using Hardy on a G5 with ATI Radeon, I can verify that Hardy uses the ATI driver you like.

---

### Post by kingmoffa on 2008-04-21
I've upgraded :) 

Didn't go THAT well.  Installing a open office component and it went tits up.

dpkg-reconfigure -a took many hours to sort itself out asking lots of questions. 

But in the end it worked. 

Now , my xorg.conf is pretty blank so I guess everything will be done by auto detection. (thanks for overwriting my own ubuntu!) 

From the logs of /var/log/Xorg.0.log it seems that the radeon driver is indeed loading. However, my computer is really really slow.

X is taking up ~50% of CPU ALL OF THE TIME.

I will try the solution above to see if that sorts it. 

This is my work computer and they are all mac fan boys.  I hate ati and nvidia. I wish this thing had an intel graphic chip.

---

### Post by stream303 on 2008-04-21
Is it really X doing that?  When I ran top, or better yet download and run HTOP, I found Network Manager sucking up all my resources back in Gutsy and had to disable it rather than remove it....

---

### Post by kingmoffa on 2008-04-22
After trying the newer driver my screen was fuzzy. I am not sure where the problem lied. So I reverted back to the stock herdy driver.

Whatever it did, it fixed things. As now my screen works fine - X is no longer taking all the CPU. X has also automatically detected hardware and 3D acceleration is working. 


Im a bit more happy now.

---

