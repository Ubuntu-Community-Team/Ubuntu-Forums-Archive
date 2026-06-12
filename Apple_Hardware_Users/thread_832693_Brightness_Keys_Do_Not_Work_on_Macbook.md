---
title: "Brightness Keys Do Not Work on Macbook"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by sixsidepentagon on 2008-06-17
Hi, I just got a new Macbook 4.1 (santa rosa, right?), and I installed Ubuntu Hardy on it. I've gotten nigh everything to work fine on it so far, except for the brightness key functions (F1 and F2) (and the accelerometer to play physical neverball, but I read that hasn't been fixed yet, right?). Note that the sound keys and eject key works fine. I've installed the newest version of pommed already.
If there isn't a fix for the keys, is there a way to change the brightness from the software? I'd really like to conserve as much power as possible, and I really don't like brighter screens. Thanks in advance!
(Note: I suppose this might be a related problem. Is there a way to get the F3 button to also activate the scale feature in Compiz? I've messed with the settings manager and haven't been able to hotkey it)

---

### Post by cyberdork33 on 2008-06-17
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

have you done the keyboard fixes?

---

### Post by sixsidepentagon on 2008-06-18
I thought I did, but a closer examination this time of the instructions say that:

The current release of pommed does not support the macbook, but support exists in the svn version. You can build from svn head yourself, or use a pre-built package. If you are using the ppa from the kernel steps, an updated pommed package is available.

And here I just decided to suda apt-install pommed! I really have no clue what an svn version is, or how to get a pre-built package. Any kind poster'd like to enlighten me?

Thanks again.

---

### Post by cyberdork33 on 2008-06-18
yea there are newer versions of pommed in the mactel-support PPA:
[https://edge.launchpad.net/~mactel-support/+archive](https://edge.launchpad.net/~mactel-support/+archive)

---

### Post by sixsidepentagon on 2008-06-18
Sorry I'm a noob. Could you give me the commands to install from that?

---

### Post by cyberdork33 on 2008-06-18
> **sixsidepentagon said:**
> Sorry I'm a noob. Could you give me the commands to install from that?
You will see the pommed package listed near the bottom of the page... click the little triangle to expand it down, and you will see the various packages. Get the 32 or 64bit deb (depending on your install). When it is downloaded, double-clicking should install.

---

### Post by hoarycripple on 2008-06-19
Macbook 4.1 is penryn.  I have the penryn macbook and you indeed need a newer version of pommed.  You should also get the pre-built hid module from this thread:  [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127") or direct link:  [http://launchpadlibrarian.net/14649798/hid.tar.gz]("http://launchpadlibrarian.net/14649798/hid.tar.gz")

Also, a quick tip for using the screen brightness/volume/backlight keys:  Gnome pops up a dialog everytime these keys are hit and so does pommed.  This gives a very strange effect where the pommed dialog is on top and the gnome popup is on the bottom.  To disable the gnome popup, go to keyboard shortcuts and disable the volume/backlight/brightness macros.  This can be done in gconf-editor also if the options are not available through the keyboard shortcuts preferences dialog.

Ubuntu on macbook is great :)

Happy linuxgeeking,

HC

---

### Post by cyberdork33 on 2008-06-19
> **hoarycripple said:**
> Macbook 4.1 is penryn.  I have the penryn macbook and you indeed need a newer version of pommed.  You should also get the pre-built hid module from this thread:  [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127) or direct link:  [http://launchpadlibrarian.net/14649798/hid.tar.gz](http://launchpadlibrarian.net/14649798/hid.tar.gz)

Also, a quick tip for using the screen brightness/volume/backlight keys:  Gnome pops up a dialog everytime these keys are hit and so does pommed.  This gives a very strange effect where the pommed dialog is on top and the gnome popup is on the bottom.  To disable the gnome popup, go to keyboard shortcuts and disable the volume/backlight/brightness macros.  This can be done in gconf-editor also if the options are not available through the keyboard shortcuts preferences dialog.

Ubuntu on macbook is great :)

Happy linuxgeeking,

HC

MacBook4,1 or MacBookPro4,1 ;)

---

### Post by hoarycripple on 2008-06-19
I misread the original post :(

Please disregard my last post.

Thanks cyberdork33.

---

### Post by sixsidepentagon on 2008-06-19
Awesome, thanks it worked!
And thanks for the concern, HoaryCripple, I appreciate it anyways.

---

### Post by windfix on 2008-10-09
I also have MBP 4.1 Penryn, and have gotten everything working except the brightness controls.  I am running Intrepid 8.10 and pommed 1.21.  I don't undersand what do do with the hid module... details?

The screen brightness is killing my eyes.

---

### Post by kosumi68 on 2008-10-09
> **windfix said:**
> I also have MBP 4.1 Penryn, and have gotten everything working except the brightness controls.  I am running Intrepid 8.10 and pommed 1.21.  I don't undersand what do do with the hid module... details?

The screen brightness is killing my eyes.

I believe pommed won't be needed in Intrepid, see this thread: [http://ubuntuforums.org/showthread.php?t=904508](http://ubuntuforums.org/showthread.php?t=904508)

---

### Post by windfix on 2008-10-10
I am running Intrepid already

---

### Post by cyberdork33 on 2008-10-10
> **windfix said:**
> I am running Intrepid already
Please read the thread that is linked to above. It goes through more detail. The fixed software may not be available yet, but should make it before the final version of Intrepid.

---

### Post by bskerr on 2008-10-12
Hi there,

My brightness keys work fine, but every time I start up, the brightness is maximum again, and I have to dim it. Is there a config file I can edit to set the default brightness?

Thanks!

---

### Post by bskerr on 2008-10-13
Update: found sections in pommed.conf where I ought to be able to set initial brightness, however no matter how I set it, display is always maximally bright upon startup. Here is the relevant section of pommed.conf:

> # Intel 945GM, 965GM backlight control (MacBook, MacBook Air)
lcd_gma950 {
        # initial backlight level [0x6f] (0x1f - 0x94 usually, -1 to disable)
        init = 0x1f
        # step value (0x01 - 0x20)
        step = 0x0f
        # backlight level when on battery [0x40] (0x1f - 0x94 usually, 0 to disable)
        on_batt = 0x40
}

Other changes to the config file (i.e. audio step value) DO make a difference.

Sorry for being a noob; thanks for any help.

---

### Post by kosumi68 on 2008-10-13
bskerr,

what macbook model do you have?
```

sudo dmidecode | grep 'Product Name:'

```

what ubuntu version are you running?
```

uname -r
dpkg -s xorg | grep Version

```

are you running pommed?

---

### Post by bskerr on 2008-10-13
Hi Kosumi,

```
$ sudo dmidecode | grep 'Product'
	Product Name: MacBook4,1
	Product Name: Mac-F22788A9
$ uname -r
2.6.24-19-generic
$ dpkg -s xorg | grep Version
Version: 1:7.3+10ubuntu10.2

```

I have installed pommed and it appears to be running.

---

### Post by kosumi68 on 2008-10-13
You might want to try this:
```

sudo /etc/init.d/pommed stop
sudo <path-of-pommed-binary>/pommed -f

```
and observe the initial settings which should be displayed in the terminal.

---

### Post by _mario_ on 2008-10-13
Hi bskerr,

I probably cannot really help you as I own a MacBookPro not a MacBook, but might point out some things to think about. 

> **bskerr said:**
> Update: found sections in pommed.conf where I ought to be able to set initial brightness, however no matter how I set it, display is always maximally bright upon startup.

1. With "startup", do you really mean restarting the machine or resuming from hibernation/suspend? According to the sources, pommed only set this initial brightness when it starts while the firmware always sets the brightness to maximum on "power-up".

2. Since your brightness keys are working after successful boot and you seem to be running Hardy, the brightness is changed through pommed. Is there any driver that has to be loaded? On my MacBookPro a driver (mbp_nvidia_bl) must be loaded in /etc/modules *before* pommed starts (auto-loading doesn't work right now). Assuming the answer is yes, your initial ramdisk (where the kernel gets its initial drivers from) might be missing the driver. Very unlikely. This should not happen. But to be sure, does ```
update-initramfs -k all -u
``` and rebooting the machine help?

ciao,
Mario

---

### Post by bskerr on 2008-10-17
Thanks for the responses and sorry for the slow reply, I was out of town for a few days.

Mario, I did mean "power up." I don't know if a driver needs to be loaded or not. I tried the update-initramfs command, but to no avail. I'm very new to Macs -- when you say that the firmware sets the brightness to maximum, I'm not entirely certain what the firmware is or if it might be configured.

Kosumi, pommed -f reports exactly the values I have set in the configuration file, which are clearly not correct (as I have the value far lower than the maximum, yet on power up the brightness can only be adjusted down, not up).

I appreciate the help -- to be honest, if I have to adjust the brightness a bit each time I boot up, it's not the end of the world. Just would have been nice to have it set itself automatically.

---

