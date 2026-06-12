---
title: "How do I open a file in terminal?"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by zanyjazz on 2009-11-14
In a Ubuntu guide it says "now open your xorg.config then find Section Monitor".
How do I open xorg.conf?

---

### Post by doas777 on 2009-11-14
try opening it with nano:

```
sudo nano /etc/X11/xorg.conf
```

when your ready to close, use ctrl + x, and it will ask you if you want to save, and if you want to overwrite the existing file

---

### Post by zanyjazz on 2009-11-14
I am rapidly coming to the conclusion that I am an idiot! When I open as suggested I get a white window with a blinking prompt. No text to edit.
I am trying to get Ubuntu to run in a larger window than 800x600. It is driving me crazy!

---

### Post by whoop on 2009-11-14
> **zanyjazz said:**
> I am rapidly coming to the conclusion that I am an idiot! When I open as suggested I get a white window with a blinking prompt. No text to edit.
I am trying to get Ubuntu to run in a larger window than 800x600. It is driving me crazy!
It could mean you have no /etc/X11/xorg.conf?
what does
```

ls /etc/X11/xorg.conf

```
return ?

---

### Post by zanyjazz on 2009-11-14
No such file or directory.
As I said I just want to alter the Ubuntu window. I have downloaded an ATI driver file but cannot install it because it puts up a page which is bigger than the 800x600 window placing the proceed button out of reach.
I can't remember anything more frustrating than Ubuntu!

---

### Post by whoop on 2009-11-14
> **zanyjazz said:**
> No such file or directory.
As I said I just want to alter the Ubuntu window. I have downloaded an ATI driver file but cannot install it because it puts up a page which is bigger than the 800x600 window placing the proceed button out of reach.
I can't remember anything more frustrating than Ubuntu!

Press "Alt" while clicking anywhere in the window, then drag keeping Alt pressed (until you can click the desired button). The window should move...

---

### Post by doas777 on 2009-11-14
on the xorg command, are you sure you're capitalizing the X in 'X11'?

in terms of your resolution, what window is it that is too big for your screen? the restricted drivers manager?

---

### Post by zanyjazz on 2009-11-14
Managed to go through the install procedure, many thanks, but when I try to complete installation as instructed I get 'No supported adapters detected'. I am rapidly coming to the conclusion that Ubuntu and my iMac are not compatible.
I would welcome any suggestions about how I can resolve the screen size issue.

---

### Post by doas777 on 2009-11-14
well, how are you installing the driver? via the system -> administration -> hardware drivers? or are you downloading a driver from ATI?
what kind of card do you have?

edit: a mac? ewwww. gross.

---

### Post by zanyjazz on 2009-11-14
First, I have a 24" screen 1920x1200. Ubuntu comes up in a 800x600 little box in the middle of the screen. The only option is 640x480. The card is an ATI Radeon HD2600. I have downloaded the driver from the ATI website, and tried to install it as per the attached installation file.
Yes, I am capitalising the X in the xorg command. The Display Preferences says Monitor Unknown and Detect Monitors produces nothing.

---

### Post by doas777 on 2009-11-14
well, the screen res app only works with open drivers. you need to use the ATI CCE thing to configure it, assuming you have already managed to isntall the driver. 

go to system-administration-hardware drivers and see if it has a restricted driver listed for your device.

---

### Post by zanyjazz on 2009-11-14
Hardware drivers searches and says 'No proprietary drivers are in use on this system'.

---

### Post by pelle.k on 2009-11-14
> **doas777 said:**
> what kind of card do you have?

edit: a mac? ewwww. gross.
Was that really necessary?

> **zanyjazz said:**
> Hardware drivers searches and says 'No proprietary drivers are in use on this system'.
Unless i'm mistaken, the screenshot you provided shows you are running ubuntu in **virtualbox**. If so, you're not supposed to install drivers for the hardware you are running on, but for the virtual machine!
That can be achieved by mounting the virtual cd drive with a virtualbox cd image containing drivers for the guest operating system.

---

### Post by zanyjazz on 2009-11-15
Thanks for all the support and attempts to help. I am trying to run ubuntu in a virtual box because I don't want to risk my OSX system which I use for Office 2008, Photoshop CS4, iTunes, Amadeus, etc. I thought ubuntu was supposed to be easy to use, and probably is if only it wasn't locked in a 800x600 box, but until I can get it out of its little box it is too difficult to use. I have switched from 9.10 to 8.04 but the same problem exists. Unless someone can explain in plain English step by step how to resolve the problem, it looks like I shall have to give up on ubuntu. Pity, because I like the look of it.

---

### Post by howefield on 2009-11-15
> **zanyjazz said:**
> I thought ubuntu was supposed to be easy to use, and probably is if only it wasn't locked in a 800x600 box, but until I can get it out of its little box it is too difficult to use.

Everything is easy when you know how, if you are running in a virtual machine, you'll need to add the guest additions, this will sort out your resolution.


Watch the video at virtualbox.org explaining how to do this.

Second video down the page.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by CharlesA on 2009-11-15
> **howefield said:**
> Everything is easy when you know how, if you are running in a virtual machine, you'll need to add the guest additions, this will sort out your resolution.

That'll get you up and running. ;)

---

### Post by zanyjazz on 2009-11-15
Unfortunately the video shows how to change the window size of the virtual box not the window size of ubuntu, so doesn't solve the problem.
"That can be achieved by mounting the virtual cd drive with a virtualbox cd image containing drivers for the guest operating system."
I'm sure it can if only I understood how to do it.

---

### Post by howefield on 2009-11-15
Have you got guest additions installed or not ? 

I hoped that video would give you the general idea, try this tutorial which is more specific to your setup.

[http://apcmag.com/how_to_virtualize_ubuntu_on_mac_os_x.htm?page=5](http://apcmag.com/how_to_virtualize_ubuntu_on_mac_os_x.htm?page=5)

---

### Post by zanyjazz on 2009-11-15
At last! Some progress. Thanks to the last piece of advice I now have a 1152x864 window for ubuntu. Display Prefs: still shows Monitor Unknown, and Hardware Drivers still says no proprietary drivers are in use on this system. Progress is being made however. Many thanks.

---

### Post by howefield on 2009-11-15
> **zanyjazz said:**
> Display Prefs: still shows Monitor Unknown, and Hardware Drivers still says no proprietary drivers are in use on this system.

I think you are a little confused. You won't get proprietary drivers, as you are restricted to the drivers supplied by virtualbox.

Your virtual machine isn't seeing an ATI graphics card, or whatever card it is that you have,  it is seeing what virtualbox tells it to see, if that makes sense.

That's why you got some duff answers early on in the thread, because you were asking a duff question or at least the wrong question. You were on a wild goose chase.

---

### Post by zanyjazz on 2009-11-15
Ubuntu seems to have decided to stop being awkward, I now have a 1920x1200 resolution window. Simply dragged the corner of the widow as far as I could then switched VB to full screen and bingo, Ubuntu is using the whole screen. I am left with at least one problem. How do you get rid of a virtual disc? The waste bin won't accept it and I can't find a delete command.

---

### Post by ikt on 2009-11-15
> **zanyjazz said:**
> 
I can't remember anything more frustrating than Ubuntu!

If you had plain installed it on a computer it would have been

system > admin > hardware drivers > activate.

You would be having the same issues here if you had put os x or windows into virtualbox.

---

### Post by howefield on 2009-11-15
> **zanyjazz said:**
> Ubuntu seems to have decided to stop being awkward, I now have a 1920x1200 resolution window.

Err yes... I'm not so sure it is Ubuntu being awkward, ;)

but glad you are making progress :)

---

### Post by pelle.k on 2009-11-15
> **zanyjazz said:**
> Ubuntu seems to have decided to stop being awkward, I now have a 1920x1200 resolution window.
You should listen to the people in this thread trying to tell you it was never an "ubuntu" problem. It was a virtualbox one.

> **zanyjazz said:**
> Simply dragged the corner of the widow as far as I could then switched VB to full screen and bingo, Ubuntu is using the whole screen.
Yes, that or launching the fullscreen mode of virtualbox does it, but only if you have installed the virtualbox guest additions.

> **zanyjazz said:**
> I am left with at least one problem. How do you get rid of a virtual disc? The waste bin won't accept it and I can't find a delete command.
One can tell you are a hardcore OS X user ;) hehe
In gnome/linux/ubuntu, the trash bin is for throwing stuff away. Not unmounting nor uninstalling, like in OS X. You can right click the disc on the desktop (or in nautilus, the equivalent of finder), and choose unmount, or eject.

---

### Post by zanyjazz on 2009-11-15
Managed to work that last one out for myself.
Thanks for all the help.
Let me add that I have been using a computer for a long time and you do get set in your ways. I got my first PC in 1985 and ran DOS then Windows then OS/2 until the mid 90s when I switched to a Mac, OS7 I believe, now on 10.6.3.
But I like what I have seen of ubuntu, nice and simple apart from the subtle differences. Looks like you have got a convert.

---

### Post by pelle.k on 2009-11-15
> **zanyjazz said:**
> Managed to work that last one out for myself.
Thanks for all the help.
Let me add that I have been using a computer for a long time and you do get set in your ways. I got my first PC in 1985 and ran DOS then Windows then OS/2 until the mid 90s when I switched to a Mac, OS7 I believe, now on 10.6.3.
Glad it's working for you.
I'm a convert myself, but in the other direction. I'm a seasoned linux user, now having bought my first mac (and snow leopard obviously). It's nice to have choice.

> But I like what I have seen of ubuntu, nice and simple apart from the subtle differences. Looks like you have got a convert.
It's a great system. It also has got a learning curve, so if things don't work out the way you want them to, just power down, and retry when you're ready again. BTW, virtualbox is a great way to do it, so you can try it out before installing "for real" (which can be a little bit finicky on macs to be honest).
For inspiration, and a learning experience, i suggest you read some ubuntu blogs and such. Oh, and get used to the concept of installing applications with a package manager! That confuses both windows users and mac users at first. :)
Good luck!

---

