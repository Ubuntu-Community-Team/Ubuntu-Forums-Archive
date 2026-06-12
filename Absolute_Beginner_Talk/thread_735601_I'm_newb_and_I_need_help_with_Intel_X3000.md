---
title: "I'm newb and I need help with Intel X3000"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by mike.pwa on 2008-03-25
Hello,:confused:

I have Intel DG965RY mobo. I would love to enable/install Beryl. 
I cant seem to get it to work. I have no idea about unix.:confused:

So I have installed Ubuntu,
Now I need a guide step by step to install The Drivers for X3000
and then Install Beryl.

Please HELP me. I have order a book about Linux, I really want to learn how it works.
But its coming in two weeks from europe [PL].:mad:

Thank you!!!! :):guitar:

---

### Post by jan quark on 2008-03-25
first post the results of these terminal commands
they will show us your hardware and if the drivers for your graphic card are active

```
lspci
sudo lshw -C display
```

the terminal can be found here
applications > accessories > terminal

after the sudo command you have to enter your login password, it wont be displayed just type it in and hit enter

beryl is outdated
if you have gutsy 7.10 installed then compiz-fusion is installed be default

---

### Post by mike.pwa on 2008-03-25
*-display               
       description: VGA compatible controller
       product: 82G965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga bus_master cap_list
       configuration: latency=0

thanks

---

### Post by northern lights on 2008-03-25
[This]("http://ubuntuforums.org/showthread.php?t=519565") thread might help, gotta do a bit of scrolling though...

---

### Post by mike.pwa on 2008-03-25
Something simplified. Like the exact commands. Most of the stuff there is like a different language to me. :) I'm sorry for being stupid :KS


thanks.

---

### Post by mike.pwa on 2008-03-26
Nobody there? To help me?? :( PLEASE!!!

---

### Post by jan quark on 2008-03-26
ok lets check first if there is the possibility to install the drivers via the restricted drivers manager

go to

system > administration > restricted drivers manager

are there drivers which are not enabled?

if yes install them
if no try to enable the effects by going to 

system > preferences > appearance > visual effects > normal or extra

are you getting an error messages? which one?

---

### Post by iSplicer on 2008-03-26
The process is quite simple, you need to get your GFX card working, then you can enable the effects, which are installed by default. Beryl is outdated, we all now use compiz-fusion. Try installing your drivers by using restricted drivers manager

---

### Post by mike.pwa on 2008-03-27
I'm really sorry for the late response.

I'm really sad :( I'm ssuch a newb :(.

So going back to the topic....

I have tried:
Use Restricted Drivers =
**_Your Hardware does not need any restricted drivers_**
Visual Effects = 
**_Desktop effects could not be enabled_**

How Do I install Compiz??
Do I need the Driver first? Or I install Compiz and the driver comes next?

Thank you ALL For the support!!!

---

### Post by mike.pwa on 2008-03-29
:(

---

### Post by northern lights on 2008-03-31
Haven't browsed this forum for a bit, my bad. Sorry your thread got lost. Anyhow, if you still wanna get this working -

Where are you trying to enable the "Visual Effects"? "System>Preferences>Appearance", "Visual Effects" tab? Is "Desktop effects could not be enabled" the entire error message? What is your current Window manager? Can you post the output of ```
compiz --version
```

---

### Post by mike.pwa on 2008-04-01
```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity 
metacity 2.20.0
Copyright (C) 2001-2007 Havoc Pennington, Red Hat, Inc., and others
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```




Thats the Compiz Version respond. Now about the Visual effects...
I did try but nothing works... I cant even select. I post the error message in older post.


Thans :)

---

### Post by northern lights on 2008-04-03
The visual effects you want to get working are a compiz feature.

Now, as you can read from the output yourself, compiz can't initialize XGL and falls back to "metacity", which is an alternative (the gnome inherent) window/desktop manager.

Thus you're not having a problem with visual effects or the desktop manager, but it's essentially a problem with your graphics card and/or drivers.

What driver do you run? The regular driver for this chipset is open source and called i810.
If I ain't mistaken, it comes with a minimum 256MB graphics memory. That should suffice.

You can read up on it here:
[http://linux.dell.com/wiki/index.php/Tech/Video/Intel]("http://linux.dell.com/wiki/index.php/Tech/Video/Intel")
[http://www.intellinuxgraphics.org/documentation.html]("http://www.intellinuxgraphics.org/documentation.html")

---

### Post by mike.pwa on 2008-04-03
I Give up... It worked for two secodns.. then it froze.. and now I cant select 
visual effects any more.
I dont know whasts happening. Poeple said its a perfect graphic card for compiz
since its intel.. I was happy to build this machine especially for linux.. but now
I feel like im going to throw it out of the window.
I works perfectly on my Dell Laptop 1501..
I have compiz runing, and many more.


I dont really now how to instal drivers from Intel and which one to chose,
I have also found that my Graphic Card is onthe black list in compiz...
I somehow took it out.. then I was able to select visual effects but after I restarted 
nothing works again.. i couldnt move between desktops. So I turn it off.

---

