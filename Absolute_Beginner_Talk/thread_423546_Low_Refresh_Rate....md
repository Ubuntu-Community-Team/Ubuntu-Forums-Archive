---
title: "Low Refresh Rate..."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Udedenkz on 2007-04-26
NOTE: I am insane!!!!! eat cabbage!!! THIS IS A VERY BADLY ORGANIZED POST. SORRY. JIGGLE

Thats the first problem... the OS seems to install a driver or whatever for Nvidia when I clicked around... restarted... clicked on that same thing that installed me something nvidia... got jiggly windows!!! :D Jiggly!!! awesome!

Ok, back to topic...

So, I was still... like... looks like 800x600 or something... hmmn.... click click click.... screen size thing!!! found it! YAY! but it doesn't even go to a refresh rate of 60Mhz, I wanted to set 72...

Windows allows 60-75Mhz... here it is like 50 to 50something...

I think it is blurry cuz of that...

Ummm....

Jiggly Windows!!!! I am still having fun with that!

Okey... I also have absolutely no idea about any terminology used...  ie: wtf is Universe and Multiverse and Dapper?

Also, is it possible to run Steam - CSS from this thing? Emulation there seems to be topics, here about this, ummm... will I be able to run anything DX or OGL with 4x AA?

I like it though... I mean, this thing is cool!
Jiggly windows!!!!!! :D YAY!!! I am still entertained by that!

There is FF2, FTW. And I played Mp3 easily and the interface ain't that different from Windows....

I think I messed up the installation though... No, no, Windows XP still boots.... I mean, I think I assigned 20gigs to swap file... i have no idea...

Also, what the Ctrl-Alt-Del of this thing?

I googled some weird stuff... does Ubu support 8x GPA with SA and FW? All the fancy things of Athlon?

Why cant I modify my NTFS hard drive files?

Does this thing have an NTFS defragger?

Ummm.... anyone like cheesecakes?

And where is Santa Fe/Albuquerque? Rio Rancho?

Nice World Editor thing...

I got,
AMD Athlon XP 3000+ (2.16? Ghz)
333Mhz FSB
AGP Nvidia GeForce 66 with 256 VRAM
1GIG DDRSDRAM
Nforce 2 Motherboard
1024*768 Monitor that looks crisp at 60 or 70
160 GB Master 7200 PATA HD with XP, 1 partition, 8 megs of space wasted for some reason,...
40GIG Slave have no clue PATA HD with this thing that I am typing this messege in, ummm.. Ubuntu... >.>
Lazer Pwnerer Mouse
Keyboard (i got extra buttons on it, what about them?)

and now I got Jiggly Windows!!!

Ok, I am bookmarking this thingy,,, and going to sleep cuz, like... it is 10:07 and I got some stupid 11grade hUM stuff... so I need my hours!!!

And if you are wandering why I tried this thing - it is becouse I am somewhat of an Antisocial Insane Furry Geek person...

Jiggly

---

### Post by Ecthelion on 2007-04-26
> Okey... I also have absolutely no idea about any terminology used... ie: wtf is Universe and Multiverse and Dapper?
Universe and multiverse are repositories. They are sources where your computer looks when you want to install new things. It from this kind of repositories that when you click on "install" things get downloaded.

> I think I messed up the installation though... No, no, Windows XP still boots.... I mean, I think I assigned 20gigs to swap file... i have no idea...
Maybe that a bit (read: way too) much. But that shouldnt cause a problem

> Also, what the Ctrl-Alt-Del of this thing?
What would you need that for?
> 
Why cant I modify my NTFS hard drive files?
You can read ntfs by default, but not write. This is because ntfs writing has been backengineered and could potentially messing up your system. (Not telling you that it does, but you don't have any guarantee that it wont)
> 
Does this thing have an NTFS defragger?
No. The way the system reads/writes to your disks makes defragmenting useless. Your system just doesn't messes up your disks so you don't have to reorganise them with a defragmentation...

> Ummm.... anyone like cheesecakes?
Yes :-)

For the rest of your jiggly windows thing -didn't understand much of it- ,if you want to install the official nvidia drivers, just do this:

[quote=pricechild]
STEP 2: Install nvidia drivers[/SIZE]
 
_**Option 1:**_

 Lupine's repos is now no-longer availiable. 
 You may use Envy, a Python script that eases installation of the official Nvidia and ATI drivers. Please see[ http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") (>=9631 driver needed...) 


_**Option2:**_
 
If you would prefer to install the nvidia drivers from nvidia's script, you may simply download the NVIDIA drivers from [here]("http://www.nvidia.com/object/unix.html"), then:
 
```
sudo nano /etc/default/linux-restricted-modules-common
```Make the last line look like```
[SIZE=-1]DISABLED_MODULES="nv"[/SIZE]
```[SIZE=-1]ctrl+x and y to save.

Then[/SIZE]
```
[SIZE=-1]sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev[/SIZE]
[SIZE=-1]sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common[/SIZE]
[SIZE=-1]sudo rm /etc/init.d/nvidia-*[/SIZE]
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
```The Nvidia script should change your xorg.conf to enable nvidia drivers & compositing.
 [B]
Remember that following this method requires a reinstillation of them every time the kernel changes.[/B][/quote]

But of course this is only if your not afraid of using the teminal :-)

---

### Post by u.b.u.n.t.u on 2007-04-26
Fiesty Fawn is broken.

It doesn't detect the correct resolution and refresh rate on some hardware.

---

### Post by aberry5555 on 2007-04-26
Furry!

---

### Post by Ecthelion on 2007-04-26
> **u.b.u.n.t.u said:**
> Fiesty Fawn is broken.

It doesn't detect the correct resolution and refresh rate on some hardware.

Well even then it's not that bad, you can easily configure it by hand...
Open a terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you just give it in by hand and everything works fine.

Btw, I don't think you should call that 'broken' since it's probably done so out of purpose...
If he doesn't know what your screen can handle, then it gives low freq etc options to make sure not to break your screen.

---

### Post by u.b.u.n.t.u on 2007-04-26
> **Ecthelion said:**
> Well even then it's not that bad, you can easily configure it by hand...
Open a terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you just give it in by hand and everything works fine.

Btw, I don't think you should call that 'broken' since it's probably done so out of purpose...
If he doesn't know what your screen can handle, then it gives low freq etc options to make sure not to break your screen.

Check this out:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

and this

[http://ubuntuforums.org/showthread.php?t=423745](http://ubuntuforums.org/showthread.php?t=423745)

Yes Fiesty Fawn is broken regarding screen resolutions and refresh rates on some hardware.

Editing the xorg.conf is a desperate act and does not do the same job as a working automated system - which isn't working properly and will hopefully be fixed by the time Gutsy Gibbon is released.

---

### Post by Ecthelion on 2007-04-26
For your launchpad bug:
> I'm upgrade my system to ubuntu **5.10**, after that, xorg can't load the correct resolution of the monitor ( 1024 x 768 ). I'ts only load 640x480. I've used dpkg-recunfigure xserver-xorg, and insert the correct values, but don't work. The system is a Samsung 753dfx and a gforce mx 200 32mb.
This talks about breezy or something

Also you link to the forum talks about Gutsy

This thread was for Feisty Fawn -or so I understood-




EDIT: sorry I just saw that the bug applies to all ubuntu versions.
while it's annoying, it's not hard to fix using the dpkg-reconfigure xserver-xorg
though I agree that's its not very user-friendly and has to change

---

### Post by u.b.u.n.t.u on 2007-04-26
I have extensively edited my xorg.conf and cannot achieve an acceptable outcome.

People are free to try this for themselves, editing xorg.conf to fix this,  but they should also know that such doesn't always work.

It really depends on the hardware.

---

### Post by Ecthelion on 2007-04-26
> **u.b.u.n.t.u said:**
> I have extensively edited my xorg.conf and cannot achieve an acceptable outcome.

People are free to try this for themselves, editing xorg.conf to fix this,  but they should also know that such doesn't always work.

It really depends on the hardware.

Why editing it by hand?
It's not something I would try and surely not something to propose to a beginner (remember where we are)

EDIT: Never mind, we are drifiting off from the guy we try to help :-)

---

### Post by ShadowVlican on 2007-05-02
> **Ecthelion said:**
> Well even then it's not that bad, you can easily configure it by hand...
Open a terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you just give it in by hand and everything works fine.

Btw, I don't think you should call that 'broken' since it's probably done so out of purpose...
If he doesn't know what your screen can handle, then it gives low freq etc options to make sure not to break your screen.
i would call it broken... in this day and age i shouldn't have to edit any file with specifications of my monitor to get additional resolution support

also while i agree with your last sentence, ALL displays within the last couple years have self protection that doesn't allow resolutions that it doesn't support (ie: my 5 year old 17" CRT has that protection... but my ~13" CRT from my 386 doesn't...)

> **u.b.u.n.t.u said:**
> Check this out:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

and this

[http://ubuntuforums.org/showthread.php?t=423745](http://ubuntuforums.org/showthread.php?t=423745)

Yes Fiesty Fawn is broken regarding screen resolutions and refresh rates on some hardware.

Editing the xorg.conf is a desperate act and does not do the same job as a working automated system - which isn't working properly and will hopefully be fixed by the time Gutsy Gibbon is released.
yea i hope it's fixed and also hope they improve this "feature" of ubuntu

---

