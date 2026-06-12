---
title: "2 video cards / 2 monitors"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by metallicamaster3 on 2007-07-04
Hello!

I've been stumped with this for a while now.

I have:
AGP nVidia GeForce 2 MX 400
PCI nVidia GeForce 4 MX 4000

(for some reason, lspci thinks that the MX 400 is in PCI, and the MX 4000 is in the AGP....odd)

anyway, ive been looking at the TwinView etc HowTos, and they lost me. Pretty much right at the beginning with "lspci -X | grep VGA" and whatnot, because they didnt work in terminal. Plus, I have NO idea what im supposed to do with my xorg.conf . Hopefully someone here can make the necessary changes to the file for me, so that i know i didnt mess anything up.  

So, hopefully someone can help me, and I'll be more than happy to post any info about my computer. 

Thanks!

---

### Post by metallicamaster3 on 2007-07-04
anyone?

---

### Post by metallicamaster3 on 2007-07-04
please?? =\ anyone??

---

### Post by Hobo Joe on 2007-07-04
I have serious doubts that this is possible. Normally people just use one video card with two outputs....

But perhaps there is a way, keep looking!

---

### Post by psyopper on 2007-07-05
Not having done this I can't really say but...

If you look at /var/log/Xorg.0.log you will see something close to the top that looks similar to this:
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "PNY GForce 6200"

This is "building" your screen space(s) by tying your monitor(s) to your device(s)

In the xorg.conf you will see something like:
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection
Section "Device"
    Identifier     "PNY GForce 6200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier       "Default Screen"
    Device         "PNY GForce 6200"
    Monitor        "Generic Monitor"

```

Again, ignorance is speaking but I believe you should be able to pair up your screen/displays by doing something like:

```

Section "Device"
    Identifier     "Card 1"
EndSection
Section "Monitor"
    Identifier     "Monitor 1"
EndSection
Section "Screen"
   Identifier  "Screen 1"
   Device  "Card 1"
   Monitor  "Monitor 1"
EndSection

Secion "Device"
  Identifier "Card 2"
EndSection
Section "Monitor"
    Identifier     "Monitor 2"
EndSection
Section
  Identifier  "Screen 2"
  Device  "Card 2"
  Monitor "Monitor 2"
EndSection

```

Of course there is a lot more to it than that like including the display options for the monitors and the configuration settings for the cards. The above will definitely not work at all as is, it will need to be adjusted to meet your specific hardware. 

And of course, before making any changes ALWAYS make a backup of your xorg.conf. 

For what it's worth, -X is not a valid switch for lspci. I copied and pasted your code into a terminal and it failed:
```

brad@Ubuntu:~$ lspci -X | grep VGA
lspci: invalid option -- X
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

```

Everything in Linux is case sensitive. Actually not everything, but if you pretend that it all is case sensitive you won't get yourself into any trouble, so - Everything in Linux is case sensitive. As you can see, my mistake in case failed and I was given a list of valid switches (isn't that nice? Thank you Linus!)

When I tried your code with a lower case x I got the following, which is just what you would be looking for had you run it on your machine.
```

brad@Ubuntu:~$ lspci -x | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

Good luck and keep us posted on how this turns out.

---

### Post by metallicamaster3 on 2007-07-05
thank you. i am working on it now :)

---

### Post by xpod on 2007-07-05
I have an MX4000 on here along with some onboard savage card but i just use the svideo/tvout for a second display....the TV, to watch movies on.

Not sure if thats any good to you?
[https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)

I imagine it would be much the same for a second monitor:D

EDIT:....or
[http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitors)

---

### Post by metallicamaster3 on 2007-07-05
neither of the 3 worked. it just crashed X :(. i guess i wont be getting dual monitors, eh?

---

### Post by psyopper on 2007-07-06
[Tkae a look at this thread,]("https://answers.launchpad.net/ubuntu/+question/6439") on Launchpad for Ubuntu. The person is doing something very similar to you (just how I thought it should be done) but there are a few little things you likely missed. Primarily the Server Layout section:

```

Section "ServerLayout"
  Identifier "Default Layout"
  Screen "Default Screen"
  Screen "Screen 2" RightOf "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  Option "Xinerama" "on"
  Option "Clone" "on"
EndSection

```

Are you using [Xinerama]("http://en.wikipedia.org/wiki/Xinerama")? You probably will need to install it. The link to the Sourceforge page is at the bottom of this Wikipedia entry.

---

### Post by rscott5 on 2007-07-06
Correct me if I'm wrong, but I think in most BIOS you have to define which type of video adapter you wish to have enabled (VGA, PCI, PEG, onboard, etc.) and it isn't a multiple choice sort of question. The only time I have seen 2 video cards each running their own monitor is on the new Mac Pro machines, but those are running two of the exact same video cards both in PCI-Express and connected via nVidia's SLI technology, so I'm doubtful about getting it to work when you are running video through 2 different interfaces.

But hey who knows, this is Linux and every single day I seem to have my mind blown with the wild things you can do in it. Best of luck to you.

---

### Post by bodhi.zazen on 2007-07-06
Take a look here :

[HOWTO: Set-up Dual Monitors with 2 graphics cards](http://doc.gwos.org/index.php/DualMonitors)

---

### Post by metallicamaster3 on 2007-07-06
that seems to work somewhat....but i think the fact that Ubuntu saw each card in mirror form (thought that the AGP card was PCI, and the PCI card was AGP) messed it up, because X crashed again, only this time it worked after i logged in, then when i moveed the mouse, it crashed.

---

