---
title: "minimizes funny"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-04-19
hello, i am new to ubuntu. i just installed it dual booting yesterday. so far, i am very pleased. i have a question though about how windows minimizes. i am not sure if this is normal but when i minimize a window, it is definately not smooth. first all these black rectangular lines outlining the window appear n they successively get smaller when they are minimized. is there any way to turn that off or change it to a regular minimizing like in windows xp? also another unrelated question -- why is it that Amarok makes everything else so slow. here are my specs: i am using ubuntu 6.10 edgy -- with 768 MB ram, 2.4 GHZ pentium 4, dual boot with windows xp. thanks for any replies. and i hope to have a nice experience here. =]

edit:

i am also wondering how you restart the computer whenever all you are left with is a blinking underscore. i hate having to do a hardreset. can i just press CTRL+ALT+DEL ?

---

### Post by tgm4883 on 2007-04-19
Sounds like a graphics driver issue

What are the outputs of this two commands

```
lspci
glxinfo | grep direct
```

---

### Post by Miroku on 2007-04-19
for the first command:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

and for the second one:
```

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

---

### Post by tgm4883 on 2007-04-19
install the nvidia graphics drivers

From ubuntuguide.com
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
```

Then restart X

---

### Post by Miroku on 2007-04-19
so after i did the restart, and i tried getting back into ubuntu, i was greeted with a blue screen talking about unable to load something "X", i checked out the more detailed problem description and it said stuff about missing font files and missing info from /usr. i then restarted the computer n put the ubuntu disk in there, thinking that might do something, but it was the same error. right now i am writing from my windows partition because i cannot get passed that blue screen. please guide if u can or if u can tell me how to get back to my old settings. thank you. lol, and everything was going so well.

---

### Post by Zuuswa on 2007-04-19
to reconfigure the xserver, try using the command

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Miroku on 2007-04-19
where do i type that command exactly? using the recovery mode of ubuntu?

---

### Post by Zuuswa on 2007-04-19
no, you dont have to go into recovery mode.  When x server fails to load, it should give you a CLI command prompt that asks you to log in.  Just log in normally.  If you do want to use the recovery mode, you do not have to put 'sudo' in front of the command, as you will be running as root.

---

### Post by Miroku on 2007-04-19
ok -- will try it soon and then report back here. i have to get some school work for lab done but then i will be back into this thing, hopefully u guys dont go too far,  i need ur uber knowledge. =) thx

---

### Post by Miroku on 2007-04-21
so after using the reconfig command and a little bit of trial and error -- im back in ubuntu goodness. unfortunately, even after all that -- the problem that i originally described is still here (the one with the minimizing with rectangular boxes) 

also, in case it is useful info to post this. the first time i went thru the reconfig using
```

sudo dpkg-reconfigure xserver-xorg
```

there was a fatal error which had to do with the framebuffer -- so i turned it off and then it started working again. please reply if anyone can help me with this minimizing annoyance. thanks.

---

### Post by st33med on 2007-04-21
Are you using Beryl?

I have seen a similar problem.

---

### Post by Miroku on 2007-04-21
i dont know what beryl is exactly but i am using ubuntu 6.10 edgyeft -- and if you have seen the same problem, was there a solution?

---

### Post by Swab on 2007-04-21
Try this, Alt+F2 to open the Run Application dialogue, then enter "gconf-editor" and click run

Then..

apps>metacity>general and check the box for reduced-resources

close gconf-editor

This fixes those daft black lines.. but creates an annoying wire frame effect when moving windows... to fix this issue click on system > preferences > accessibly >  assistive technology preferences .. and then check enable assistive technologies

Should be all good now.

---

### Post by pjones0404 on 2007-04-21
also make sure that u have installed the correct video card driver for ur machine. i find the envy script the easiest way to do this. u can either run "sudo apt-get install envy" or visit the link below and look for the ubuntu 6.10 package and install in that way. either way i would review the following website to see how it works. 

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Miroku on 2007-04-21
YOU ARE MY HERO SWAB! -- so the rectangles and everything are gone and now it minimizes like its normally supposed to. do you know why those lines use to be there? and pjones, i will look into envy because it looks like an awesome util and it may help me get more out of my video card.

well thats one problem solved and here is another completely unrelated one:

why is it that Amarok makes everything else so slow? here are my specs: i am using ubuntu 6.10 edgy -- with 768 MB ram, 2.4 GHZ pentium 4, dual boot with windows xp.

thanks everybody

---

### Post by Swab on 2007-04-21
> **Miroku said:**
> YOU ARE MY HERO SWAB! -- so the rectangles and everything are gone and now it minimizes like its normally supposed to. do you know why those lines use to be there? and pjones, i will look into envy because it looks like an awesome util and it may help me get more out of my video card.

well thats one problem solved and here is another completely unrelated one:

why is it that Amarok makes everything else so slow? here are my specs: i am using ubuntu 6.10 edgy -- with 768 MB ram, 2.4 GHZ pentium 4, dual boot with windows xp.

thanks everybody

The lines are normal... apparently someone thinks that looks good!

Amarok is KDE app which is probably why it's not running too well.  I believe there is a gnome equivalent called Banshee.. but personally I just use Rhythmbox

---

### Post by Miroku on 2007-04-22
heh .. i guess ppl got some very strange tastes in what looks good to them. to them, theirs eh?

anyway, since its a kde program, would that mean something like kubuntu would run it better? -- i stick to rhythm box to but it lacks global hotkeys -- which would be awesome to have

---

### Post by silverglade00 on 2007-04-25
Since it is a KDE program, your system has to load the basic kde libraries in order to run it. That is why you are experiencing a slowdown. Your system is using more resources. Yes, kubuntu would run it better, but you don't have to resort to that. You could always just install KDE and log into a KDE session when you want to run Amarok. Of course, that gets really annoying. Probably the best way to fix this is to install more RAM. :) That will give you better performance overall and the resources used by the kdelibs will have a smaller effect.

---

### Post by Lord Illidan on 2007-04-25
With 768 MB of RAM you shouldn't be experiencing much of a slowdown. I only have 512 MB myself and I use Amarok and a slew of other apps quite well on Gnome.

I am guessing the problem is more due to cpu usage.

Install htop from the repositories - sudo apt-get install htop

It is a commandline based app which will allow you to monitor the performance of your system. Alternatively use system monitor (System -> Admin -> System Monitor). Then you can check whether the problem is memory consumption or cpu usage.

---

### Post by Miroku on 2007-04-26
> **Lord Illidan said:**
> With 768 MB of RAM you shouldn't be experiencing much of a slowdown. I only have 512 MB myself and I use Amarok and a slew of other apps quite well on Gnome.

I am guessing the problem is more due to cpu usage.

Install htop from the repositories - sudo apt-get install htop

It is a commandline based app which will allow you to monitor the performance of your system. Alternatively use system monitor (System -> Admin -> System Monitor). Then you can check whether the problem is memory consumption or cpu usage.

yes, i just checked, its due to CPU usage

---

### Post by Miroku on 2007-04-26
so i am planning to use that envy program some1 suggested, hopefully it doesnt blow up the xserver whenever i tried to get the right drivers the first time.

so i tried gettin envy thru the terminal window but i got this error:

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy 
```

i went to the website and downloaded the proper .deb.


im greatful for the help in gettin rid of the lines, but i want to get the full potential out of my hardware if possible -- yes i am greedy like that =]

btw, i have a nvidia fx5200 that came with my dell. if anyone has a simpler way of installin the correct drivers, please let me know before i destroy my computer once again. thanks.

---

### Post by Miroku on 2007-04-26
alrite, so i ran the envy program and told it to install the nvidia drivers. unfortunately, the xserver crashed again, just like it did the first time i tried to do something with the drivers.

i was able to reconfig and i logged back in, but now its tellin me there is a broken depedency. 

synaptic tells me it has to do with 'nvidia-glx-dev'

also after
```
glxinfo | grep direct 
```

i get this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```



what should i do with it now? complete removal or something else? and one other question that i should have asked a long time ago, how do i know that i have the correct version video drivers currently? -- i remember in windows, if it wasnt the correct version, it would show incompatibility. 

any help would be much appreciated.

---

