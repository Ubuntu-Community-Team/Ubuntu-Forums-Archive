---
title: "MacBook Pro stuck at install"
date: 2007-08-26
forum: Apple Intel Users
---

### Post by self-defence on 2007-08-26
Hi,

I recently got a MacBook Pro 15" and I'm desperately trying to install Ubuntu 7.04 on it.
I've already reinstalled MacOS X and resized the partition. I also got BootCamp installed and used the alternate cd to install Ubuntu and it worked. Even Grub installed without a hitch.
I've even been able to tweak the xorg so that I got the resolution up to 1280x800 (but with vesa not nv or nvidia driver)  and got the wifi working. But the rest is a bit of a problem.
I can't seem to get the cdrom to work, or the audio, or the screen brightness or the keyboard illumination or the isight. In fact I actually got isight to somehow work but it only worked ekiga and only under root and for a few seconds and then it crashed. 
So I thought I'd compile the mac kernel like in the instructions at the beginning of the forum. But  after adding the new kernel and rebooting the machine booted but not even the wired network card worked anymore. 
If I try to change screen brightness I get: 
```
unexpected maximum brightness value
```
and that's it.
If I try to run Pommed to turn on the keyboard illumination I get this error:
```
SMBIOS vendor name: [Apple Inc.]
E: Unknown non-Apple machine
```
I also can't seem to be able to read/write cds/dvds or eject them. :(

The Mac is a new one I think its a Santa Rosa model. 

I've already read tones of pages, posts and blogs trying to find a way how to get things working. But I just got more confused on how to get the HW working.

Can anyone help me in any way. I'm actually quite new to Linux, I've only been a user for about a year now but is there any hope and or way that I could get my mac in working order or am I barking up the wrong tree? Because MacOS is nice and everything, but what can I say Ubuntu grew on me and now I can't seem to live without it. :-D

Thanks for any and all help on this matter.

---

### Post by self-defence on 2007-08-27
Ok

I've got one thing working. The screen brightness and keyboard illumination works. I installed Pommed 1.8 (the 1.2 version doesn't work). It told me I had some issues with dependencies but I forced it and it works.  \\:D/ 

Now on to the rest of the problems. :)

Nice day to all.

---

### Post by self-defence on 2007-08-27
Ok, I just found a problem. Now because I forced the package to install I keep getting error messages about broken packages. Is there any way to make synaptic ignore these package and treate it as not broken?

Thanks for the help.

---

### Post by cyberdork33 on 2007-08-28
you need to install the dependencies... The program depends on them.

---

### Post by self-defence on 2007-08-28
The problem is that if I try to install Pommed 1.8 it tells me I need libc6 a newer version that I've got and if I try to install a newer version of libc6 it says that it doesn't need a bunch of packages like gnome and some other that I wouldn't like to lose. That's why I can't install all of the dependencies.
Any suggestions on how to tackle this problem.

Also I've found that if I run a program called Cheese under root the iSight works fine and doesn't crash. But it only works in Cheese and only under root. Any ideas?

Thanks for the help. :)

---

### Post by cyberdork33 on 2007-08-28
> **self-defence said:**
> The problem is that if I try to install Pommed 1.8 it tells me I need libc6 a newer version that I've got and if I try to install a newer version of libc6 it says that it doesn't need a bunch of packages like gnome and some other that I wouldn't like to lose. That's why I can't install all of the dependencies.
Any suggestions on how to tackle this problem.

Also I've found that if I run a program called Cheese under root the iSight works fine and doesn't crash. But it only works in Cheese and only under root. Any ideas?

Thanks for the help. :)
IDK, the newer lib6 is not in the repository yet. You might look on getdeb.net

As for Cheese, what version are you using? Did you compile it?

---

### Post by self-defence on 2007-08-28
Here's what happens if I try to install Pommed 1.8 it tells me that I need a newer version of libasound2 (even though I've got it installed already) and when I try to install libasound2 it tells me I need libc6 and if I try to install it I get a conflict tzdata and it needs to be removed. But if I try to remove it wants to take a long about 8 other packages like gnome-language-pack, etc.
Is there really not any other way to force install Pommed 1.8 so that Synaptic wouldn't have problems with broken links. I mean there's got to be a way becouse Pommed 1.8 works just fine.

Thanks for the help and have a nice day.

---

### Post by cyberdork33 on 2007-08-28
> **self-defence said:**
> Here's what happens if I try to install Pommed 1.8 it tells me that I need a newer version of libasound2 (even though I've got it installed already) and when I try to install libasound2 it tells me I need libc6 and if I try to install it I get a conflict tzdata and it needs to be removed. But if I try to remove it wants to take a long about 8 other packages like gnome-language-pack, etc.
Is there really not any other way to force install Pommed 1.8 so that Synaptic wouldn't have problems with broken links. I mean there's got to be a way becouse Pommed 1.8 works just fine.

Thanks for the help and have a nice day.

I can't really help you anymore on pommed. I haven't used it. 

You didn't answer my question on Cheese...

---

### Post by self-defence on 2007-08-28
O sorry, no I installed it from a deb package. When I run it there is no picture, but if I press the button it actuality takes a picture and saves it. :)

Thanks for the help.

---

### Post by cyberdork33 on 2007-08-28
> **self-defence said:**
> O sorry, no I installed it from a deb package. When I run it there is no picture, but if I press the button it actuality takes a picture and saves it. :)

Thanks for the help.

If it is version 0.21 or 0.22, the developer is aware of the bug. It is fixed in the code repository and a new release is forthcoming. For now, you can stick with 0.20, it works decently.

---

### Post by self-defence on 2007-08-28
O cool, thanks for the info cyberdork33's. The version is 0.22 I'll change it to 0.20.

Thanks :)

---

### Post by self-defence on 2007-09-07
Well I'm having a bit of luck with my mac. I've been able to get the cdrom working by adding piix to /etc/modules. After a reboot it just works. As for pommed it's still marked as broken so anytime I need a new package I remove it and then add it again. Couldn't find a better solution.

Nice day to all.

---

