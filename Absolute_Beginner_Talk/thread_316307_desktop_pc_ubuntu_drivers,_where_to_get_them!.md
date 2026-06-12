---
title: "desktop pc ubuntu drivers, where to get them!"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by pthickett on 2006-12-10
Hi,

Previously installed ubuntu on my laptop, just thought i had better bung it on my desktop pc aswell. However this install did not go quite so smoothly, as ubuntu didnt pick up some of my hardware. Most importantly my graphics and my wireless hardware.

Luckily Nvidia supply linux drivers as a .run format? is that correct? and how do i install it?

My wireless i am a little stuck on, i have a sitecom pci mimoxr WL-151 card, and sitecom do not supply linux drivers. What can i do? Otherwise i am stuck getting online without getting a more linux friendly card, does anyone know of a cheap and cheerful one?

Thanks

Pete Thickett

---

### Post by Usedpants on 2006-12-10
if you figure out how to run a .run file let me know!

---

### Post by halitech on 2006-12-10
open the terminal and type 

```

sudo ./filename.run

```

---

### Post by nickpaton on 2006-12-10
Hi Pete

Wireless-wise, please can you post the output when you put the following in a Terminal:

```
sudo lshw -C network
```

This identifies the hardware used for your network components.

We'll then take it from there.

For your Nvidia drivers, how about installing Automatix2 from:

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

and installing the driver from there.

More clever people will chip in with the command line solution, but I use ATI so not sure!

@ Usedpants:

To install a .run file:

First sort out permissions:

```
chmod +x <YOURPROGRAM>.run
```

And install the program:

Code:

```
sh ./*.run
```

---

### Post by nickpaton on 2006-12-10
> **pthickett said:**
> Luckily Nvidia supply linux drivers as a .run format? is that correct? and how do i install it?

looking into this further Pete, there are a number of threads, such as:

[http://www.ubuntuforums.org/showthread.php?t=314978]("http://www.ubuntuforums.org/showthread.php?t=314978")

[http://www.ubuntuforums.org/showthread.php?t=315749]("http://www.ubuntuforums.org/showthread.php?t=315749")

But other's are suggesting either installing via Synaptics or Automatix.

I've used Automatix loads, and found it to be 100% reliable, but it doesn't give you that sense of achievement of doing it all via the command line!!

---

### Post by pthickett on 2006-12-10
Well it sounds like the best idea is to wait until i get online and can run automatix to sort out the nvidia drivers.

I ran the sudo command in the terminal and got this result:

[B] *-network               
       description: Wireless interface
       product: Ralink RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 8
       bus info: pci@02:08.0
       logical name: wmaster0
       version: 00
       serial: 00:0c:f6:1b:03:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=rt61pci driverversion=CVS firmware=.bin link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:eb000000-eb007fff irq:201[/B]

So if that means anything then that would be great!

Thanks

Pete

---

### Post by igknighted on 2006-12-10
for the command line solution:

1) download the .run file to you desktop

2) make sure nothing is open then hit ctrl+alt+F1 to get to text only terminal.

3) type 'sudo /etc/init.d/gdm stop' to kill all graphical elements open.

4) type 'sudo chmod 775 NVIDIADriverName.run' (you can use tab to autocomplete once you type NV)

5) type ./NVIDIADriverName.run (again, tab can auto complete after you have a couple letters.  Note, this is case sensitive.

6) Follow through all its menus and just keep hitting OK to accept defaults.

7) When you are done, type 'sudo nano /etc/X11/xorg.conf'.  This will open a text editor in the terminal.  Use the arrows navigate down to the line 'Section "Device"'.

8) Just underneath this there will be a line that says 'driver "nv"'.  Change the "nv" to "nvidia".

9) hit ctrl-o to save, enter to confirm, and finally ctrl-x to quit.

10) type 'sudo init 6' to reboot, then when the system loads you chould get a splash just before the login screen that says NVIDIA, and then you know it worked.

NOTE:  If x fails to load and you get a text terminal on  reboot, use the 'sudo nano /etc/X11/xorg.conf' to change "nvidia" back to "nv" then save and restart again, something didn't work properly.

---

### Post by nickpaton on 2006-12-10
@Igknighted - many thanks for that M8 - I'm going to archive that for future reference.

Pete

Have a look at:

[http://www.ubuntuforums.org/showthread.php?t=264360]("http://www.ubuntuforums.org/showthread.php?t=264360")

Unfortunately you are going to have to connect to the Internet, so suggest using your other PC to do that and transfer any files across using a memory stick or whatever

Also search the forums under "ralink RT2600 wireless" - there are more posts there.

---

