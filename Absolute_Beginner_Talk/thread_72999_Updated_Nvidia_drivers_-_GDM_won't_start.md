---
title: "Updated Nvidia drivers - GDM won't start"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Heretushi on 2005-10-07
Quickies :
[LIST]
[*]Breezy - 5.10
[*]AMD64 3500+
[*]MSI NEO4 Platinum PCI-E
[*]MSI GeForce 6600GT **PCI-E**
[/LIST]

I just installed the Nvidia drivers using these two wonderful guides :
[LIST=1]
[*][http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)
[*][http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)
[/LIST]

Now, the drivers seem to be installed ok. I got in the logs of the installation and everything looks to be fine. Really, there are no errors in the installation log.

I did a backup of my xorg.conf file, it's ok.

When I try to start my GDM, it fails. When I check in the logs, it something along the lines of "there is no Nvidia card in this system". So I tried to replace the old xorg.conf (the backup) in place but it won't work neither! :o

So now, I'm stuck in console on my ubuntu PC.

Is there a way to get my screen back? I know it's not really a great post and not all that detailed... But I will be glad to give you the info you need! :)

---

### Post by Heretushi on 2005-10-07
So here is the message I have now :

(WW) NV: No matching Device section for instance (BusID PCI:5:0:0) found
(EE) No device detected.

Fatal server error :
no screens found

--- HOWEVER ---

I **DO** have "nvidia" written in my xorg.conf file! It seems it will not read the xorg.conf file correctly.

---

### Post by Heretushi on 2005-10-07
My god... Even if I REMOVE the xorg.conf file it still gives the same message! :o

It seems it doesn't even read the file anymore... :S

---

### Post by ow50 on 2005-10-07
Did you try installing the Nvidia drivers from the repositories?
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

It seems the instructions you linked advised you to remove at least some files ("sudo rm /etc/init.d/nvidia-glx"). So restoring  your xorg.conf file is not enough. Follow the instructions in the above link to get the non-latest nvidia drivers installed.

If you just want to get to X, you can use driver "nv" instead of "nvidia" in your xorg.conf file. That should always work.

---

### Post by Heretushi on 2005-10-07
Found this in the Xorg.0.log :

(--) PCI:*(5:0:0) nVidia Corporation unknown chipset (0x0140) rev 162, Mem @ 0xf4000000/26, 0xd0000000/27, 0xf8000000/24

So...My video card is unknown to the system!?

It was working FINE an hour ago! :(

---

### Post by Heretushi on 2005-10-07
That's the trouble! :o Even with "nv" it does not work. I'll try to get those drivers back from the guide.

---

### Post by Heretushi on 2005-10-07
I installed the drivers as the guide says.

Again, there is NO errors while doing so. But I can't get into GDM.

The error does not change. It always say my device is not supported... :S

---

### Post by Heretushi on 2005-10-08
I reinstalled from scratch. Everything works fine now.

---

