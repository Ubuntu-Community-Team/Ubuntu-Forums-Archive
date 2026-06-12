---
title: "How to maximize battery life ?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by younity on 2008-04-02
edit : this forum thread comes from Mint forums (I'm using Mint atm), but I guess that the tips you may provide me are the same in Ubuntu (I'm using a new & fresh installation!).
That being said :


Hello,

Topic says it all ! For the 'lil story, I'm new to linux, and I've been trying several distros before being seduced by Mint, its fastness, smoothness and friendly use ! I'm not going to whine about linux, but I really need a battery life as good as on Windows Vista. I take my laptop to university everyday ; basically I only use Word and type my classes for sometimes 4 hours straight. Under Vista, when I disable Wifi interface, Aero, Sidebar and dim brightness a bit, I can get up to 4 hours of battery life, just what I need. The thing is, now I really want to switch to Linux, but Mint only offers me 2.5 hours of autonomy, sometimes even less 
What are the tips to lenghten battery life ? Is there a way to systematically disable Wireless or WLAN scanning at system startup ? I heard about PowerTOP utility, tried it, but it's still far away from being competitive with Vista.

Again, this is not a Vista vs Linux thread ; I'm just looking for a solution to fit my needs.

Thanks!

---

### Post by Whiffle on 2008-04-02
Powertop doesn't do much to help by itself.  Its more of a tool to show you areas that could be improved.  

If I want to disable wireless, I generally just unload the module that runs my wireless card with modprobe -r  <nameofmodule>.  

Honestly though, a default ubuntu install is quite a bit behind in the power consumption department. 

Could you post a screenshot of powertop taken while your'e running on battery?  It'll give some idea where to start.

---

### Post by younity on 2008-04-02
Thanks for your quick answer.

Here some sshot I've just taken (wifi enabled).

[http://img522.imageshack.us/my.php?image=screenshotah6.png](http://img522.imageshack.us/my.php?image=screenshotah6.png)

edit :
after powertop tweaks

[http://img522.imageshack.us/my.php?image=screenshot1wt4.png](http://img522.imageshack.us/my.php?image=screenshot1wt4.png)

---

### Post by Vadi on 2008-04-02
8.04, out due in less than a month, promises better battery savings if you're on 64bit.

Btw, you did you do the suggestions powertop says, yeah? They only stay until you reboot too.. I haven't figured out how to get them to be permanent.

---

### Post by smartboyathome on 2008-04-02
You can try setting your processors to powersave. To do this, run this in a terminal:
sudo dpkg-reconfigure gnome-panel
And enable cpu frequency scaling. Then right click on your panel and click Add to Panel. Then add the cpu frequency scaling applet.

---

### Post by younity on 2008-04-02
hmm doesn't work, when I type that command and type enter, it looks valid but nothing shows up :/

---

### Post by Whiffle on 2008-04-02
Heres a couple pictures for reference:  I need to boot to windows and do the same thing sometime (i'm pretty sure its about the same on mine)
Wireless:
[http://www.resnet.trinity.edu/avaselaa/wireless.png](http://www.resnet.trinity.edu/avaselaa/wireless.png)

No wireless:
[http://www.resnet.trinity.edu/avaselaa/nowireless.png](http://www.resnet.trinity.edu/avaselaa/nowireless.png)

The short of it is that the hard drive and the wireless suck up the most power.  Getting things to stop writing to the hard drive can be kind of a pain ( I still don't have this nailed down yet).  

I don't really have time right now to flesh out this a bunch, but after Hardy comes out I'll probably write a howto based upon it.  Here's the most useful things I can think of at the moment:

This is meant for thinkpads, but its got alot of good information others can use too:
[http://de.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://de.thinkwiki.org/wiki/How_to_reduce_power_consumption)

A list of the worst program offenders as far as power consumption is concerned:
[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)

And actually, take some time to browse [www.lesswatts.org](www.lesswatts.org), theres alot of information to be had there.  

Finally, someone mentioned about having these power optimizations run.  Thats the easy part!  All you have to do is make a script that performs all of your optimizations, such as stopping services, removing modules, etc, and save it to 
/etc/acpi/battery.d

It will be run whenever the system goes into battery mode.  Additionally, things in 
/etc/acpi/ac.d
run whenever its plugged back in.

So for my system, I have a script that unloads modules, another that stops services, and another that runs all those misc optimizations that powertop gives.  I can give some more help on this later if needed.


Off the top of my head though, looking at that powertop output, I'd shut off your wired ethernet unless you're using it (ifconfig eth0 down) and remove its module (modprobe -r r8169).  Additionally, I'd remove the uhci_hcd module.

---

### Post by younity on 2008-04-02
Thank you for your very precise answer and extended links. However, I expected to find user friendly solutions ! I guess I should wait for the new Ubuntu :X

---

### Post by Whiffle on 2008-04-02
Yeah, there is no user friendliness I'm aware of in linux power management...yet...

---

### Post by younity on 2008-04-02
Maybe this will come later :(

---

### Post by annda on 2008-04-02
> **younity said:**
> I expected to find user friendly solutions ! I guess I should wait for the new Ubuntu :X

sorry to disappoint you, but this is not going to help very much.

i really love ubuntu and i use it all the time at home but when i take my laptop "for a walk" i just boot into a more battery-friendly distribution (wolvix when i need a full desktop environment or downstripped gentoo for the basics).

ubuntu really is "bloated" compared to other popular Linux flavors - it is very user friendly by catering to a wide range of hardware out of the box but the cost is a heavy kernel. in order to save power, it would have to exclude a lot of features and let users install all the modules - just like all windows users have to install drivers for every piece of hardware. but reading various forums tells me that this is exactly what most people hate about linux...

a little off-topic: my dream linux application would be a flexible and scalable optimization tool that would allow users to easily tailor their systems to current and planned needs - sort of super-menuconfig for the people. that way everybody could double their battery time and boot in 30 seconds, not just the ubergeeks.

---

### Post by younity on 2008-04-02
Well so far ubuntu has been (at least from my point of view) the most user friendly linux distro ever. Sure it may improve, and considering the complaints they heard about the battery life, they might improve that in the next releases ... let's just cross our fingers :P

If you can tweak anything via terminal, I guess someone will finally make an easy tool for newbies !

---

### Post by zgoda on 2008-04-26
> **Whiffle said:**
> Finally, someone mentioned about having these power optimizations run.  Thats the easy part!  All you have to do is make a script that performs all of your optimizations, such as stopping services, removing modules, etc, and save it to 
/etc/acpi/battery.d

It will be run whenever the system goes into battery mode.  Additionally, things in 
/etc/acpi/ac.d
run whenever its plugged back in.

So for my system, I have a script that unloads modules, another that stops services, and another that runs all those misc optimizations that powertop gives.  I can give some more help on this later if needed.

I got to similar idea (i.e. turn off NFS sharing and Postgresql server when on battery) but did not know it will be as easy. Thank you!

---

### Post by dirtblack on 2008-04-26
I like the way mint looks. it is possible to add it with a hardy sytstem. Would it work like kde and gnome share?

---

### Post by HiddenFly on 2008-05-22
I have made a little [script](http://unksi.kapsi.fi/powersave.sh) to save power. Basically, it does a few things that PowerTOP suggests and disables Bluetooth and CD drive polling.  It has a some options for them in the beginning of the file. I have tested it only with Kubuntu 8.04 Hardy Heron, so I don't know if it works with other versions/distro's. Any suggestions are welcome.

---

