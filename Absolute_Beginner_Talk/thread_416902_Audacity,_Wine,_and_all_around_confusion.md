---
title: "Audacity, Wine, and all around confusion"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by shoeshoemjr on 2007-04-21
Hey everyone, I'm pretty new to the Linux world. I've been doing a lot of research on how to do everything in Linux and how it differs in comparison to Windows. I saw that I was using alot of the same applications (open source things) and decided to try it out. I had been waiting for Fawn before I did it because I had heard about it's integrated wireless card drivers. 

Needless to say, I've made the switch and I love it. However, after looking through the Add/Remove.... and trying to install Wine and Audacity, along with a few others, it never lets me install them. Tells me I need to go to the Synaptic Package Manager, so I did. Tried to install from there as well, but it just tells me that I can't. Please help!

---

### Post by picpak on 2007-04-21
Do you get any errors? If so, can you please post them?

Also, try going to the terminal and posting the output of

```
sudo apt-get install audacity wine
```

---

### Post by shoeshoemjr on 2007-04-21
Okay, I tried to do it in the terminal and got this. Unfortunately I have no idea what ANY of this means. :(

```
matt@matt-desktop:~$ sudo apt-get install audacity wine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  audacity: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
            Depends: libmad0 (>= 0.15.1b) but it is not installable
            Depends: libsamplerate0 but it is not installable
            Depends: libwxgtk2.4-1 (>= 2.4.5.1ubuntu2) but it is not going to be installed
  wine: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
E: Broken packages

```

---

### Post by picpak on 2007-04-21
Hmm...

perhaps try installing those uninstallable programs to see what the problem is?

```
sudo apt-get install libid3tag0 libmad0 libsamplerate0 libwxgtk2.4-1 libartsc0
```

---

### Post by shoeshoemjr on 2007-04-21
Hmm... no luck there. 

```

matt@matt-desktop:~$ sudo apt-get install libid3tag0 libmad0 libsamplerate0 libwxgtk2.4-1 libartsc0
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libid3tag0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libid3tag0 has no installation candidate


```

---

### Post by Pobega on 2007-04-21
If you're on Feisty it looks to me like the devs forgot about a few packages. Maybe try apt-pinning it in from Edgy to see if it works right?

[Apt-Pinning for Beginners](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by shoeshoemjr on 2007-04-21
Apt what? I really have no idea what that means... sorry, i'm really really new.

---

### Post by picpak on 2007-04-21
I don't get why it can't install those files...have you added any unofficial repositories? Have you enabled any extra ones?

I guess, as a last resort, you could download all those .deb files:

[libid3tag0_0.15.1b-8_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-8_i386.deb)
[libmad0_0.15.1b-2.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb)
[libsamplerate0_0.1.2-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-2_i386.deb)
[libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/w/wxwindows2.4/libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb)
[libartsc0_1.5.6-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/arts/libartsc0_1.5.6-0ubuntu1_i386.deb)

And install them with:

```
sudo dpkg -i ~/Desktop/*.deb
```

---

### Post by paker on 2007-04-21
I just installed Audacity through Automatix. If you are as new to ubuntu as me, I recommend you install Automatix first. Automatix has a list of programs. All you have to do is to check mark the programs you want and click on install button.

For Automatix, go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) and choose the right link. It will guide you through installation. No "sudo apt-get ---" stuff.

I am working on wine myself. It is not in ubuntu Fiesty AMD64 (if that's what you are using) repository. You have to visit wine web site and download from there, just like Automatix.

---

### Post by Kilz on 2007-04-21
> **paker said:**
> I just installed Audacity through Automatix. If you are as new to ubuntu as me, I recommend you install Automatix first. Automatix has a list of programs. All you have to do is to check mark the programs you want and click on install button.

For Automatix, go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) and choose the right link. It will guide you through installation. No "sudo apt-get ---" stuff.

I am working on wine myself. It is not in ubuntu Fiesty AMD64 (if that's what you are using) repository. You have to visit wine web site and download from there, just like Automatix.

There is a 64bit wine .deb posted to the[ 64bit section in a post.]("http://ubuntuforums.org/showthread.php?t=297280")

---

### Post by shoeshoemjr on 2007-04-22
> **picpak said:**
> I don't get why it can't install those files...have you added any unofficial repositories? Have you enabled any extra ones?

I guess, as a last resort, you could download all those .deb files:

[libid3tag0_0.15.1b-8_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-8_i386.deb)
[libmad0_0.15.1b-2.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1_i386.deb)
[libsamplerate0_0.1.2-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libs/libsamplerate/libsamplerate0_0.1.2-2_i386.deb)
[libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/w/wxwindows2.4/libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb)
[libartsc0_1.5.6-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/arts/libartsc0_1.5.6-0ubuntu1_i386.deb)

And install them with:

```
sudo dpkg -i ~/Desktop/*.deb
```

okay, here's the terminal message I got when I did this...

```
matt@matt-desktop:~$ sudo dpkg -i ~/Desktop/*.deb
Password:
Selecting previously deselected package libartsc0.
(Reading database ... 88325 files and directories currently installed.)
Unpacking libartsc0 (from .../libartsc0_1.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-8_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-2.1_i386.deb) ...
Selecting previously deselected package libsamplerate0.
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.2-2_i386.deb) ...
Selecting previously deselected package libwxgtk2.4-1.
Unpacking libwxgtk2.4-1 (from .../libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb) ...
Setting up libartsc0 (1.5.6-0ubuntu1) ...

Setting up libid3tag0 (0.15.1b-8) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up libsamplerate0 (0.1.2-2) ...

dpkg: dependency problems prevent configuration of libwxgtk2.4-1:
 libwxgtk2.4-1 depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 libwxgtk2.4-1 depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing libwxgtk2.4-1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwxgtk2.4-1

```

what does all this mean? what am I doing here with the commands in the terminal?

---

