---
title: "8800GT drivers"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by clykke on 2008-04-10
Hey

So, I finally got my Ubuntu installed (32-bit though. Does it make any difference even though I have a 64-bit CPU?) and would like to install drivers for my 8800GT. I downloaded this file: NVIDIA-Linux-x86-169.12.pkg1.run from [http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html)

I opened the terminal, changed directory to where I placed the file, and typed "sh NVIDIA-Linux-x86-169.12.pkg1.run". I then received this message: "sh: Can't open NVIDIA-Linux-x86-169.12.pkg1.run".

Am I doing anything wrong? Any ideas?

---

### Post by mikeyphi on 2008-04-10
> **clykke said:**
> Hey

So, I finally got my Ubuntu installed (32-bit though. Does it make any difference even though I have a 64-bit CPU?) and would like to install drivers for my 8800GT. I downloaded this file: NVIDIA-Linux-x86-169.12.pkg1.run from [http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html)

I opened the terminal, changed directory to where I placed the file, and typed "sh NVIDIA-Linux-x86-169.12.pkg1.run". I then received this message: "sh: Can't open NVIDIA-Linux-x86-169.12.pkg1.run".

Am I doing anything wrong? Any ideas?

Hi there and welcome!
Not sure why that didn't work however, Ubuntu has support for your graphics card - you just need to open the 'Restricted Drivers Manager' and install the driver.

---

### Post by clykke on 2008-04-10
And where exactly do I find that? :)

---

### Post by clykke on 2008-04-10
I found it, under the System Menu. When I click it, it tells me that: Your system doesn't need any restrcited drivers. 

Can someone explain this to me?

---

### Post by bodhi.zazen on 2008-04-10
You can use envy to install the driver

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You should remove nvidia-glx first, if it is installed.

The manual method is as follows. Note: You need to stop X (your GUI) to install teh nvidia driver, so print this out (or write it down).

[http://ubuntuforums.org/showpost.php?p=4148573&postcount=3](http://ubuntuforums.org/showpost.php?p=4148573&postcount=3)

To make the nvidia driver you downloaded you need to make it executable

```
chmod a+x NVIDIA*
```

To install the drive, use ctrl-alt-F1 to go to the console (command line).

Use ```
sudo /etc/init.d/gdm start
``` to restart your GUI

---

### Post by stchman on 2008-04-10
> **clykke said:**
> Hey

So, I finally got my Ubuntu installed (32-bit though. Does it make any difference even though I have a 64-bit CPU?) and would like to install drivers for my 8800GT. I downloaded this file: NVIDIA-Linux-x86-169.12.pkg1.run from [http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_169.12_uk.html)

I opened the terminal, changed directory to where I placed the file, and typed "sh NVIDIA-Linux-x86-169.12.pkg1.run". I then received this message: "sh: Can't open NVIDIA-Linux-x86-169.12.pkg1.run".

Am I doing anything wrong? Any ideas?

Yes, I used Envy to install the 169.12 drivers in Feisty.  I have an 8800GT and it works excellent.  I even can use the Twin View for multi monitors.

If you have Gutsy or earlier then use Envy 0.9.10 and select manual install.  The 169.12 driver will be there.  Highlight it and go.  Make sure you ahve uninstalled any previous nvidia driver by using the Envy uninstall nvidia driver.

Let Envy modify your xorg.conf for you and reboot.

---

### Post by clykke on 2008-04-10
> **bodhi.zazen said:**
> You can use envy to install the driver

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You should remove nvidia-glx first, if it is installed.

The manual method is as follows. Note: You need to stop X (your GUI) to install teh nvidia driver, so print this out (or write it down).

[http://ubuntuforums.org/showpost.php?p=4148573&postcount=3](http://ubuntuforums.org/showpost.php?p=4148573&postcount=3)

To make the nvidia driver you downloaded you need to make it executable

```
chmod a+x NVIDIA*
```

To install the drive, use ctrl-alt-F1 to go to the console (command line).

Use ```
sudo /etc/init.d/gdm start
``` to restart your GUI

How do I figure out if nvidia-glx is installed? And should I remove it first even if I use Envy?

---

### Post by stchman on 2008-04-10
> **clykke said:**
> How do I figure out if nvidia-glx is installed? And should I remove it first even if I use Envy?

Check in Synaptic for nvidia-glx.

---

### Post by bodhi.zazen on 2008-04-10
> **clykke said:**
> How do I figure out if nvidia-glx is installed? And should I remove it first even if I use Envy?

sudo apt-get remove nvidia-glx

If it is installed that will remove it.

Yes, you should remove it first, it is easier that way.

---

### Post by clykke on 2008-04-11
Alright, I'll try this when I get home from work today. However, I am an absolute beginner regarding ubuntu (and linux in general) and I have no idea how to do most of the stuff you tell me to do, like installing Envy, removing old drivers, turning of my GUI (stopping X).

I have been trying to find guides, and how-tos, but haven't found anything I feal really comfortably with. 

As far as I have understood, this is what I need to do, and in the following order:

- Download and install envy
- Remove nVidia-Glx (it is installed btw, but there is also something called nVidia-glx.dev or something)
- Turn off my GUI
- Install the driver


Is this correct? Can I use envy to install the driver when my GUI has been disabled?

Anyways, of the above mentioned tasks, I can handle one of them. Which would be removing the nVidia-glx, because it as already been explained in this thread how to do it.

Can someone guide me through the rest? I mean, a seriously newbie-friendly guide that tells me which menues and programs I should run, what I should type, and in what order.

I would very much appreciate it.

Thank you in advance, and thank you for the help you all have provided so far.

---

### Post by bodhi.zazen on 2008-04-11
I think there is a misunderstanding.

You need to :

1. Remove nvidia-glx.

2. Install the Nvidia driver. You can do this with envy from the gui. If you do NOT want to use envy, THEN and only then will you need ot download the driver directly from Nvidia, stop X, and manually install teh driver.

Either envy OR manual installation, not both.

3. After the driver is installed, re-start X (log out and then back on) and then run :

```
gksu nvidia-settings
```

4. If for some reason envy fails, then you will need to install the drier manually. You do NOT need to remove it with envy first, just install the driver you download from nvidia.

---

### Post by clykke on 2008-04-11
Oh, thank you, that cleared up a few things. 

I need to run "gksu nvidia-settings" even if I use envy? What does this commando do. 

I am sorry for all of these stupid questions. Please bear with me :)

---

### Post by bodhi.zazen on 2008-04-11
gksu = run a graphical application as root This allows you to save your settings. (kdesu for KDE) .

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

nvidia-settings allows you to configure your monitor(s). Resolution, twinview, frequency, etc. Twinview = 1 large shared desktop across multiple monitors.

Note: see my first post if you are still having problems after installing the nvidia driver, there may be a small edit you may need to make ....

---

### Post by herbster on 2008-04-11
You want to run nvidia-settings as root for the purpose of saving your settings. The changes you make to fundamentals like screen resolution are saved to a very important file called xorg.conf, which resides in /etc/X11/. This file is owned by root, so if you run nvidia-settings normally, you can hit save changes but the defaults will be restored when you reboot.

---

### Post by clykke on 2008-04-12
Thank you. I think I have installed the driver correctly. Any way to verify that things are running as good as possible?

---

### Post by herbster on 2008-04-12
```
glxinfo | grep direct
```

What's the output? If Yes, then you're pretty much set.

Either the driver is being used and is functional, or it's not; nvidia-settings will tell you that in the information section of it.

---

