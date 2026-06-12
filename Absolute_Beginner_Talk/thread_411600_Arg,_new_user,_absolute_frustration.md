---
title: "Arg, new user, absolute frustration"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Amorget on 2007-04-17
I just installed 6.10 on my Dell 9300 laptop with the NVIDIA 6800 Go, 2 ghz proc, and 2 gigs of ram.  It runs okay, though video stuff is very slow to respond when compared to Windows, which makes me really unhappy considering the footprint that Ubuntu has compared to Windows XP it shouldn't be slow to respond.  By slow to respond I mean I click, it wait for a second, then the UI responds.

So, my frustrations are:  The Alps touchpad is WAYYY to sensative for touch-to-click.  I cannot find anywhere to turn it down.

Second:  The only reason I tried Ubuntu was for the 3d desk top that was displayed in the Vista vs Linux YouTube video.  I tried to enable/install it and nothing works.

Third - I cannot figure out what version of the NVIDIA driver I am using, and I cannot get the NVIDIA .run file to well... run.  I logged in as root as it complained when I didn't run as root.  Then it complained that I was running xServer.  I was thinking that may be why the UI is so slow and the effects don't work all the time.

Last, and minor, if I try to switch user the touchpad gets disabled.

I used Debian a little on a server, I got mildly proficient to move around in the Command Line environment and editing stuff.  I am overall very new to Linux, however so far it has been a real PITA to just install a driver.  I have other complaints but I don't need to vent here...

---

### Post by devnulljp on 2007-04-17
Use Envy to install the correct drivers for your nvidia card - it takes the pain out of the pita.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
[http://ubuntuforums.org/showthread.php?p=2416172](http://ubuntuforums.org/showthread.php?p=2416172)

---

### Post by Amorget on 2007-04-17
> **devnulljp said:**
> Use Envy to install the correct drivers for your nvidia card - it takes the pain out of the pita.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
[http://ubuntuforums.org/showthread.php?p=2416172](http://ubuntuforums.org/showthread.php?p=2416172)

Nope, no love for me.  

Error: dependency is not satisfied: module-assistant.  I ran the updates command (I think... found that in another post) and it still doesn't work.

---

### Post by RomeReactor on 2007-04-17
Hi. Have you tried installing the drivers through Synaptic (System-->Administration-->Synaptic Package Manager)? If not, search for **nvidia-glx** and install that; after it finishes installing, open a terminal (Applications-->Accessories-->Terminal) and enter

```
sudo nvidia-glx-config enable
```

If you already have the Nvidia drivers installed, then, still from the terminal, enter

```
gksudo gedit /etc/X11/xorg.conf
```

and scroll to **Section "Device"** to see if the **Driver** reads **"nvidia"**; also there's a couple of options you can add so that section of the file looks like this:

```
Section "Device"
        Identifier      "YOUR_CARD_HERE"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel" "true"
```

Note that you **must not** change the BusID if it's different on your file. Save it and close gedit, and reboot. See if video is more responsive now.

---

### Post by Amorget on 2007-04-17
> **RomeReactor said:**
> Hi. Have you tried installing the drivers through Synaptic (System-->Administration-->Synaptic Package Manager)? If not, search for **nvidia-glx** and install that; after it finishes installing, open a terminal (Applications-->Accessories-->Terminal) and enter

```
sudo nvidia-glx-config enable
```

If you already have the Nvidia drivers installed, then, still from the terminal, enter

```
gksudo gedit /etc/X11/xorg.conf
```

and scroll to **Section "Device"** to see if the **Driver** reads **"nvidia"**; also there's a couple of options you can add so that section of the file looks like this:

```
Section "Device"
        Identifier      "YOUR_CARD_HERE"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel" "true"
```

Note that you **must not** change the BusID if it's different on your file. Save it and close gedit, and reboot. See if video is more responsive now.

Thank you for your help, however now my system is totally fuxored.

In my xorg.conf file I made the changes you suggested after installing the NVIDIA drivers.  First error was that I renamed the Identifier, it errored on startup because it was looking for "Default Video Card" instead of "GeForce Go 6800"  No problem, went in and changed it in the other section from the command line... now I am totally screwed.  It is telling me that it can't find a NVIDIA card at PCI:1:0:0.... my card is at PCI:0:5:0.  I left that as 0:5:0 in the conf file, but it seems the drivers are looking for it elsewhere or something, but I have NO idea where I might be able to change that.

I tried changing the conf file back it what it originally was, same error.

Help...

---

### Post by Terl on 2007-04-17
> **Amorget said:**
> Nope, no love for me.  

Error: dependency is not satisfied: module-assistant.  I ran the updates command (I think... found that in another post) and it still doesn't work.

I had the same issue.  Easy to fix.  Make sure you did all your updates (the icon to top right tells you you need updates when you first log in after install)  After you do those, open synaptic and make sure you have all the repositories checked.  Then tell synaptic to reload and it will add some more packages.  Then run envy.

Envy is much easier than the other way (it isn't too bad either).

If it is "fluxored" as you say, hit ctl-alt-F1 and go to a terminal.  login at the prompt.  Then type:  sudo dpkg-reconfigure xserver-xorg.  It will walk you through the setup of x11 and get you back and running.  Then run Envy.

---

### Post by Amorget on 2007-04-17
> **Terl said:**
> I had the same issue.  Easy to fix.  Make sure you did all your updates (the icon to top right tells you you need updates when you first log in after install)  After you do those, open synaptic and make sure you have all the repositories checked.  Then tell synaptic to reload and it will add some more packages.  Then run envy.

Envy is much easier than the other way (it isn't too bad either).

If it is "fluxored" as you say, hit ctl-alt-F1 and go to a terminal.  login at the prompt.  Then type:  sudo dpkg-reconfigure xserver-xorg.  It will walk you through the setup of x11 and get you back and running.  Then run Envy.

Thank you, I will try that when I get home from work tonight.

---

### Post by Amorget on 2007-04-18
Yeah, that didn't fix it, so I reinstalled completely.  Not much lost.  I think the drivers that were suggested earlier caused a serious problem.

---

