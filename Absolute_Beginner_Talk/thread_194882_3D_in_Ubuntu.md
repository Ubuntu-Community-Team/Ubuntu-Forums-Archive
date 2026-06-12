---
title: "3D in Ubuntu"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-06-12
Hi!

I'm running an ATI(sigh) 9600 pro Graphics Card. But I'm not going to ask for help with setting it up in Dapper because i've come to the conclusion that for now, that is impossible. There are about 30 threads on this forum alone about ATI.

What I would like to know is how does the Linux display system work? Just the basics. In windows(sorry, but that is where I come from) You have Windows, The Graphics card and in between them a driver that you could in/uninstall via a task manager. You could also disable a driver or force windows to use that specific driver. If all went to hell a MS soft driver would take over on reboot and give you some functionality. I fix and build windows machines for extra income(I'm a student) and know quite a lot about the system.

I REALLY enjoy the Ubuntu way of doing things but in Ubuntu I feel like a blind person. I would really like to be able just to help my self and then use what I’ve learned to help others. The problem is that in 99% of “how to’s” on display issues, I just get told copy and paste this and change this to that without anybody just briefly explaining what the command does. 

I had some great, detailed help with networking and since then have been able to help 5-6 other people set up there Lans. But it seems that installing Graphics Cards is some sacred knowledge that no one will share.
 
In Ubuntu:
1) Is Mesa the soft driver, the one i'm currently running with no 3D.
2) How do I uninstall any display driver
3) How do I install any display driver (even though it may not work)
4) What do I need to edit to piont Ubuntu to a specific driver?

I'm not looking for a detailed "how to"(if you do have the time go ahead!:)). 

I'm just looking for Install - This command- this is what it does.
This specific line points to that function in Xorg.conf

If  I’m asking something ridiculous, or if this has been answered some where else, please tell me so! 

All I know is that 95% of what I know about computers I’ve never read in a book, I learned it through experience and from experienced people.

Thanks in advance for any response! 	[-o<

(This thing turned out to be way longer than I planned!)

---

### Post by kuja on 2006-06-12
Well, basically, as far as I can see, it's set up something like this (granted, this is probably a bit oversimplified):

Client applications 
X Server
Video Drivers
Kernel

1) I'm not really sure what Mesa is, never had to worry about it :P I do believe it's an implementation of OpenGL (3D graphics stuff), though.
2) You shouldn't really need to, unless it's something you installed yourself, in which case, you should know what you added.
3) You shouldn't really need to do this UNLESS you're looking to install the proprietary drivers (often desirable). For an ATI card you would install the xserver-xorg-driver-ati package I believe. For an NVidia card you would add the nvidia-glx package. 
4) To do this, you can either edit X (the window manager)'s configuration file by hand, or use another program to edit it for you. The file for this is /etc/X11/xorg.conf. One convenient way to edit this is to run the following in a terminal ```
sudo dpkg-reconfigure xserver-xorg
```. That command just re-writes the xorg.conf file....

---

### Post by kriding on 2006-06-12
to install your ATI card, follow this howto in the wiki

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ATI%29]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ATI%29")

it worked a treat for me

---

### Post by superm1 on 2006-06-12
Hello,

Welcome to the ubuntu world.

Now so long as that 9600 is not R200 series (i'm not sure where the cutoff was), then 3D should be fairly straightforward.

I'm sure you have looked at this [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
right?

If not - thats your start.

I'll try to break down what its explaining here.

1) Add the restricted repository to your list.

This is because by default Ubuntu doesn't have anything that is nonfree/nonopensource.  To get around licensing problems but easily allow users to add nonfree stuff, they created an extra repository called "restricted".

2) Copy and paste these things
```
sudo apt-get update
```
After adding restricted to your list, this will update the list of available packages to include restricted.

```
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
```
Install all of the restricted kernel modules.  The restricted
module of concern here is called fglrx.
The way that linux does drivers is by removable "modules" that 
load into the kernel.  At any time, you can pull up a Terminal
and type "lsmod" to see all the loaded modules.  Fglrx is the
ATI propietary driver that loads into the kernel.

```
sudo apt-get install xorg-driver-fglrx
```
This installs all of the opengl & x11 related items for the driver
as well as any binaries that ATI distributes with the driver.

This package is seperate from the linux-restricted-modules package
because if a kernel update comes out, then you don't need to reinstall
all of the opengl,x11, and ati binaries.  Instead, the only thing
that would change is the kernel module which comes in linux-restricted-modules.

```
sudo depmod -a
```

This updates the list of available kernel modules to reflect
fglrx being added.  It can actually be done before installing
xorg-driver-fglrx.

```
sudo aticonfig --initial
```
This reads in your initial /etc/X11/xorg.conf.  It then parses
it and updates it to change anything required for fglrx.
aticonfig actually has lots of other options that you can set
up as well including but not limited to multiple displays and power
management.  If your curious run **aticonfig --help** to see.

```
sudo aticonfig --overlay-type=Xv
```
This enables the video overlay to be handled by Xv.
Video overlays can be handled either by Xv, X11, or opengl.
X11 is the straight X11 windowing protocol.  If you use this,
most higher resolution videos will play pretty horribly.
Xv stands for XVideo.  It is the defacto standard for video
playback, so if your driver supports it, you should use it.
Opengl plays back your video in an opengl texture.  This can
be good in some cases, but you would have to experiment with it a bit.


Does that help?

---

### Post by Patrick-Ruff on 2006-06-12
also, on another note, I've had a tun of problems with Gnome graphically, so if you see a delay in opening menus' thats normal. well, not so normal, its a huge annoyance for me. I'm switching to Kubuntu. faster desktop environment, well, good luck then. I suggest installing UT2k4 as your '3d test', ```
glxgears -printfps
``` is not the best way to get your actual 3d acelleration, good luck.

---

### Post by RudolfMDLT on 2006-06-12
Thank you everyone! 

As for the
[https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29](https://wiki.ubuntu.com/BinaryDriver...29%7C%28ATI%29)
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

guides they are actually just a copy of each other. And sadly I have already tried them.

superm1 and kuja thank you for detail and your time, it sort of helps the blind see!

BUT sadly no 3D as of yet! Still running Mesa - which most guides say is a bad thing.

> rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

and in glsgears(very handy that! Thnx!)

> rudolf@rudolf:~$ glxgears -printfps
1378 frames in 5.1 seconds = 271.001 FPS
1358 frames in 5.4 seconds = 250.545 FPS
1368 frames in 5.1 seconds = 267.328 FPS
1368 frames in 5.0 seconds = 272.123 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
rudolf@rudolf:~$

So the quest goes on...](*,)

But thank you for trying and helping! :-)

Any other ideas would be appreciated!

---

### Post by JanVH on 2006-06-12
Did you edit the /etc/X11/xorg.conf line Identifier to:

```
Identifier "aticonfig-Screen[0]"
```

?

Does lsmod lists that you fglrx-driver is running?

Try to replace "ati" by "fglrx" in each "Driver"-occurence in each "Device"-section of /etc/X11/xorg.conf... Then restart X (or reboot).

---

### Post by RudolfMDLT on 2006-06-12
From bad to worse! I have just installed these drivers:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
Official ATI linux drivers. I installed them, did the aticonfig --initial and rebooted my PC. When loging in my account starts to load, icons appear, gaim starts connecting to ICQ and wham, black screen, I see the TTY1 screen for 1 second and I'm back at the login screen! I'm currently logged in as root, weird that root works but not my account?

Please can some one help me revert to my old system? No, i did not back up Xorg or any other folder so I probally deserve this but that aside, please help!

PS: Identifier "aticonfig-Screen[0]"-JanVH- i did do that yes. Thnx anyway!

---

### Post by RudolfMDLT on 2006-06-12
Okay, I unstalled the ATI drivers and now I have my system back again. Sorry for the useless post but I couldn't manage to uninstall the drivers earlier. don't know why.

---

### Post by jetpeach on 2006-06-12
I believe I have the exact same problem as you - followed those guide exactly and fglrxinfo yields
```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect

``` etc...
Will keep searching around hopefully for a solution...

---

### Post by superm1 on 2006-06-12
For those having trouble in this thread....

Using the Ubuntu repository route,
First off, do a```
 lsmod
```.
Determine whether fglrx is actually loaded.  If it isn't loaded, then try
```
modprobe fglrx
```
If that doesn't work, try 
```
depmod -a
```
again.
If it is loaded, attach a /var/log/Xorg.0.log to a post here.  Also

---

### Post by RudolfMDLT on 2006-06-13
superm1

Thank you, I removed all FGLRX drivers, restarted, Xorg would not load, no surprise. In TTY1 followed your instructions to the letter and it worked!... in EVRY account BUT mine. I started a new thread as this one is one concerning ATI

[http://www.ubuntuforums.org/showthread.php?p=1132279#post1132279](http://www.ubuntuforums.org/showthread.php?p=1132279#post1132279)

Please check it out and see if you don't no the answer.

To anybody else looking for help with ATI cards. Print superm1's instructions(or write them down), restart into recovery mode to keep Xorg from loading then try his instructions. I don't know why, but his way is the only way that has worked for me!

Thanks for your help but please help me over the last obstacle! 

Thank You!

---

### Post by RudolfMDLT on 2006-06-13
I'm gonna go mad! The ati drivers just disappeared. I'm back using Mesa! I can log back into my account. I did not touch any drivers. I just added another users through root. While in root, i was using the FGLRX drivers and getting an fps of 1900 with glxgears. Upon creating a new account, the driers disappeared and reinstalling them doesn't help in Gnome, I'll try again in recovery mode.

I have attached my Xorg log file which you requested, it's too big to be uploaded as a text file so i renamed it to *.zip. Just save it and rename it to *.txt. The forum will only allow 19.4 kb for txt files but 950kb for zip files.

Thank you for your time and patience superm1!

---

### Post by RudolfMDLT on 2006-06-13
[QUOTE=RudolfMDLT]I'm gonna go mad! [/QUOTE]

OKAY! resarting and installing them while Xorg is not loaded works. My account works. 

> rudolf@rudolf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

superm1, thank you very much! This drove me up and over the wall but it's working now, sofar....

Thank you!

---

### Post by RudolfMDLT on 2006-06-13
superm1,

I think the reason that some people can't get there cards to work is because they need to be in an environment where the Xserver is not running. It made the differences on my system. I have posted your advice on a new thread to make it clearly available to other ATI users. If you do a search on ATI you'll find there are allot of unlucky buggers who still need help.

[http://www.ubuntuforums.org/showthread.php?p=1133444#post1133444](http://www.ubuntuforums.org/showthread.php?p=1133444#post1133444)

Thank you again!

---

