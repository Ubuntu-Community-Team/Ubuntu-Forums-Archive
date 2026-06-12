---
title: "True Newbie (Server, CLI troubles)"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by winterion on 2007-09-18
I'll apologize in advance - my questions are going to be of a newbie level the likes of which are sure to frustrate. :(

I'm trying to set up an Apache web server, so I'm doing a little practice run with Ubuntu Server (606?) on a Microsoft Virtual Machine '07. I was able to mount the ISO and it installed all peachy-like.

Now, I'm at a scary, big, intimidating command-line interface. I know the absolute basics.. cat, ls, pwd, etc. But, I really, really would feel a thousand-fold more comfortable in a GUI. I'm aware that this distribution doesn't come with one, so I read a couple forum threads where people mentioned using sudo updates to go get them? That seems great.

Except, I have absolutely zero idea how to configure my internet connection from the command line. I've tried a couple efforts at vi and the like. I'm completely, totally, paralyzed.

Here's the static settings for Windows:
192.168.1.106
255.255.255.0
192.168.1.93 gate
198.6.1.2 dns1

How would I set up the connection to run through the VM? Manually assign everything to the same settings as Windows (and how is that done?) I've tried setting the virtual machine as both Shared Networking (NAT) and the network card itself, neither lets a ping resolve.

So, please start asking me questions.. things to post, etc.

Here's what I think people would be looking for:

netstat -nr
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 192.168.1.93 0.0.0.0 UG 0 0 0 eth0

/etc/resolv.conf
(I did not have this file, so I created it)
search test.com
nameserver 198.6.1.2

ifconfig -a
eth0
Link encap: Ethernet HWaddr 00:03:FF:8E:B9:41
inet addr:192.168.1.106 Bcast:192.168.1.255 Mask: 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3 errors:0 dropped:0 overruns:0 frame:0
TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:158 (158.0 b) TX bytes:3514 (3.4KiB)
Interrupt:11 Base address:0xec00

lo
Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:54 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueueulen: 0
RX bytes:4116 (4.0 KiB) TX bytes:4116 (4.0KiB)

/etc/hosts
127.0.0.1 localhost
127.0.0.1 ubuntu

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
FE00::0 ip6-localnet
FF:00:0 ip6-mcastprefix
FF02::1 ip6-allnodes
FF02::2 ip6-allrouters
FF02::3 ip6-allhosts

---

But, the way I see it, as long as I can get this 'net connection going, I can pull down and install a GUI, and then, I should be able to do the same for Apache.

Help?

---

### Post by kebes on 2007-09-18
> **winterion said:**
> I'll apologize in advance - my questions are going to be of a newbie level the likes of which are sure to frustrate. :(
No need to apologize! The only way to learn is to try!


> I'm trying to set up an Apache web server, so I'm doing a little practice run with Ubuntu Server (606?) on a Microsoft Virtual Machine '07. I was able to mount the ISO and it installed all peachy-like.

Now, I'm at a scary, big, intimidating command-line interface. I know the absolute basics.. cat, ls, pwd, etc. But, I really, really would feel a thousand-fold more comfortable in a GUI.

Since you installed the server version, there is no GUI. You could install the desktop version instead. It comes automatically with a GUI, which is much easier to learn. The desktop version can still be used as a server (you can still install apache, etc.). So the easiest option would be to download the Ubuntu desktop ISO and load that into your virtual machine.


> I'm aware that this distribution doesn't come with one, so I read a couple forum threads where people mentioned using sudo updates to go get them? That seems great.
If you want to add the default GUI to your server install, you just run this command:
```
sudo aptitude install ubuntu-desktop
```
You will be asked for your admin password to confirm the installation. The "sudo" means "do this as the admin user" the "aptitude" is the command for installing/uninstalling, and the final part says to install the package "ubuntu-desktop" which includes all the components needed for the GUI.

Of course, this will only work if you have a functioning net connection!


> Except, I have absolutely zero idea how to configure my internet connection from the command line. I've tried a couple efforts at vi and the like. I'm completely, totally, paralyzed.
Normally, the internet connection is automatically configured. However, when running inside a virtual machine, things can be different. If you launch your virtual machine with network connectivity and DHCP enabled, Linux should auto-detect everything.

From your ifconfig and netstat, it looks like the network is up and running properly. The first thing I would check is your virtual machine settings: make sure that it is not blocking network connections. (I've never used MS Virtual PC so I'm not sure what settings need to be enabled.)

---

### Post by JustAboutRealJAR on 2007-09-18
if you want to have a server with a GUI... instead of starting with a server version and installing a GUI... I would install Ubuntu Desktop Edition and install apache

That's just me, but it sounds like it would work out better for your purposes

---

### Post by kebes on 2007-09-18
Also, this guide discusses installing Ubuntu in MS Virtual PC 2004:
[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)

The section "Network Card" has some advice for troubleshooting network connectivity.

---

### Post by JustAboutRealJAR on 2007-09-18
rats! kebes beat me to it... and did a much better job at it too

---

### Post by rsambuca on 2007-09-18
> **JustAboutRealJAR said:**
> if you want to have a server with a GUI... instead of starting with a server version and installing a GUI... I would install Ubuntu Desktop Edition and install apache

That's just me, but it sounds like it would work out better for your purposes

Keep in mind that the server uses a different kernel from the desktop version, but as this is just in a virtual environment, it probably won't make a big difference in this case.

---

### Post by winterion on 2007-09-18
Thanks everyone for the really helpful posts.

I get the sense that my biggest mistake was downloading Server instead of Desktop, so I'm going to do that now and see where it gets me.

I'll post in a couple hours with a what's what and where's where of my exploits. Hopefully I won't break the interweb in the process! :confused:

---

### Post by winterion on 2007-09-18
Well, fresh problem for a fresh installation.

This time around, it starts to install (I get the orange bar) and then it gives me an error of some kind. The display is quite garbled so I can't read it out, but it looks like it has something to do with GNOME.

I hit CTRL-ALT-F1, and it gets me to a loading.. log in type command line.
Is this the command line for an installed OS or for the OS running off the CD? (I get the feeling it's the latter.)

I'm in /home/ubuntu

What now? Is there a command-line to see which I'm on? Some tips on what the screen (I think it might be a resolution issue) fix could be? Any way to manually set it at 800x600x16 and try the installer over again, if that's what need be done? Etc.

I guess the OS is so good because you have to EARN it. :popcorn:

---

### Post by winterion on 2007-09-18
Woah! Wait, a reboot and we're getting somewhere. Now it's visible.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, ..... etc. The message just went away, so I can't finish typing it, but hopefully that's enough.

Also, I can't seem to assert mouse control on the window.

---

### Post by winterion on 2007-09-18
Okay, now I can't seem to exert any control over the screen whatsoever.

Looks like this (excuse the low color, saved as GIF)
[http://winterion.derrickvanduzer.com/status.gif](http://winterion.derrickvanduzer.com/status.gif)

Hmm. Getting tons of "SQUASHFS errors" scrolling down when I CTRL-ALT-F1. Hard drive issue?
I'm gonna move the virtual disk files back onto my main drive and off the external.

---

### Post by winterion on 2007-09-18
Okay, well, a reboot later and now it's telling me to insert a boot disk, so I guess maybe I was working on the CD-ROM rather than the install the entire time, and I've never actually installed the operating system.

Sigh. This is incredibly difficult, and I've been spending the last eight hours on it. :(

I guess my question just got 100x newbier.

*How do you install Ubuntu?*

---

### Post by JustAboutRealJAR on 2007-09-18
when you boot from the cd...

there should be an icon on the desktop called install... which you double click

otherwise... it's in the 'Applications" menu (if not look in "system")

---

### Post by winterion on 2007-09-19
I'll give it another whirl this evening, but the present problem is that once I get Ubuntu to look all reasonable and happy in its GUI, I no longer seem to have any control of the system (mouse, keyboard, etc. all fail me, save for alt-enter to get out of full screen, or ctrl-alt-del to bring up Task Manager.

More on my exhausting efforts to use Ubuntu as they develop.

---

### Post by kebes on 2007-09-19
> **winterion said:**
> I'll give it another whirl this evening, but the present problem is that once I get Ubuntu to look all reasonable and happy in its GUI, I no longer seem to have any control of the system (mouse, keyboard, etc. all fail me, save for alt-enter to get out of full screen, or ctrl-alt-del to bring up Task Manager.

More on my exhausting efforts to use Ubuntu as they develop.

What is the exact version of the virtual machine software you are using? (Is it MS Virtual PC? What version?)

You might also consider using the "alternate" CD installer instead of the normal "desktop" installer. The alternate CD is a text-only installation processes, but you end up with a full GUI once the install is done. The alternate CD sometimes works better on "strange" hardware (and I guess a virtual environment qualifies as strange).

I know you already downloaded the server edition then the desktop edition, so you may not be keen on yet another download. But, it's worth a try if you're keen on getting it working!

(To get the alternate CD, check the box for it on the [download page]("http://www.ubuntu.com/getubuntu/download").)

---

### Post by JustAboutRealJAR on 2007-09-19
sounds like MS Virtual machine is designed not to let ubuntu run haha

---

### Post by winterion on 2007-09-24
My troubles continue, I'm afraid.

I'm now trying to install Ubuntu on an old eMachines PC instead of Microsoft Virtual Machine. It's not terrible.. 512 ram, 40gig hd, 2 gig processor, so I'm not sweating system requirements.

But, booting up in the graphical CD-loaded interface is causing the machine to crash more often than not. Any way I can perform the install from the command line, since I can CTRL-ALT-F1 to get there?

Weeks without this OS.. I couldn't feel more stupid. :confused:

---

### Post by kebes on 2007-09-24
> **winterion said:**
> But, booting up in the graphical CD-loaded interface is causing the machine to crash more often than not. Any way I can perform the install from the command line, since I can CTRL-ALT-F1 to get there?

You can use the "alternate" install CD, which uses a commandline installer. (The final installation will have the GUI). Hopefully whatever glitch is crashing the LiveCD won't affect the final install (perhaps once the proper graphics driver is loaded...).

Another thing to try: before booting into the LiveCD session, you can use the "check CD" and "memory check" options, to eliminate those possibilities. (You'd be surprised how often CDs burn with glitches... normally you don't notice but for a LiveCD these can ruin it in a hurry!)

> Weeks without this OS.. I couldn't feel more stupid. :confused:
Don't lose heart... It takes time to learn something new. We've all been in that stage of being totally confused and frustrated, so we know what it feels like. At least for me, it was "worth it" once I got over the initial learning curve.

---

### Post by winterion on 2007-09-25
I was able to get the installation going, and it seems to have finished on its own.

So, that's one step in the right direction.

Unfortunately, it's remarkably slow, fails to load anything on the desktop 3/4 of bootups, and often hangs. I think something might be wrong internally (HDD, RAM, etc.) so I'm going to memtest it and see what crops up.

I'm going to need a second bucket of this. :popcorn:
*gnaw*

---

### Post by JustAboutRealJAR on 2007-09-27
any luck?

---

### Post by winterion on 2007-10-03
Some. I got it installed, but I think the installation is corrupt because I get segmentation faults when trying to install programs.

MEMTEST86 came out clear.

I've actually got a second thread up, so let this one die. :)

---

