---
title: "Anyone got a fx5700le going"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-05-27
hi has anyone got a Nvidia Geforce fx 5700le 256mb Graphics card to do 3d acceleration I feel I've tried everything to no avail (using Feisty Fawn 7.04 ) Please help.

---

### Post by fongs on 2007-05-28
> **fongs said:**
> hi has anyone got a Nvidia Geforce fx 5700le 256mb Graphics card to do 3d acceleration I feel I've tried everything to no avail (using Feisty Fawn 7.04 ) Please help.
Is there no one who has got this to work . After an extensive search through forum it appears that there is not a thread on this topic.

---

### Post by dpzektor on 2007-05-28
Did you try the restricted drivers manager?

---

### Post by fongs on 2007-05-28
> **dpzektor said:**
> Did you try the restricted drivers manager?

Hi Yes i have tried the restricted drivers and it says:Your hardware does not need any restricted drivers.

---

### Post by fongs on 2007-05-28
> **dpzektor said:**
> Did you try the restricted drivers manager?

I've tried sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run and get.

---

### Post by fongs on 2007-05-28
Please someone must know whats going on here

---

### Post by igknighted on 2007-05-28
> **fongs said:**
> Please someone must know whats going on here

please, wait 24 hours before bumping a topic.  Much of Europe and the Americas have been asleep during this timespan so the forums are quite slow.

As for you problem, I would recommend not using the NVIDIA-Linux-x86-1.0-9755-pkg1.run file from Nvidia.  It can work with Ubuntu, but there are much easier alternatives.  Open a terminal window and type:
```
sudo apt-get install nvidia-glx-new
```
and then
```
sudo nvidia-xconfig
```

I heard a rumor that the xconfig command does not come with the version in the repo's.  If this is the case, simply open the xorg config file with this command:
```
gksudo gedit /etc/X11/xorg.conf
```
and scroll down until you see the section "Device".  There will be a driver listed there along with your video card,  The driver will read "nv".  Change it to "nvidia".  Then save and exit the file.  Now save any work you have open and hit ctrl+alt+backspc to restart the xserver, and it should use the new driver when it comes back.

---

### Post by fongs on 2007-05-28
thanks for help

---

### Post by fongs on 2007-05-28
No good Champ left me with a Blank screen any alternatives, maybe directions down the path I was aready heading

---

### Post by fongs on 2007-05-28
New day fresh head lets see if theres any help out there.

---

### Post by fongs on 2007-05-29
Help Please

---

### Post by RomeReactor on 2007-05-29
Hi fongs, open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **nvidia** and post here the packages already installed.

---

### Post by fongs on 2007-05-29
> **RomeReactor said:**
> Hi fongs, open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **nvidia** and post here the packages already installed.
Mate just have to say you are the best help I've had here. It doesn't appear that i have any.

---

### Post by RomeReactor on 2007-05-29
Now that Synaptic is open, press the **Search** button, enter **nvidia**, and see what is listed as installed.

---

### Post by fongs on 2007-05-29
> **RomeReactor said:**
> Hi fongs, open Synaptic (System-->Administration-->Synaptic Package Manager) and search for **nvidia** and post here the packages already installed.

Sorry found search here it is.

---

### Post by RomeReactor on 2007-05-29
What is the output of this:
```
glxinfo | grep rendering
```
If it's "direct rendering: No", then try this: First, back up xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Next, let's try to enable the drivers already installed:
```
sudo nvidia-glx-config enable
```
Now, reboot, and if all goes well, after you login, run the first command in the terminal:
```
glxinfo | grep rendering
```
If it still doesn't say yes, we'll try something else.

Note: If after the reboot you get a black screen (the terminal) saying the xserver couldn't be started, you'll need to restore xorg (it would be a good idea to copy the following 2 commands on paper to use if this happens):
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and
```
sudo reboot
```
Remember to copy the commands *exactly* as they appear here.

---

### Post by fongs on 2007-05-29
> **RomeReactor said:**
> What is the output of this:
```
glxinfo | grep rendering
```
If it's "direct rendering: No", then try this: First, back up xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Next, let's try to enable the drivers already installed:
```
sudo nvidia-glx-config enable
```
Now, reboot, and if all goes well, after you login, run the first command in the terminal:
```
glxinfo | grep rendering
```
If it still doesn't say yes, we'll try something else.

Note: If after the reboot you get a black screen (the terminal) saying the xserver couldn't be started, you'll need to restore xorg (it would be a good idea to copy the following 2 commands on paper to use if this happens):
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and
```
sudo reboot
```
Remember to copy the commands *exactly* as they appear here.

The answer to to the first is attached. To scared to do next step until you say to.

---

### Post by RomeReactor on 2007-05-29
Hmmm... I'm not sure about this, but it seems we need to specify what display to use; let's try this first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to backup xorg, and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure your X server (the display).

Remember to keep the follwing 2 commands at hand, on a piece of paper or a notepad, to use if you can't get back to your desktop after a reboot:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
```
sudo reboot
```

---

### Post by fongs on 2007-05-30
> **RomeReactor said:**
> Hmmm... I'm not sure about this, but it seems we need to specify what display to use; let's try this first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to backup xorg, and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure your X server (the display).

Remember to keep the follwing 2 commands at hand, on a piece of paper or a notepad, to use if you can't get back to your desktop after a reboot:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
```
sudo reboot
```

Do i change from vesa to nvidia.

---

### Post by RomeReactor on 2007-05-30
No need to change that yet. Assuming you already ran this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
let's see if a correct display has been found:
```
glxinfo | grep rendering
```

---

### Post by fongs on 2007-05-30
> **RomeReactor said:**
> No need to change that yet. Assuming you already ran this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
let's see if a correct display has been found:
```
glxinfo | grep rendering
```

same result as attached also when i sudo dpkg-reconfigure -phigh xserver-xorg then change nvidia i get a blank screen on reboot do you know if there is an official compatible GPU list for this 
Thanks for your patients .

---

### Post by RomeReactor on 2007-05-30
I tried searching for a compatibility list and couldn't find any, sorry. Did you recover your X server?

---

### Post by RomeReactor on 2007-05-30
I still think that xorg can't find the correct display, though I could be wrong. What does this say?:
```
sudo lshw -C display
```

---

### Post by fongs on 2007-05-30
> **RomeReactor said:**
> I still think that xorg can't find the correct display, though I could be wrong. What does this say?:
```
sudo lshw -C display
```

Yes full recovered see attachment. Don't worry about the compatibility Guide I could not find one neither

---

### Post by RomeReactor on 2007-05-30
Ok, according to that information, your display is **pci@02:00.0**; now, I'm not certain that this will work, but it seems odd that your xorg.conf doesn't list a **Busid** entry for your card. This is my card's entry in xorg.conf:
```
Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
```
meaning that my card is at **pci@01:00.0**. So let's try to add that to your xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
scroll down to **Section "Device"**, which from your previous thread looks like this:
```
Section "Device"
Identifier "Nvidia GeForce Fx5700le"
Driver "nvidia"
EndSection
```
and add the following lines
```
Busid           "PCI:2:0:0"
Option          "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
Option          "NoLogo"        "True"
```
after **Driver "nvidia"**, so that section of your file looks like this:
```
Section "Device"
Identifier "Nvidia GeForce Fx5700le"
Busid           "PCI:2:0:0"
Option          "AddARGBVisuals"        "True"
Option          "AddARGBGLXVisuals"     "True"
Option          "NoLogo"        "True"
```
Driver "nvidia"
EndSection[/CODE]
save the file, close gedit and reboot; if that brings you to the desktop, try this
```
glxinfo | grep rendering
```

---

### Post by fongs on 2007-05-30
No I'm afraid that doesn't work either I just get a blank screen. Any other suggestions. 
Thanks again

---

### Post by RomeReactor on 2007-05-30
I really can't figure out what's wrong here. For the moment, that's all I can think of, sorry. Perhaps it would be a good idea to ask for help on IRC (irc.freenode.net, the channel is #ubuntu).

---

### Post by fongs on 2007-05-30
> **RomeReactor said:**
> I really can't figure out what's wrong here. For the moment, that's all I can think of, sorry. Perhaps it would be a good idea to ask for help on IRC (irc.freenode.net, the channel is #ubuntu).

THANKYOU SO VERY MUCH FOR ALL YOUR HELP if Ihad a heap of beans you would get them lol

---

### Post by fongs on 2007-06-04
is there anyone else that can help with this delma. All help is welcome.

---

### Post by fongs on 2007-06-04
> **RomeReactor said:**
> I really can't figure out what's wrong here. For the moment, that's all I can think of, sorry. Perhaps it would be a good idea to ask for help on IRC (irc.freenode.net, the channel is #ubuntu).

Don't know how to use irc. But i have a old graphics card maybe you could help me remove all the junk I've put in drivers and install this Riva tnt Gpu

---

