---
title: "Macbook drivers"
date: 2009-04-21
forum: Apple Hardware Users
---

### Post by slanker70 on 2009-04-21
Hi,

This is my first ever post so hello all.

I've just succesfully triple booted my macbook 5.1, so now I'm trying to install all the drivers necessary for Ubuntu by following the instructions in this link:

[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)

The problem when I tried to follow the first instruction whih is:

> sudo apt-get install applesmc-dkms

It says that the package can't be found. The next thing I did was try to install the package by following the instructions on this link:

[https://wiki.ubuntu.com/MactelSupportTeam/PPA#Installation](https://wiki.ubuntu.com/MactelSupportTeam/PPA#Installation)

So again I followed the first instruction which is:

> Make sure you have these lines in /etc/apt/sources.list

But it keep saying that I don't have permission.

So now I'm stuck and since I'm a complete newbie regarding to linux and ubuntu, I was wondering whether there's anybody who can help me with this issue. Please help.

Reagrds,

Perdana Putra

---

### Post by buntuLo on 2009-04-21
> **slanker70 said:**
> (...) it keep saying that I don't have permission.
when do you get the permission error? are you using the sudo command also for editing the /etc/apt/sources.list file?

---

### Post by horstfenchel on 2009-04-21
got the same problem here.
just set up ubuntu 8.04 on my macbook 5.
i followed these [https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA) instructions.
then i tried:
sudo apt-get install applesmc-dkms
too, but get this result:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package applesdmc-dkms

:( (that happens with all of the packages recommended in this guide: [https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid))
internet is working btw and i did update (and reboot).

ps: and i did the editing of the sources.list file with the application that opened when i double-clicked on it :o

---

### Post by cyberdork33 on 2009-04-21
> **slanker70 said:**
> But it keep saying that I don't have permission.

Use 'sudo' (or gksudo for GUI applications) to get root permissions to perform actions.
```
gksudo gedit /etc/apt/sources.list
```

> **horstfenchel said:**
> 
sudo apt-get install applesmc-dkms
too, but get this result:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package applesdmc-dkms

that happens with all of the packages recommended in this guide
It sounds like the PPA is not added properly to your sources.list file. Can you post it here?

---

### Post by horstfenchel on 2009-04-21
the last part of the file:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

thanks for helping :)

---

### Post by cyberdork33 on 2009-04-21
> **horstfenchel said:**
> the last part of the file
Ok, then you updated:
```
sudo aptitude update
```

and make sure that near the end there is no error message when it tries to retrieve the mactel ppa packages list.

---

### Post by slanker70 on 2009-04-23
Hi,

Thank all your for the replies. I've managed to complete all the instructions except for

> To enable the built-in microphone, start System > Preferences > Volume Control (gnome-volume-control) and in the Recording tab activate audio recording in the first Capture column. Finally, in the Option tab set Front Mic to be the first Input Source. 

There's no volume control on the preferences tab?

There's a couple of more things that I'm curios about:
 
1. The LED light on the caps lock key is not working

2. The hash key # (alt + 3) only works with alt key located on the right side but not the left.

Please help.

Thanks again,

Perdana Putra

---

### Post by cyberdork33 on 2009-04-23
> **slanker70 said:**
> There's no volume control on the preferences tab? you can get to it through the speaker icon in your system tray area.

> **slanker70 said:**
>  The LED light on the caps lock key is not working
uninstall mouseemu

> **slanker70 said:**
> The hash key # (alt + 3) only works with alt key located on the right side but not the left.there are a lot of bug affecting the international apple keyboards. I believe the right alt key is mapped to the alt-gr key and the left alt key is just alt. What layout are you using?

---

