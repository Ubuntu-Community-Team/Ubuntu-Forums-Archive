---
title: "Short battery use with MacBook"
date: 2007-05-03
forum: Apple Intel Users
---

### Post by Seamyst on 2007-05-03
I'm using a MacBook Core Duo 2.0, dual-partitioned with 10.4.9 and Feisty.  I have one kinda-big problem I haven't been able to solve, yet... the battery life in Feisty is MUCH shorter than in Tiger, by almost half.  I can watch nearly all of the Return of the King Extended Edition (four hours) on battery in Tiger, but I can only get about two to two and a half hours on battery in Feisty, even with running just Gaim and Firefox.

All the updates (including firmware) have been applied in Tiger; I admit I'm still working on updates in Feisty (had to start it all from scratch after my hard drive crashed), but that's because the campus network is incredibly slow.  If one of the updates addresses this, please let me know and I'll just be patient until it's in the batch that I install next.  If it's not in one of the updates, does anyone have a solution?  It's not a big problem now, since classes are over for the year, but I'd really like to be able to take my laptop to classes in the fall without having to worry about charging it between classes.

---

### Post by ronocdh on 2007-05-03
This is a huge problem for me as well; power management in Feisty, well, it just plain sucks. I personally have taken to just using OS X through classes to take notes, unless I have access to an AC outlet, which means getting a nice seat (which would mean getting to class on time =P).

I think it's more of a waiting game than anything right now. =(

---

### Post by Azathoth_ on 2007-05-05
We must report this bug to launchpad, because is a huge issue on ACPI panel on Ubuntu

---

### Post by mustang on 2007-05-05
> **Azathoth_ said:**
> We must report this bug to launchpad, because is a huge issue on ACPI panel on Ubuntu

I'm not sure the ubuntu dev's are capable of debugging this problem. It seems to be a larger power management issue that is even present in Windows (see [here.]("http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00440.html"))

From [ this]("http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00428.html") thread, it seems the most we can do is unload unnecessary modules like bluetooth or isight video.

---

### Post by ronocdh on 2007-05-05
> **mustang said:**
> I'm not sure the ubuntu dev's are capable of debugging this problem. It seems to be a larger power management issue that is even present in Windows (see [here.]("http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00440.html"))

From [ this]("http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00428.html") thread, it seems the most we can do is unload unnecessary modules like bluetooth or isight video.
Hm very interesting, there are certainly a ton of things I could shut down, then. But as far as the feasibility of a fix, I think it's possible. No, Apple isn't going to provide the devs with the specs they need, but I do think the Ubuntu devs actually give a damn about usability, whereas MS... not so much. Certainly not when it comes to Apple computers. ;)

We may be a niche within a niche here at Ubuntu, but whatever support we get form the devs will STILL be better than anything we'd get from MS!

---

### Post by Ken T on 2007-06-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/112610](https://bugs.launchpad.net/ubuntu/+bug/112610) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Someone has already posted a bug, to which I've added a link to this thread. Dunno what the developers can do, but any improvement will be a welcome one. I estimate that I get a half of the battery life running Ubuntu thru Parallels or VMware as I do when just running OSX.

K.

---

### Post by ronocdh on 2007-06-23
> **Ken T said:**
>  I estimate that I get a half of the battery life running Ubuntu thru Parallels or VMware as I do when just running OSX.

K.
Maybe so, but have you tried PowerTOP? [Benanzo says]("http://ubuntuforums.org/showpost.php?p=2857518&postcount=10") a battery life of up to 2.5 hours is possible.

---

### Post by pveith on 2007-06-23
> **Ken T said:**
> Someone has already posted a bug, to which I've added a link to this thread. Dunno what the developers can do, but any improvement will be a welcome one. I estimate that I get a half of the battery life running Ubuntu thru Parallels or VMware as I do when just running OSX.

K.
Uhm do i get this right? You want Ubuntu Devs to improve battery life using Ubuntu in a VM in OSX? I don't see a real reason to put ubuntu devs effort in powermanagement using a VM (the underlying system is controlling CPU and powerconsumption and should do so with its programs, even if these are VMs. And VM-Softwaredevelopers should implement powersaving features for their software). I rather would have ubuntu-devs improve battery life in running feisty directly without running a virtualizer. And by the way a VM is a very CPU-intensive program, which in turn drastically reduces battery-life of its host OS...

I use Feisty via bootcamp and get about 3,5h-4,5h battery life, which is less as in OSX, but IMHO acceptable. i might have a look at undervolting, but at this point i just don't have the time...

---

### Post by kzm. on 2007-06-23
you get 3.5h through using powertop and switiching of certain things.. or is ther more you did?
what do you mean by "undervolting"? do you have a reource on that?
and does all your battery tweaks also improved the heat? my laptop gets pretty hot.. though the cpus are quite ok at 50-60 C.

---

### Post by ivesjd on 2007-06-23
Id be interested in what all you do to get 3.5 to 4.5 hours as well. The most ive seen on mine was about 3 with wireless turned off. Which means that (a very rough estimate) that wireless drops your battery like by about .5 to 1 hr!

---

### Post by pveith on 2007-06-23
Only thing i did was dimming the LCD to the lowest possible status and unloading the wireless driver (which alone reduced powerconsumption by about 2W of the 16W used normally). And i actually did next to nothing during the test.

On undervoltinh have a look at linux phc look into this thread: [http://ubuntuforums.org/showthread.php?t=364321&highlight=feisty+undervolting](http://ubuntuforums.org/showthread.php?t=364321&highlight=feisty+undervolting)

---

### Post by ivesjd on 2007-06-23
I was thinking that you had unloaded the WIFI driver. But as my apartment only has wireless, that is of little use to me. But its nice to know. I did notice when I had my wifi turned off that I had much better battery life. Maybe that is one of the next steps that needs to be taken. Work on power consumption with wifi drivers.

---

### Post by pveith on 2007-06-23
@ivesjd: Are you using the lowlatency kernel? If i recall it correctly Ubuntu-Studio relies on it. Unfortunately it is rumored that it uses more power as the generic. Additionaly i use 64Bit Ubuntu, don't know if this matters for power consumption....

---

### Post by ivesjd on 2007-06-23
I am not using the Low-Latency kernel. I am using 2.6.20.16 generic. I did a regular fiesty install and then did the ubuntu studio look, sounds and everything. I tried using the low-latency kernel, but my wireless didnt work out of the box and I figured it was just easier to not deal with it.

---

### Post by kzm. on 2007-06-24
i saw a lot of threads on this forum that were meant to just carry together everybodys working solution for one particular problem. they are more intense than normal ones and start quite often with one advanced person throwing up some how-to.
am i the only one, who would love to have one very good thread about tricks and how-tos about reducing power consumptions and heat (as i think its related) and may be add it to the quintessence to the inoffical macbook how to at the forums help section?
i would to make a start, but my laptop burns my pants and i can work 2h max on battery... :-\"

---

### Post by kzm. on 2007-06-24
pveith the link about the low volting sounds promising and interesting! does anybody tried these instructions with a c2d or can tell me about using them with 64bit install would differ? its from the closed feisty development forum? does this mean its implemented by now or too old informations? they talk about nearly the same kernel i have (its -14 and i have -16)... i am not right away rushing into this, as i am happy having a stable build now. but i would jump into it right away if people would confirm its working. anybody?

---

### Post by Ulf Karlsson on 2007-06-26
I have my MacBook down at 13.1-13-2 W now according to PowerTop at lowest backlight level and at fan speed 1200.

You need the kernel from gutsy to use powertop. Add to /etc/apt/sources.list:

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

and then install

$ sudo apt-get install linux-headers-2.6.22-6 linux-headers-2.6.22-6-generic linux-image-2.6.22-6-generic linux-restricted-modules-2.6.22-6-generic linux-ubuntu-modules-2.6.22-6-generic


What I did was to add this in /etc/modprobe.d/blacklist-power

blacklist uvcvideo # isight
blacklist hci_usb # bluetooth
blacklist ndiswrapper # wlan

Then I follow the instructions at [http://www.linuxpowertop.org/known.php](http://www.linuxpowertop.org/known.php)

So I added Option "NoDRI" to xorg.conf as prescribed in the i915@pci section (I don't use 3D anyway)

There is some problem with powernowd as well, but there is a simple workaround. In /etc/rc.local, put (before exit 0):

cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

Also I applied the patch for the appletouch. To do that you will need the kernel source. I use 2.6.22-6 from gutsy, so:

$ sudo apt-get source linux-source-2.6.22
$ cd linux-source-2.6.22-2.6.22/drivers/input/mouse
$ patch < /path/to/thepatch (and type in appletouch.c when it asks for file)
$ make -C /lib/modules/2.6.22-6-generic/build SUBDIRS=$(pwd) modules
$ sudo cp appletouch.ko /lib/modules/2.6.22-6-generic/kernel/drivers/input/mouse/appletouch.ko
$ sudo rmmod appletouch
$ sudo modprobe appletouch

The above assumes that you have the kernel headers installed already etc.

You should also note that syndaemon is bad since it generates some wakeups.

I also removed the volume applet.

My battery time should be almost 4h now if things are linear.

I think that was all :)

---

### Post by Ulf Karlsson on 2007-06-26
The MacBook page on the wiki seems hopelessly outdated by the way. I found some useful stuff there but most of it seems to be irrelevant. I consider rewriting it. Does anyone feel like helping me out? I have written down some notes already.. :)

---

### Post by kzm. on 2007-06-27
i dont think i am of a great help (noob as i am) but i noticed too, that some on that site is not working for me neither so i made my own notes. i could give you those, if that would be of any help to you..

---

### Post by kzm. on 2007-06-27
another question ulf. how is your heat? do you feel a difference? and if i follow your steps does this mean compiling my own kernel becomes a little bit obsolete (if i dont really wonna tweak everything)? i wanted to compile my own kernel for dynamic ticks and the powertop...

---

### Post by jackiecanev2 on 2007-06-27
I have the same exact problem. In feisty, my battery life drops to just over an 1 1/2 hours. Sheesh. Even on my old Dell, it dropped from 2 hours to less than one...

---

### Post by Ulf Karlsson on 2007-06-27
If you use the gutsy kernel you will not need to recompile.

To use gutsy packages add the following two lines to /etc/apt/sources.list:

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

Then, to prevent apt-get from installing gutsy packages by default, put the following in /etc/apt/preferences (this is called pinning, read about it in the manual page apt_preferences(5)):

Package: *
Pin: release o=Ubuntu,a=feisty
Pin-Priority: 900

Package: *
Pin: release o=Ubuntu,a=gutsy
Pin-Priority: 400

Now you can use the command

$ sudo apt-get -t gutsy install linux-headers-2.6.22-6 linux-headers-2.6.22-6-generic linux-image-2.6.22-6-generic linux-restricted-modules-2.6.22-6-generic linux-ubuntu-modules-2.6.22-6-generic

to install the new gutsy kernel with support for PowerTop and dynamic ticks. For the appletouch fix you will still need to recompile appletouch.ko, but you do not have to recompile the entire kernel. If you follow my instructions above, you will only recompile the necessary module, to replace the old one from the kernel package.

I think my heat is still worse than in OS X, especially with wlan. I usually have the fan running at 3000 rpm.

---

### Post by kzm. on 2007-06-27
@ulf: sweeeeeeeeeet.. gonna try it out! (my touchpad is working fine)

---

### Post by thully on 2007-06-27
What does the appletouch patch do?  Does it make the trackpad more responsive?

---

### Post by Ulf Karlsson on 2007-06-27
As stated at [http://www.linuxpowertop.org/known.php](http://www.linuxpowertop.org/known.php)

"Matthew Garrett has provided a patch to the apple macbook touchpad driver to stop it from doing hundreds of wakeups per second."

If you do not think the trackpad is responsive enough that has to do with the configuration. You can tweak it in xorg.conf. My section for the appletouch follows below and my touchpad is very responsive:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
       Option  "Protocol"    "event"
       Option  "LeftEdge"      "0"
       Option  "RightEdge"     "1100"
       Option  "TopEdge"       "0"
       Option  "BottomEdge"    "310"
       Option  "FingerLow"     "1"
       Option  "FingerHigh"    "1"
       Option  "MaxTapTime"    "180"
       Option  "MaxTapMove"    "220"
       Option  "MaxDoubleTapTime"      "180"
       Option  "HorizEdgeScroll" "1"
       Option  "VertEdgeScroll" "1"
       Option  "TapButton1"            "1"
       Option  "TapButton2"            "3"
       Option  "TapButton3"            "0"
       Option  "LockedDrags"           "off"
       Option  "VertScrollDelta"       "10"
       Option  "HorizScrollDelta"      "10"
       Option  "VertTwoFingerScroll"  "0"
       Option  "HorizTwoFingerScroll" "0"
       Option  "MinSpeed"      "0.79"
       Option  "MaxSpeed"      "1.25"
       Option  "AccelFactor"   "0.24"
        Option          "SHMConfig"             "true"
EndSection

It is the FingerLow and FingerHigh section that determine whether the driver will consider a tap or movement as input or not depending on the pressure.. I set to 1 which is at the lower end. You can read about the other options in the synaptics manual page.

---

### Post by luisbg on 2007-06-29
The new kernel 2.6.22 has a lot of powermanagement improvements. 2.6.22-7 is in the gutsy repos.

An other thing that helps and is trivial is going to System > Administration > Services, and deactivate unused services like for example bluetooth.

Set the cpu_scaling_governor to powersaver mode, that helps not only battery use but cpu temperature.

To get the maximum... add powertop for all that, but that isn't as trivial.

---

### Post by kzm. on 2007-06-30
> cpu_scaling_governor

sorry for this question, but where do i set this?

---

### Post by cyberdork33 on 2007-06-30
> **Ulf Karlsson said:**
> "Matthew Garrett has provided a patch to the apple macbook touchpad driver to stop it from doing hundreds of wakeups per second."

I think this is now included in the 2.6.22 mactel patches.

---

### Post by benanzo on 2007-07-01
I have been running a vanilla 2.6.21.1 kernel with the mactel 2.6.21 patches for about two weeks and after applying every suggestion from PowerTOP (including turning off Beagle (duh) and disabling bluetooth) I average 2h20m-2h40m on a single charge (my battery reports 89% max capacity.)  That is with my LCD at about 70% brightness and wireless on full time.  The main killers on my battery life right now are the appletouch module and the USB subsystem.

The good news is that the kernel team and the ACPI folks are really taking power management issues head on.  I follow the ACPI mailing list and they're getting several patches a day based on PowerTOP's findings.  The mactel list is pretty heated on the subject too.  We should be seeing some real improvements in Gutsy.

---

### Post by ntetreau on 2007-07-19
You can also make sure that laptop-mode is turned on by default when you unplug on even boot up unplugged, it is also possible to put your intel wifi card on powersaving mode.  Follow the first post of my howto for thi:

[http://ubuntuforums.org/showthread.php?t=419772](http://ubuntuforums.org/showthread.php?t=419772)

Nic

---

### Post by cyberdork33 on 2007-07-19
> **thanos12 said:**
> this problem with the battery needs a solution!!
[IMG]http://s4.bitefight.gr/c.php?uid=15792[/IMG]

Plug it in!?

---

