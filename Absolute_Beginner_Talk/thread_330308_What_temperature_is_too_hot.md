---
title: "What temperature is too hot?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-01-02
Hello, I have Conky 1.4.5 installed with lm-sensors and I'd like to know what temperatures are safe for my computer.

I have a hp pavilion dv4230us notebook.

Most of the time my temp is from 52c to 73c. I have seen it up to 88c. What are average temps?

---

### Post by Patrick K on 2007-01-03
I depends on the processor you have. I looked into this a couple years ago and they can vary widely on how hot is too hot. On Tom's Hardware site there was a video of an AMD going  up in smoke is less than 2 seconds without a heatsink. IIRC, a Pentium survived for almost a minute. Different Pentiums have different tolerances. Even the stepping makes a difference. A quick search on "cpu temperatures" should provide a lot of info. 88c seems very high but maybe not for a laptop which are much more air flow restricted. My desktop P4 varies from about 44c to 58c. In the BIOS I have the shut down temp set at 80c. Many cpus will throttle back when they get too hot.

---

### Post by crimesaucer on 2007-01-03
Thanks, every time I googled the subject, I always get a lot of Windows related material and never an actual temperature guide, but I'll keep searching. Most of the time my temp is in the 60's or low 70's. It's just programs that run a lot of cpu really take the temp up to the 80's, which I think is pretty warm.

---

### Post by macogw on 2007-01-03
Well my laptop goes all black screen and says "Critical temperature reached (87C) shutting down now" and 87C is reeeeally hot.  It says 87, then 75, then 87...back and forth.  Both are rather too hot.  Look into getting one of those laptop cooler-downers.  Even if the CPU isn't frying from it, too much heat shortens the life of the battery (and the hard drive, I think).

---

### Post by aidanr on 2007-01-03
88c is very high, i have a pentium 4 prescott, prescotts run very hot, with a zalman cooler mine ranges 40-50

with a laptop make sure you aren't covering any air intakes, if it's sitting on a desk you may want to put something under it to raise the back of the laptop off the desk a bit to help airflow, and you might want to get a can of compressed air at it to clear out any dust

---

### Post by k1001001 on 2007-01-03
You might want to consider getting one of those Targus cooling platforms for laptops. They sit underneath the laptop and have two fans blowing the heat out from underneath the laptop. It's powered through the USB port, and it runs without any installation. I use one and it seems to help.

---

### Post by Laptop1 on 2007-01-03
how do you check the temps?

---

### Post by Frank Golden on 2007-01-03
> **Laptop1 said:**
> how do you check the temps?
In Ubuntu Gnome I use computertemp. Get it from Synaptic Package Manager. Search for it in Synaptic.
Once installed right click the panel and choose +add to panel. Find the Computer Temperature Monitor applet
and add. It will run and boot with Ubuntu and provide real time monitoring of your processor temps. Right click and choose preferences to change from F to C or vice versa.

---

### Post by macogw on 2007-01-03
when i did apt-cache search computertemp nothing came up.  Are you sure that's the name of the package?

---

### Post by k1001001 on 2007-01-03
> **macogw said:**
> when i did apt-cache search computertemp nothing came up.  Are you sure that's the name of the package?
Same result for me. I would like to find a program like this though.

---

### Post by confused57 on 2007-01-03
I use lm-sensors with gkrellm:

[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

---

### Post by haiku99 on 2007-01-03
there is some good info on maximum temperatures for various cpu's at [http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)
FWIW gkrell is one program (there are a few, but I have no idea which is best) that monitors temperature and it is available in synaptic.

---

### Post by Frank Golden on 2007-01-03
> **k1001001 said:**
> Same result for me. I would like to find a program like this though.
The program name is most definitely computertemp.
Search for it in Synaptic Package Manager. Use the search feature in Synaptic.
Make sure your 'universe' and 'multiverse' and 'restricted' repositories are enabled.

I just look for and found this app. No problem.
I think this is a Gnome app only.

---

### Post by macogw on 2007-01-03
i have gkrellm but it tells me no lm-sensors. lm-sensors couldnt find a temperature on my mobo it said

I'm using Gnome and I have all the official repos + mediuntu and beryl and a few others.  nothing comes up searching for computertemp

---

### Post by Frank Golden on 2007-01-03
> **macogw said:**
> i have gkrellm but it tells me no lm-sensors. lm-sensors couldnt find a temperature on my mobo it said

I'm using Gnome and I have all the official repos + mediuntu and beryl and a few others.  nothing comes up searching for computertemp
Very strange try 

sensors-applet

this is another Gnome applet that does the same thing. If you find either one it will place an applet
in your +Add To Panel menu.

---

### Post by crimesaucer on 2007-01-03
The Targus cooling platforms and a compressed can of air sound like really good suggestions. I think I will definitely get the platform and clean all of the dust from my fans, thanks.

Does anyone know if you can control the fans of a hp pavilion dv4230us with an Intel 910GML celeron m? It's a really low grade computer so I don't think I will be able to adjust the fan speeds. 

I have already tried the makdev.sh and the pwmconfig from the wiki page, but I failed most all of the probes and haven't tried to figure it out yet. The lm-sensors work perfectly with Conky so I don't know why I failed most all of the probes. I have saved all of the info from when I tested the lm-sensors with ```
sudo sensors-detect
``` and ```
sudo sensors -s
```

@ Laptop1, I use the lm-sensors and Conky 1.4.5

---

### Post by DougieFresh4U on 2007-01-03
> **Frank Golden said:**
> In Ubuntu Gnome I use computertemp. Get it from Synaptic Package Manager. Search for it in Synaptic.
Once installed right click the panel and choose +add to panel. Find the Computer Temperature Monitor applet
and add. It will run and boot with Ubuntu and provide real time monitoring of your processor temps. Right click and choose preferences to change from F to C or vice versa.

I searched through Synaptic and there was not even a word computer in there.  There is : complearn-tools and the next is: config-manager :confused:

---

### Post by _duncan_ on 2007-01-03
not sure if this is what you're looking for, but I usually just open a terminal and type the following to get temperature reading:
```
acpi -t
```

---

### Post by Olav on 2007-01-03
> **Frank Golden said:**
> The program name is most definitely computertemp.
Search for it in Synaptic Package Manager. Use the search feature in Synaptic.
Make sure your 'universe' and 'multiverse' and 'restricted' repositories are enabled.

I just look for and found this app. No problem.
I think this is a Gnome app only.
You must have downloaded it from [http://computertemp.berlios.de/](http://computertemp.berlios.de/) - I did.

It is NOT in any of the well known Ubuntu repositories, but it will indeed show up in Synaptic after you installed it (so you can uninstall it should you like to).

---

### Post by Frank Golden on 2007-01-03
> **Olav said:**
> You must have downloaded it from [http://computertemp.berlios.de/](http://computertemp.berlios.de/) - I did.

It is NOT in any of the well known Ubuntu repositories, but it will indeed show up in Synaptic after you installed it (so you can uninstall it should you like to).
Nope in Edgy I used the search feature in Synaptic (press the search button, type computertemp and press go). I am pretty sure I did the same for dapper.
My edgy install is a fresh install so it didn't inherit any thing from dapper.

How about sensor-applet. This does the same thing. See

[http://sensors-applet.sourceforge.net/index.php?content=packages](http://sensors-applet.sourceforge.net/index.php?content=packages)

According to the above link it is available in the Ubuntu universe repos. Make sure your universe,multiverse and restricted repos are active.
Open /etc/apt/sources.list using this command sudo gedit /etc/apt/sources.list and uncomment the repos for multiverse, universe and restricted (remove the # from in front of them)

sudo apt-get install sensors-applet

Below is link to .deb download for computertemp

[http://prdownload.berlios.de/computertemp/computertemp_0.9.3-0ubuntu1_all.deb](http://prdownload.berlios.de/computertemp/computertemp_0.9.3-0ubuntu1_all.deb)

You should be able to install using debian package manager.

Your link appears to be dead at this time.

---

### Post by DougieFresh4U on 2007-01-03
> **_duncan_ said:**
> not sure if this is what you're looking for, but I usually just open a terminal and type the following to get temperature reading:
```
acpi -t
```

dougie@DougiesToyBox:~$ acpi -t
No support for device type: thermal

---

### Post by DougieFresh4U on 2007-01-03
> **Frank Golden said:**
> Nope in Edgy I used the search feature in Synaptic (press the search button, type computertemp and press go). I am pretty sure I did the same for dapper.
My edgy install is a fresh install so it didn't inherit any thing from dapper.

How about sensor-applet. This does the same thing. See

[http://sensors-applet.sourceforge.net/index.php?content=packages](http://sensors-applet.sourceforge.net/index.php?content=packages)

According to the above link it is available in the Ubuntu universe repos. Make sure your universe,multiverse and restricted repos are active.
Open /etc/apt/sources.list using this command sudo gedit /etc/apt/sources.list and uncomment the repos for multiverse, universe and restricted (remove the # from in front of them)

sudo apt-get install sensors-applet

Below is link to .deb download for computertemp

[http://prdownload.berlios.de/computertemp/computertemp_0.9.3-0ubuntu1_all.deb](http://prdownload.berlios.de/computertemp/computertemp_0.9.3-0ubuntu1_all.deb)

You should be able to install using debian package manager.

Your link appears to be dead at this time.
I used the link for deb and downloaded/package installer installed. Now where do I find it to use it? Thanks

---

### Post by kerry_s on 2007-01-03
For AMD cpu's try-> athcool
For Pentium cpu's try-> cpudyn 

I use both of these and they bring the temp down alot, my amd runs in the 30's & my pentium runs in the 50's.

---

### Post by Frank Golden on 2007-01-03
> **DougieFresh4U said:**
> I used the link for deb and downloaded/package installer installed. Now where do I find it to use it? Thanks
Right click the panel and choose +Add To Panel, find 'Computer Temperature Monitor'
in resulting menu and add to panel. Right click icon after install and choose preferences
to change from F to C etc.

---

### Post by DougieFresh4U on 2007-01-03
I know this is not my thread, sorry if I intruded, although I found info helpfull from this. Now I followed links and other posts but the screenshots kind of contradict each other. some one please look over and maybe explain](*,) Synaptic shows installed but when I try t0o add launcher it say not installed

---

### Post by Frank Golden on 2007-01-03
> **DougieFresh4U said:**
> I know this is not my thread, sorry if I intruded, although I found info helpfull from this. Now I followed links and other posts but the screenshots kind of contradict each other. some one please look over and maybe explain](*,) Synaptic shows installed but when I try t0o add launcher it say not installed
Apparently your computer does not have termal support.
These programs get there info from ACPI sensors. What processor are you using?
They may not work on older desktop processors.

---

### Post by DougieFresh4U on 2007-01-03
> **Frank Golden said:**
> Apparently your computer does not have termal support.
These programs get there info from ACPI sensors. What processor are you using?
They may not work on older desktop processors.

It is an older model I use for playing around w/Feisty (not my main machine) I know it's a Dell  w/Intel mother board -Celeron (Coppermine) If you give me a code I can produce other specs. Is there not other ways to have thermal support for older models?

---

### Post by Frank Golden on 2007-01-04
> **DougieFresh4U said:**
> It is an older model I use for playing around w/Feisty (not my main machine) I know it's a Dell  w/Intel mother board -Celeron (Coppermine) If you give me a code I can produce other specs. Is there not other ways to have thermal support for older models?I don't know of a command to tell whether or not you proc/motherboard has sensors or not. Perhaps others here can chime in. I suspect that you don't, judging by the error message when trying to add Computer Temperature Monitor. I think this kind of support is fairly new. My last laptop (HP Pavillion 3010us)
did not support his kind of thermal monitoring. It used a pentium M first gen mobil processor. It is now about 3 years old.

---

### Post by Frank Golden on 2007-01-04
> **DougieFresh4U said:**
> It is an older model I use for playing around w/Feisty (not my main machine) I know it's a Dell  w/Intel mother board -Celeron (Coppermine) If you give me a code I can produce other specs. Is there not other ways to have thermal support for older models?I don't know of a command to tell whether or not you proc/motherboard has sensors or not. Perhaps others here can chime in. I suspect that you don't, judging by the error message when trying to add Computer Temperature Monitor. I think this kind of support is fairly new. My last laptop (HP Pavillion 3010us)
did not support his kind of thermal monitoring. It used a pentium M first gen mobil processor. It is now about 3 years old.

I think the command you tried earlier 

acpi -t

and the response you got was a definite clue that these little applets wouldn't work.
They depend on a piece of hardware attached to the chip. A thermal diode or thermistor.


PS sorry for the double post.

---

### Post by luvinit on 2007-01-04
Don't know whether it is useful but I will tell you my recent experience. I have an AMD athlon 64 3000. It can, according to my comp, take a little over 110 degrees C before the motherboard shuts it down. I have done this many times with no apparent damage to the cpu. The problem was that the heatsink was coming away from the chip. I now have it tied on with a piece of wire, having first wiped off the heat conductive paste and replaced with some new stuff, arctic silver. It now does 35-40 degrees regardless of load.

---

### Post by crimesaucer on 2007-01-18
I just got the Lian Li 17" inch laptop cooler and it has brought my temps way down. I'm now getting an average temp around the lower to mid 40.C's when it used to be the 60.C's and 70.C's.

Thanks for the suggestion, but I researched it and found out aluminum is the way to go.

---

