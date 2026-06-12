---
title: "Installing my nVidia drivers"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by K_Alex on 2007-05-23
Greetings

As the title of this thread suggests, I'm in the process of installing nVidia drivers on my box. Specifically, I'm running an nForce1 chipset and using the integrated graphics.

##MAJOR NOTE##
I have no direct internet to my linux box... Thats just how it is. So using add/remove is out the question. Everything I need, I collect using xp and then copy it over. And the only things I collect are .deb files. Through time I've learnt the High-Noob art of the Double-Click. Compiling things is still in my future.

Now, what i have so far is the NVIDIA-Linux-x86-1.0-9631-pkg1.run file from the nVidia site (one of their other .run files told me this is the one I need). After logging on, shuttuing down x server and running ```
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
``` it starts the installation and everything is going fine until it spits out a message saying:
ERROR: You do not appear to have libc header files installed on your system. Please install you distribution's libc development package.

Help... :(

---

### Post by Sparkster185 on 2007-05-23
You can look here: [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the libc-dev package for your version of Ubuntu.  Just do a search for "libc" and you'll find it.  I'm not sure if that site offers downloads of the .deb files though, as I always use Add/Remove and apt-get to install stuff.

You also might want to try to use Envy. [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) .  Though, when I tried to install the .deb I needed a bunch of dependencies, so you might have issues with no internet connection.

---

### Post by dstew on 2007-05-23
You need the Ubuntu Debian package libc6. Get it [here]("http://packages.ubuntu.com/feisty/base/libc6") if you have Feisty. If you keep getting errors, maybe you should install the general building packages build-essential and linux-headers for your particular kernel.

---

### Post by K_Alex on 2007-05-23
I've downloaded libc6 twice and both times i try to run it it says the file is either corrupted or i don't have the permissions to run it...
I'm busy downloading libc6-dev at the moment. hopefully i'll have more luck :)

Thanx guys.

---

### Post by Sparkster185 on 2007-05-23
Are you running the dpkg command with sudo before it?  You should always run apt-get or dpkg with sudo, since the installer needs to write to system folders.

---

### Post by K_Alex on 2007-05-23
Oh, and one more thing, I'm looking for the "GStremer extra plugins" and "GStreamer plugins for aac, xvid, ..."

I've scoured packages.ubuntu.com but nothing really fits the description, just a whole bunch of bits and pieces. Any ideas?

---

### Post by K_Alex on 2007-05-23
> **Sparkster185 said:**
> Are you running the dpkg command with sudo before it?

I'm running the double click command... :)   But I'll give yours a shot next time I boot up. Thanx

---

