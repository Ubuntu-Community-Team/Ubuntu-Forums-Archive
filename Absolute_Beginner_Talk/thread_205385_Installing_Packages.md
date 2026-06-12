---
title: "Installing Packages"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by veagles on 2006-06-28
I am new to Linux. I dont have an internet connection. I was not able to play .mp3 or .mpg files. I downloaded all the gstreamer0.10 packages from packages.ubuntu.com. When I double click on the package file or try sudo dpkg -i packagename.deb I get some cache or dependency error.
What could be wrong?
Is there anything else that i need to install to play mp3 and mpg files?

---

### Post by aysiu on 2006-06-28
Ubuntu with no internet is painful, as it has no official add-on CDs.

A user here named CompShrink has been kind enough to create an unofficial add-on CD, though:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by veagles on 2006-06-28
[QUOTE=aysiu]Ubuntu with no internet is painful, as it has no official add-on CDs.

A user here named CompShrink has been kind enough to create an unofficial add-on CD, though:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)[/QUOTE]

I dont think I can download that 200 MB add on. Can you tell what exactly are the packages i need to install to be able to play mp3 and mpg files?

---

### Post by aysiu on 2006-06-28
Well, [http://packages.ubuntu.com](http://packages.ubuntu.com) helps you see what dependencies each package has.

I'm assuming you have another computer that does have an internet connection. Can you run the Ubuntu live CD on it?

---

### Post by veagles on 2006-06-28
[QUOTE=aysiu]Well, [http://packages.ubuntu.com](http://packages.ubuntu.com) helps you see what dependencies each package has.

I'm assuming you have another computer that does have an internet connection. Can you run the Ubuntu live CD on it?[/QUOTE]

I got the Ubuntu CD from a friend. I have Ubuntu installed in my comp. No internet connection. What I can do is download a max of about 50 MB of packages at college and install it in my comp. Cant run linux here. I just want the ability to play mp3 and mpg files. Can you tell me the exact packages?

---

### Post by xtacocorex on 2006-06-28
It's really hard to give you the exact packages, because of the dependencies, we may be listing off a hundred or so packages.

I personally don't have the time to go figure out what packages I installed to get audio and video to work, also because I just blindly installed a bunch of stuff to cover base so if I gave you a list, it might be way more than you actually need.

I would go here: [http://www.ubuntuforums.org/forumdisplay.php?f=143](http://www.ubuntuforums.org/forumdisplay.php?f=143)
This is BUMPS and it will do basic multimedia setup. I don't know how large the packages it will download are, but I'm sure it's less than 50MB. To download it, go to the development thread. The problem is that it uses apt to install so you need a constant internet connection.

I would suggest Automatix, but in this case, you don't need the extra stuff that it can install.

---

### Post by aysiu on 2006-06-28
So no Ubuntu live CD, huh? Because you could probably use the live CD to download at college the packages you need and then transfer them to your computer.

This is what you should download:
[http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly)

By the way, can you tell your friend it's not very nice to just hand somebody who doesn't have an internet connection a Ubuntu CD?

---

### Post by veagles on 2006-06-28
[QUOTE=aysiu]So no Ubuntu live CD, huh? Because you could probably use the live CD to download at college the packages you need and then transfer them to your computer.

This is what you should download:
[http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/dapper/libs/gstreamer0.10-plugins-ugly)

By the way, can you tell your friend it's not very nice to just hand somebody who doesn't have an internet connection a Ubuntu CD?[/QUOTE]

Thanks for the reply. I will download the Ubuntu Plus add on. Well, my friend know nothing about ubuntu. He got it for me, from his cousin.

---

### Post by xtacocorex on 2006-06-28
[QUOTE=aysiu]Well, [http://packages.ubuntu.com](http://packages.ubuntu.com) helps you see what dependencies each package has.[/QUOTE]

I will have to remember that.

---

