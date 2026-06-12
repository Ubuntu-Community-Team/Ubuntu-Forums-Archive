---
title: "[SOLVED] Installing Nvidia drivers... cannot run... Need lotta help here..."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Agenator on 2007-07-20
I am following the instructions from this website: [http://www.compiz.org/NVidia](http://www.compiz.org/NVidia)
I am trying to install the lateste Nvidia drivers but whenever I type sudo sh NVIDIA-Linux-x86-100.14.1-pkg1.run it always says that it cannot run it. I dl'd the file to my desktop so I assume that in the terminal myname@ubuntu means that it is pointing to the desktop right?
If not how can I get it to point there? Also I read that you need to edit the restricted drivers but whenever i open that up it says:

> You need to install the package

  linux-restricted-modules-2.6.20-16-lowlatency

for this program to work.

I looked for the file online but couldn't find anything. I also read that I needed to install glx... cant find that dl or instructions anywhere. Please somebody help me get this working.
AGENATOR

*stats*
Core 2 duo
2gb ddr2 ram
ubuntu fiesty
Nvidia 8600 GTS 
Intel DG965WH mb

---

### Post by Moop on 2007-07-20
The easiest way to install the latest Nvidia drivers is to use Envy. It's not supported by Ubuntu but has worked well for me.  

The official way to install the Nvidia driver is to use the Restricted Driver Manager in System-Administration. 

To change to your desktop directory ```
cd Desktop
```  It's case sensitive.

---

### Post by ravenwere on 2007-07-20
No it is pointing to your home directory /home/myname

cd Desktop 
puts you in the correct directory

You can check the file listing by typing
dir

PS note the capital letter in Desktop

Regards,

R

---

### Post by bodhi.zazen on 2007-07-21
> **Agenator said:**
> I am following the instructions from this website: [http://www.compiz.org/NVidia](http://www.compiz.org/NVidia)
I am trying to install the lateste Nvidia drivers but whenever I type sudo sh NVIDIA-Linux-x86-100.14.1-pkg1.run it always says that it cannot run it. I dl'd the file to my desktop so I assume that in the terminal myname@ubuntu means that it is pointing to the desktop right?
If not how can I get it to point there? Also I read that you need to edit the restricted drivers but whenever i open that up it says:



I looked for the file online but couldn't find anything. I also read that I needed to install glx... cant find that dl or instructions anywhere. Please somebody help me get this working.
AGENATOR

*stats*
Core 2 duo
2gb ddr2 ram
ubuntu fiesty
Nvidia 8600 GTS 
Intel DG965WH mb

Install the restricted modules :

```
sudo apt-get install linux-restricted-modules-2.6.20-16-lowlatency
```

You also need to install build-essential and your kernel headers ....

---

### Post by bigfox on 2007-07-21
If you are using Ubuntu 7.04 Feisty Fawn you can just go to System -> Administration -> Restricted Driver Manager and install it from there.

---

### Post by cheesewhiz on 2007-07-21
> **bigfox said:**
> If you are using Ubuntu 7.04 Feisty Fawn you can just go to System -> Administration -> Restricted Driver Manager and install it from there.

That's what I've been doing,  but when I reinstalled Ubuntu the other day and did it, it did something and now my X wont start.

---

### Post by Saner on 2007-07-21
uname -a
*Note the kernel version*
sudo apt-get install linux-headers-*(your kernel version)*
wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
(may have to su, I su out of habit for some reason I cant get into the habbit of using sudo)
Next > Next > Next > Next > Next (etc etc etc....)

Reboot


That worked for me (I am writing this from memory so you may have to adjust a little) (at your own risk of course)

---

### Post by ayenack on 2007-07-21
I'd think that a backup was made during the install of the nvidia drivers. Try this in terminal.

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Then reboot. 

sudo shutdown now -r

This might work. You'll just have to hope that there was a backup. If you're ever going to edit/reconfigure your xorg.conf make a backup like this.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

It's important to use capitol "X" in all instances of typing "X11".

Best of luck. ayenack.

Take a look at these post. Read through them there are some points of interest for you.
[http://ubuntuforums.org/showthread.php?t=453942&highlight=ayenack]("http://ubuntuforums.org/showthread.php?t=453942&highlight=ayenack")

Envy seems to do the job for most people. To install take a look at [this]("http://lunapark6.com/envy-easy-way-to-install-nvidia-drivers-in-ubuntu.html")

---

### Post by Agenator on 2007-07-21
thanks guys I just did it the lazy way and used envy :P it workedlike a charm and now Im having a load of fun with beryl.
AGEN

---

