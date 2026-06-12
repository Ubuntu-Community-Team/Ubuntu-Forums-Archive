---
title: "Black Screen AGAIN"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by jeffk14 on 2008-01-19
O.K., I'm still new at this, but now I'm having the problem of black screen & shutdown after the initial ubuntu logo. When the logo comes up and the orange bar goes across, this finishes, then the screen shuts off. The monitor actually loses signal from the comp. This is happening with Ubuntu 7.10 (both live & alt versions), Xubuntu 7.10 ( both live & alt versions) and Ubuntu 6.06 live version. I have tried setting the color depth to 16 and also the screen resolution to 1028. Black screen every time. The comp is a Gateway that was given to me and had XP working on it. I have wiped this out. 333mhz processor, 256mb ram. Not sure what video card is in it or how to find out. Any help would be greatly appreciated.

---

### Post by xeth_delta on 2008-01-19
You can find out what video card you have with
```
lshw -C video
```

Might be a graphics card driver related problem.
Try having a look at "/var/log/Xorg.0.log". The lines starting with "EE" inform about errors.

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> You can find out what video card you have with
```
lshw -C video
```

Might be a graphics card driver related problem.
Try having a look at "/var/log/Xorg.0.log". The lines starting with "EE" inform about errors.

Thanks. It says; description: VGA compatible, product: Mpact2, vendor: Chromatic research inc, physical id:0, bus info: pci@0000:01:00.0, version:41, width: 32 bits, clock: 66mhz, capabilities: pm agp agp-1.0 vga bus_master cap_list, configuration: latency=64 mingnt=8. When I try to run the /var/log/Xorg thing, it says "Permission denied".

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> Thanks. It says; description: VGA compatible, product: Mpact2, vendor: Chromatic research inc, physical id:0, bus info: pci@0000:01:00.0, version:41, width: 32 bits, clock: 66mhz, capabilities: pm agp agp-1.0 vga bus_master cap_list, configuration: latency=64 mingnt=8. When I try to run the /var/log/Xorg thing, it says "Permission denied".

You don't have to run /var/log/Xorg.0.log. It is a text file which you can read with a text editor or send the output to the console with
```
cat /var/log/Xorg.0.log
```

Just out of curiousity, can you be more specific about the specs of your computer? How old is it? How much RAM and video card memory does it have?

---

### Post by xeth_delta on 2008-01-19
Also, I don't recognize the graphics card name. Try:

```
lspci | grep -i graph
```

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> You don't have to run /var/log/Xorg.0.log. It is a text file which you can read with a text editor or send the output to the console with
```
cat /var/log/Xorg.0.log
```

Just out of curiousity, can you be more specific about the specs of your computer? How old is it? How much RAM and video card memory does it have?

When I cat/var/log/Xorg, lines of data go screaming by and end up with info about the mouse, etc. I don't know how to "scroll up" to look at what went or what to look for. The comp is a gateway with 333mhz processor, 256mb ram & not sure about the video memory.

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> Also, I don't recognize the graphics card name. Try:

```
lspci | grep -i graph
```

When I do this, I get nothing, just kicks me down a notch to a new command line.

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> When I cat/var/log/Xorg, lines of data go screaming by and end up with info about the mouse, etc. I don't know how to "scroll up" to look at what went or what to look for. The comp is a gateway with 333mhz processor, 256mb ram & not sure about the video memory.

try
```
cat /var/log/Xorg.0.log | grep EE
```

Hmmm, I am not sure there is enough memory to properly run Ubuntu (Gnome) or Kubuntu (KDE). I guess the RAM will also be shared with the video card. You should try to find in the forum whethter someone runs without any issues (K)Ubuntu.

Are Xubuntu or Fluxbuntu viable alternatives for you? Their GUIs (and the system in general) are lighter.

Let me see if I find anything about it.

Xeth

---

### Post by xeth_delta on 2008-01-19
From this link ([https://help.ubuntu.com/community/Installation/SystemRequirements?highlight=%28requirements%29]("https://help.ubuntu.com/community/Installation/SystemRequirements?highlight=%28requirements%29")) it would seem your computer should be able to at least run Ubuntu.

---

### Post by Majorix on 2008-01-19
Don't look at the absolute minimum - that's crap. Ubuntu would laugh its a-- off if it would see 300mhz processor and 64mb ram listed as the minimum.

I would take a look at the recommended minimum, and there it says you need at least 500mhz to run Ubuntu. Your ram is ok, if it's not shared with the GPU.

EDIT: With absolute minimum I mean the minimum. It seems there is another section for absolute minimum at the bottom :)

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> try
```
cat /var/log/Xorg.0.log | grep EE
```

Hmmm, I am not sure there is enough memory to properly run Ubuntu (Gnome) or Kubuntu (KDE). I guess the RAM will also be shared with the video card. You should try to find in the forum whethter someone runs without any issues (K)Ubuntu.

Are Xubuntu or Fluxbuntu viable alternatives for you? Their GUIs (and the system in general) are lighter.

Let me see if I find anything about it.

Xeth

As per my first post, I tried Xubuntu (both live and alt versions). Exact same results.

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> try
```
cat /var/log/Xorg.0.log | grep EE
```

Hmmm, I am not sure there is enough memory to properly run Ubuntu (Gnome) or Kubuntu (KDE). I guess the RAM will also be shared with the video card. You should try to find in the forum whethter someone runs without any issues (K)Ubuntu.

Are Xubuntu or Fluxbuntu viable alternatives for you? Their GUIs (and the system in general) are lighter.

Let me see if I find anything about it.

Xeth

Typing that command I get; 
"(EE) AIGLX: Screen 0 is not DRI capable"

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> Typing that command I get; 
"(EE) AIGLX: Screen 0 is not DRI capable"

Are you trying to run visual effects/compiz-fusion/beryl? From what I can understand, right now you don't have hardware acceleration enabled.

Please post the output of:
```
glxinfo | grep -i direct
```
```
glxinfo | grep -i Opengl
```

Also the contents of "/etc/X11/xorg.conf"

Please place the text between code tags (# button in the posting window)

Xeth

---

### Post by GavinZac on 2008-01-19
Blackouts like that were happening to me when my CPU fan wasn't attached properly. Overheating?

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> Are you trying to run visual effects/compiz-fusion/beryl? From what I can understand, right now you don't have hardware acceleration enabled.

Please post the output of:
```
glxinfo | grep -i direct
```
```
glxinfo | grep -i Opengl
```

Also the contents of "/etc/X11/xorg.conf"

Please place the text between code tags (# button in the posting window)

Xeth

running either of the commands gives:
"Error: unable to open display"

I really appreciate all your help. I apologize for my ignorance. I'm COMPLETELY new at Linux, but I follow instructions pretty well.:)

---

### Post by jeffk14 on 2008-01-19
I can't copy & paste text of /etc/X11/xorg.conf. I'm on another computer. The comp that I'm having problems with is not hooked to internet.

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> running either of the commands gives:
"Error: unable to open display"

I really appreciate all your help. I apologize for my ignorance. I'm COMPLETELY new at Linux, but I follow instructions pretty well.:)

Don't worry, that's how one learns, little by little. :) Are you perhaps logged as root in the command line? Run glxinfo as a regular user.

Please do post your "/etc/X11/xorg.conf", read it with a text editor, copy and paste.

---

### Post by jeffk14 on 2008-01-19
I can't open anything on that comp but a terminal from booting in recovery mode. I don't have a text editor or anything else working on it. Just the recovery terminal. That's all.

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> I can't open anything on that comp but a terminal from booting in recovery mode. I don't have a text editor or anything else working on it. Just the recovery terminal. That's all.

Ok, no problem, I wanted to know what driver it was using. Look in that file for a text fragment called <<Section "Device">>. In the case of my computer it looks like:

```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```

What driver is your computer using?

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> Ok, no problem, I wanted to know what driver it was using. Look in that file for a text fragment called <<Section "Device">>. In the case of my computer it looks like:

```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```

What driver is your computer using?

Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16

There is no reference to the driver.

---

### Post by jeffk14 on 2008-01-19
I gotta go for awhile. Be back in about 1hr. Thanks again.

---

### Post by xeth_delta on 2008-01-19
> **jeffk14 said:**
> Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 16

There is no reference to the driver.

What you showed me is the section for the screen not the driver and the video card. It should be there in the file, look again :) <<Section "Device">>

---

### Post by jeffk14 on 2008-01-19
> **xeth_delta said:**
> What you showed me is the section for the screen not the driver and the video card. It should be there in the file, look again :) <<Section "Device">>

Sorry. It flashes by too fast to read. How do I scroll back up to see what went by?

---

### Post by xeth_delta on 2008-01-20
> **jeffk14 said:**
> Sorry. It flashes by too fast to read. How do I scroll back up to see what went by?

Open the file with nano:

```
nano /etc/X11/xorg.conf
```
By the way, to scroll use shift+Up/Down arrow

---

### Post by jeffk14 on 2008-01-20
Thanks man. I'm at work right now & will be away from the computer in question til about Tuesday morning. I'll post back with my findings in a couple of days.

---

### Post by jeffk14 on 2008-01-24
Thanks xeth_delta. Finally found it.

Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"

---

### Post by xeth_delta on 2008-01-24
I've been looking for information about your video card over the internet and it seems "Chromatic Research" was bought by ATi quite some time ago. From what I understand ATi did not continue to provide support for MPACT cards. Right now I am not quite sure there is proper X support for your card.

I don't habe any good ideas right now, but what I can suggest right now to you, is to make a backup of "/etc/X11/xorg.conf", if you hadn't yet. Change the resolution of your screen to something rahter low, just to check, for instance start with 320x240. In **Section "Screen"**, **SubSection "Display"** change the line containing Modes to 320x240:
```
Modes "320x240"
```
Try like this with the "vesa" driver.

Then try some of the other drivers, Changing "vesa" for "vga", "ati", "radeon", "i810", etc, then restarting X.

With the exception of "vga", I am not sure it will work, but it is worth a try.

If I find anything else, I will let you know. Good luck!

Xeth

---

### Post by xeth_delta on 2008-01-25
JeffK14, there is another user called Smatt454 that I think has the same card as you do, he does not seem to mention any problem with it. You may want to ask him how he got his computer configured.
A thread where the card is mentioned in a lspci output is this: [http://ubuntuforums.org/showthread.php?t=574540&highlight=chromatic+research]("http://ubuntuforums.org/showthread.php?t=574540&highlight=chromatic+research")

I have also read that there are people being able to use old graphic cards with a frame buffer driver (even though performance would be lower). You could try setting your driver also to: "fbdev", &#8220;vga16fb&#8221;, &#8220;vesafb&#8221;. Have a look at this thread for reference: [http://ubuntuforums.org/showthread.php?t=197365&highlight=fbdev]("http://ubuntuforums.org/showthread.php?t=197365&highlight=fbdev") and at [http://www.xfree86.org/4.3.0/fbdev.4.html]("http://www.xfree86.org/4.3.0/fbdev.4.html") and [http://tldp.org/HOWTO/Framebuffer-HOWTO-17.html]("http://tldp.org/HOWTO/Framebuffer-HOWTO-17.html")

Xeth

---

### Post by jeffk14 on 2008-01-25
> **xeth_delta said:**
> I've been llokeing for information about your video card over the internet and it seems "Chromatic Research" was bought by ATi quite some time ago. From what I understand ATi did not continue to provide support for MPACT cards. Right now I am not quite sure there is proper X support for your card.

I don't habe any good ideas right now, but what I can suggest right now to you, is to make a backup of "/etc/X11/xorg.conf", if you hadn't yet. Change the resolution of your screen to something rahter low, just to check, for instance start with 320x240. In **Section "Screen"**, **SubSection "Display"** change the line containing Modes to 320x240:
```
Modes "320x240"
```
Try like this with the "vesa" driver.

Then try some of the other drivers, Changing "vesa" for "vga", "ati", "radeon", "i810", etc, then restarting X.

With the exception of "vga", I am not sure it will work, but it is worth a try.

If I find anything else, I will let you know. Good luck!

Xeth

Well I tried "vga & "ati", no good. Then I looked to change the resolution, but I only have "sections" when I pull up the xorg.conf file. No "subsections" are shown.

---

### Post by jeffk14 on 2008-01-25
Additionally, I tried running "lshw" to list my hardware, but again, the info scrolled by very fast. I tried to use shift+up arrow to scroll, but that doesn't work.

---

### Post by xeth_delta on 2008-01-25
> **jeffk14 said:**
> Additionally, I tried running "lshw" to list my hardware, but again, the info scrolled by very fast. I tried to use shift+up arrow to scroll, but that doesn't work.

```
lshw -C video
```
Should show you only and only the video subsystem.

Ok, I would like you to do try the following:
-Make a back-up of /etc/X11/xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```

Now, reconfigure the xserver-xorg:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions.

Now, look again for the resolution line.

---

### Post by jeffk14 on 2008-01-26
> **xeth_delta said:**
> ```
lshw -C video
```
Should show you only and only the video subsystem.

Ok, I would like you to do try the following:
-Make a back-up of /etc/X11/xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```

Now, reconfigure the xserver-xorg:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions.

Now, look again for the resolution line.

O.K., I did the backup, entered;
```
sudo dpkg-reconfigure xserver-xorg
```
I was blazing through, set resolution to lowest, then set color depth to 16. Now, after doing that, I'm stuck with this warning in the terminal;
xserver-xorg postinst warning:overwriting possibly-customised configuration
     file; backup in /etc/X11/xorg.conf.20080126081220

Won't let me do anything now, so I stopped. Don't want to lose my place & have to start over.

---

### Post by xeth_delta on 2008-01-26
> **jeffk14 said:**
> O.K., I did the backup, entered;
```
sudo dpkg-reconfigure xserver-xorg
```
I was blazing through, set resolution to lowest, then set color depth to 16. Now, after doing that, I'm stuck with this warning in the terminal;
xserver-xorg postinst warning:overwriting possibly-customised configuration
     file; backup in /etc/X11/xorg.conf.20080126081220

Won't let me do anything now, so I stopped. Don't want to lose my place & have to start over.

It says it will over-write your current xorg.conf file, but since you've already make a back-up you are safe to continue.

---

### Post by jeffk14 on 2008-01-26
Thanks, but (I know, I'm a dumba$$) exactly "how" do I continue? It appears to not be responding. I can't scroll down to hit "OK" on the white screen.

---

### Post by xeth_delta on 2008-01-26
> **jeffk14 said:**
> Thanks, but (I know, I'm a dumba$$) exactly "how" do I continue? It appears to not be responding. I can't scroll down to hit "OK" on the white screen.

No need to be that harsh with yourself :) Try changing focus with TAB, if it still does not work, try quiting with Control-C.

---

### Post by jeffk14 on 2008-01-26
O.K., hitting "TAB" gives "display all 1552 lines?" (y or n)

I hit "n" & get a new command line, so I hit Ctrl + C and get a new command line. 

Soooo I restarted computer (Xubuntu 7.1), get the Xubuntu logo with "bar" loading  across the bottom, that finishes, short pause, black screen, same as before.

---

### Post by jeffk14 on 2008-01-26
xeth_delta, thanks so much for all your help. I finally gave up after running a trial of "puppy" & it wouldn't work either. The solution was to grab an old junk machine I had lying around, yank an old PCI video card out of it, slap it in the computer I've been working on, reconnected the monitor and off she went. Thanks for the education. I'm gonna keep reading everything I can on Linux and experimenting in my basement "lab".

---

### Post by xeth_delta on 2008-01-27
> **jeffk14 said:**
> xeth_delta, thanks so much for all your help. I finally gave up after running a trial of "puppy" & it wouldn't work either. The solution was to grab an old junk machine I had lying around, yank an old PCI video card out of it, slap it in the computer I've been working on, reconnected the monitor and off she went. Thanks for the education. I'm gonna keep reading everything I can on Linux and experimenting in my basement "lab".

Glad you got your computer working, but that MPACT2 card does not seem to have good support.
Putting in another graphics card was obviously the easiest solution. For some reason I don't recall I thought that machine was a laptop, and hence was stuck with the card.

In any case, good it's working now, good luck!
Xeth

---

