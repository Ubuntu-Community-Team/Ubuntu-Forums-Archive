---
title: "MBA and Ubuntu"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by othsy2k on 2008-05-03
I'll admit it was not easy to get this far with my MBA. I followed the how tos in other forums and postings about installing Ubuntu on a Macbook Air.

At this point the only OS I have is Ubuntu 8.04. I tried using Boot Camp to install Ub but each time (using rEFIT or not) the only partition recognizable was the OSX partition. So...bah! I blew the whole thing away and now I have a running copy of Linux.

I was able to get the wifi working following the forums. Make sure you pay close attention to all steps (yeah that's right I was a bit impatient).

As of now I can't get the light up keyboard stuff to work, or right clicking.

For the keyboard lights I tried installing pommed. When I used apt the only available package was 15. I know that 16 is out and 17 is in beta....but I'm still not the best at installing from source. And now that I have installed 15 I have no idea how to upgrade. Grrrr

I've read some grubbling about how to get the right click activity working, but nothing that I've tried yet.

Oh yeah, I also got the audio working quite nicely.

Anyone have suggestions for where to go from here?

---

### Post by cyberdork33 on 2008-05-03
pommed 1.16 is in the mactel-support ppa:
[https://launchpad.net/~mactel-support/+archive]("https://launchpad.net/%7Emactel-support/+archive")

---

### Post by othsy2k on 2008-05-04
Awesome. Thanks. I added the repository and updated pommed it started and I didn't get the error like before, but now what?

I thought that pommed would auto-magically make the hot-keys work and the abi-light sensor work.

Is there something I need to enable before all that happens?

---

### Post by cyberdork33 on 2008-05-04
what "hot keys" are you referring to?

---

### Post by othsy2k on 2008-05-04
Oh, yeah I guess I should have been a little more specific. Sorry.

In OSX the F keys raise and lower the volume, brighten and darken the screen. I thought that pommed allowed for that in Linux.

Why don't we back up a little. What I've read pommed can do is:

"pommed adjusts the LCD backlight, sound volume, keyboard backlight or ejects the CD-ROM drive.

pommed also monitors the ambient light sensors to automatically light up the keyboard backlight.

Optional support for the Apple Remote control is available."

All this is great, but I think I'm missing a step. After I install pommed the cmd prompt says that pommed has started successfully (something along those lines basically no errors). Where do I go from here to make it do all that it been promoted to do?

---

### Post by cyberdork33 on 2008-05-04
> **othsy2k said:**
> Oh, yeah I guess I should have been a little more specific. Sorry.

In OSX the F keys raise and lower the volume, brighten and darken the screen. I thought that pommed allowed for that in Linux.

Why don't we back up a little. What I've read pommed can do is:

"pommed adjusts the LCD backlight, sound volume, keyboard backlight or ejects the CD-ROM drive.

pommed also monitors the ambient light sensors to automatically light up the keyboard backlight.

Optional support for the Apple Remote control is available."

All this is great, but I think I'm missing a step. After I install pommed the cmd prompt says that pommed has started successfully (something along those lines basically no errors). Where do I go from here to make it do all that it been promoted to do?you shouldn't have to do anything. if the function keys don't work as expected, try holding the FN key to access them.

---

### Post by othsy2k on 2008-05-05
I tried holding the fn key down, but nothing new seemed to happen. Do you think this might be because I chose a Mac keyboard layout during install?

I ran the pommed with the -f option. It recognizes that I'm using a MBA, but at the end there was an error that kept repeating:

 E: Not primary DBus name owner

I had to ctrl-c to kill it.

BTW thanks for your help with this. 

Beyond pommed do you know any good ways to get my right click working?

---

### Post by cyberdork33 on 2008-05-05
> **othsy2k said:**
> Beyond pommed do you know any good ways to get my right click working?
It depends on what you mean by that, but you can get many of the more advanced touchpad features on the Macbook Air by using touchd.
[http://tannewt.org/touch/](http://tannewt.org/touch/)

---

