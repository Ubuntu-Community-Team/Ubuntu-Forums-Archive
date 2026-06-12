---
title: "MacBook Pro (latest) + Ubuntu Temperature paranoia"
date: 2007-11-13
forum: Apple Intel Users
---

### Post by ChardFi on 2007-11-13
Right, I know there are a lot of threads in this forum that seem to relate to this subject but i can't seem to get the information i need for my spanking new Mackbook pro.

I'm triple booting Vista, OSX and Ubuntu 7.10 and i must say that overall getting stuff to work as been pretty easy. However I've still got this massive paranoia that my V expensive purchase is going to cook it's self. 

I've had instructions to set the fan speed higher with the following command but this just returns a permission denied error.

```
echo 1 > /sys/devices/platform/applesmc.768/fan1_manual
echo 1 > /sys/devices/platform/applesmc.768/fan2_manual
```

And

```
echo 4000 > /sys/devices/platform/applesmc.768/fan1_output
echo 4000 > /sys/devices/platform/applesmc.768/fan2_output
```

I presumed this was because the files are in use so thought i would mod them by accessing the folder from my windows partition. This is where i learned that the folder /sys/ is obviously for loaded modules and therefore cannot be edited while Ubuntu is down either.

I have dug a little deeper and have now noticed that the folder /sys/devices/platform/applesmc.768 doesn't exist when the laptop boots, but does appear if i type 

```
sudo modprobe applesmc
```

is this what the problem is? 
Can i get this applesmc.768 folder to exist at startup?
Can i get applesmc to load with an new minimum fan speed?
How can i see the current temperature?

So many questions....


Thanks in advance.

Chard

---

### Post by pveith on 2007-11-13
Erm. Just don't do this... First to get this working you need to "sudo" the command, but seriously: Don't switch to complete manual Fan speed setting. Just ajust the minimal speed of your fan, cause they can speed up to 6200 rpm. If you force them on 4000 you deny them the possibility for full speed...

```
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan1_min
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan2_min

```

additionaly type in the command
```
sudo lsmod|grep applesmc
```
to see if the dirver is up and running (the command should produce some output, if not then applesmc is not loaded). If it is not automatically started you might want to add a "applesmc" to the file /etc/modules (just ad a line at the end off the file which contains "applesmc"). On next bootup apllesmc will be loaded...

```
sudo gedit /etc/modules
```

The easiest way to automatically edit Fan-Speed on startup would be to add the relevant lines (e.g. "echo 4000 > /sys/devices/platform/applesmc.768/fan1_min", Yes this time no sudo... ;) ) at the end of /etc/rc.local, but before any "exit 0" line. 

```
sudo gedit /etc/rc.local
```

---

### Post by ChardFi on 2007-11-13
Cheers matey that worked a treat!

-- I'll see how she goes with them set at 3500 as a minimum and post back here with my findings. Might help someone else.

Thanks again, This one has been bothering me for a week now.

Peace and Ubuntu

---

### Post by ChardFi on 2007-11-15
MacBook Pro users lend me your ears!

Continuing from my previous post my MacBook pro is still getting a lot hotter than under XP or OSX. Has anyone else been experiencing this problem?

I've also found this [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl]("https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl")
Has anyone given this a go? If so what we the results?

I'm really running out of ideas now and i have massive paranoia about cooking my laptop. I would like to recompile my own kernel but past experience of this has left me with a screwed system - So many questions i don't know the answer to :-(


Help anyone?

---

### Post by cyberdork33 on 2007-11-15
> **ChardFi said:**
> MacBook Pro users lend me your ears!

Continuing from my previous post my MacBook pro is still getting a lot hotter than under XP or OSX. Has anyone else been experiencing this problem?

I've also found this [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)
Has anyone given this a go? If so what we the results?

I'm really running out of ideas now and i have massive paranoia about cooking my laptop. I would like to recompile my own kernel but past experience of this has left me with a screwed system - So many questions i don't know the answer to :-(


Help anyone?

I haven't seen anyone even mention this script before. Probably worth a try.

---

### Post by eddietours on 2008-05-14
anyone knows if that script works my Macpro runs really hot :(

---

### Post by aztechclan on 2008-06-14
Yes, the script works.  I've been using it for months and it keeps my MBP at about 59degrees core temp.  Without this script you will burn your book into oblivion.  The default install of both Ubuntu hardy and gusty had ZERO fan speed.  That is VERY BAD!

So yea, follow that wiki guide and also add the fan/core monitor applet to your gnome panel so you can watch the temps.

---

### Post by trekbiker on 2008-07-05
hello everyone,

been reading up and this and trying to get the temperature control working on my mac mini.  with kernel 2.6.25.10

I've made great progress,  however I think I may have done something wrong in my last kernel.  I compiled a kernel with applesmc in it..  and I think I needed to have it as a loadable module.  

as of right now I get no output from sudo insmod|grep applesmc

and I don't appear to have applesmc.ko in my modules directory 

I do however get temperatures and fan speed when I run the sensors command.  but any change in the minimum speed doesn't raise or lower the speed of the fan.  

I read here: [http://http://www.jasonparekh.com/linux-on-macbook/]("http://http://www.jasonparekh.com/linux-on-macbook/") that the default is to only view the minimum fan speed,  and that you couldn't change it without a patch.  but I don't know how accurate that is or how long ago it was written.  

just a little background... my mac mini has an issue with its SMC controller on the system board,  it runs the fan full blast all the time,  but I found a program for OSX that can stop it from doing that..  and controls the fan perfect.  its at [http://www.lobotomo.com/products/FanControl/]("http://www.lobotomo.com/products/FanControl/")

so I know it is possible to fix this issue in linux thru software as well.  

if anyone has any advice on this I would appeciate it.

---

