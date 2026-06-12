---
title: "[SOLVED] Visual Effects"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by DaMann on 2008-03-07
It wont let me change the visual effects at all. If I click on Normal, Extra, or Custom it just says it cant do it. I know my graphics card can handle it its a GeForce 8800 GTX. I read some other things and followed then through but there was no luck. 

Please Help

-DaMann

---

### Post by NightwishFan on 2008-03-07
Go to system/administration/restricted drivers manager. See if the nvidia restricted drivers are enabled.

---

### Post by DaMann on 2008-03-07
> **NightwishFan said:**
> Go to system/administration/restricted drivers manager. See if the nvidia restricted drivers are enabled.

It told me my hard ware does not need any restricted drivers.

---

### Post by NightwishFan on 2008-03-07
Open a terminal and type  glxgears  and post the response.

---

### Post by SuperCow56 on 2008-03-07
I went through this problem a couple days ago.  Try going to Add/Remove and installing the nvidia binary. If that doesn't work, then manually install the nvidia drivers from [http://www.nvidia.com](http://www.nvidia.com)

---

### Post by DaMann on 2008-03-07
> **NightwishFan said:**
> Open a terminal and type  glxgears  and post the response.

Well.... There are three gears, and they are spinning....

---

### Post by NightwishFan on 2008-03-07
That believe that means you have open gl 3d acceleration. Which means that your card should support the 3d effects. I am not on Ubuntu, so I cannot tinker with a solution myself. I will look around a bit.

---

### Post by prshah on 2008-03-07
Are you using the vesa server by any chance? post the output of "cat /var/log/Xorg.0.log | grep -i driver". This will give us a clue.

Or simply use the command "sudo dpkg-reconfigure xserver-xorg" to reconfigure your display and screen parameters (Pretty self-explanatory and easy to use).

Cheers,
PRShah

---

### Post by kesman on 2008-03-07
Type in terminal 
```

glxinfo | grep rendering

```
If you get direct rendering: YES then everything should be ok.

---

### Post by oedha on 2008-03-07
> **DaMann said:**
> It told me my hard ware does not need any restricted drivers.

can you open terminal and type :==> sudo dpkg-reconfigure -phigh xserver-xorg
and make sure you choose "nvidia"
then sudo /etc/init.d/gdm restart  <== to restart your gnome
try to set the visual effect again

---

### Post by DaMann on 2008-03-07
sudo dpkg-reconfigure -phigh xserver-xorg

That gives me this. 

xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080307174653

glxinfo | grep rendering 

I get No.

---

### Post by DaMann on 2008-03-07
Also I downloaded the NVidia drivers and still didn't work.

---

### Post by DaMann on 2008-03-07
I'm not quite sure what the rules are for this site but I'm sure giving this a bump is better than making a new thread. 
I have been trying to enable Visual Effects but it wont work. Just says I can't. I use an NVidia 8800 GTX. Nothing has worked so far and I am yet to find a guide that has worked for me. 

Please help,
DaMann

---

### Post by PmDematagoda on 2008-03-07
Can you open Nvidia Settings using:-
```
gksudo nvidia-settings
```
and look around to see if there are any flaws.

---

### Post by DaMann on 2008-03-07
> **PmDematagoda said:**
> Can you open Nvidia Settings using:-
```
gksudo nvidia-settings
```
and look around to see if there are any flaws.

It opened a rather bare Nvidia control panel. I am just kind of used to the Windows version. 
There are a few checkboxes and everything is checked besides "Include X Display Names in the Config File"

---

### Post by PmDematagoda on 2008-03-07
Enter:-
```
compiz --replace
```
in a terminal, post any errors you receive.

---

### Post by DaMann on 2008-03-07
> **PmDematagoda said:**
> Enter:-
```
compiz --replace
```
in a terminal, post any errors you receive.

Checking for XGL: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by PmDematagoda on 2008-03-07
Could you please post as to how you installed the Nvidia driver in the first place?

---

### Post by DaMann on 2008-03-07
> **PmDematagoda said:**
> Could you please post as to how you installed the Nvidia driver in the first place?

I went to add/remove programs picked the one that sounded right. Used the command to enable it and restarted.

---

### Post by PmDematagoda on 2008-03-07
And what exact package/entry did you select?

---

### Post by DaMann on 2008-03-07
> **PmDematagoda said:**
> And what exact package/entry did you select?

As in the one from the add/delete? The Nvidia binary X.Org driver

---

### Post by PmDematagoda on 2008-03-07
I think the binary driver may be the one causing the problem.

Please refer to this [thread]("http://ubuntuforums.org/showthread.php?t=665018"), perhaps one of those solutions could solve your problem.

---

### Post by DaMann on 2008-03-07
> **PmDematagoda said:**
> I think the binary driver may be the one causing the problem.

Please refer to this [thread]("http://ubuntuforums.org/showthread.php?t=665018"), perhaps one of those solutions could solve your problem.

Nope none of em worked. 

I would also like to say this forum is great. Many people are willing to help and its active... sometimes a little to active but better than no activity.

---

### Post by Tatty on 2008-03-07
Have you tried installing the latest driver from the Nvidia site?

---

### Post by DaMann on 2008-03-07
> **Tatty said:**
> Have you tried installing the latest driver from the Nvidia site?

I tried, I got the file but it just wouldn't run...

---

### Post by Tatty on 2008-03-07
> **DaMann said:**
> I tried, I got the file but it just wouldn't run...

What did you do to try to make it run?

It will definately run, but there are a few hurdles to jump before it will.

---

### Post by kesman on 2008-03-08
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You could also download Envy from that page and use it to automagically install the nvidia-drivers for you.

---

### Post by prshah on 2008-03-08
Once again, are you sure that the drivers in use are nv and not vesa? Pls check by command 

"cat /var/log/Xorg.0.log | grep -i driver". 

This will give us a clue.

Cheers
PRShah

---

### Post by DaMann on 2008-03-09
> **prshah said:**
> Once again, are you sure that the drivers in use are nv and not vesa? Pls check by command 

"cat /var/log/Xorg.0.log | grep -i driver". 

This will give us a clue.

Cheers
PRShah

curtis@curtis-desktop:~$ cat /var/log/Xorg.0.log | grep -1 driver
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
--
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
--
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
--
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
--
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) v4l driver for Video4Linux
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
 
I got that which says I'm using Vesa but I changed it through the screens and graphics.... hmm

Edit: Right now I am installing the NVidia drivers with Envy. Hope it works!

Edit: It works thanks guy I love this forum!

---

