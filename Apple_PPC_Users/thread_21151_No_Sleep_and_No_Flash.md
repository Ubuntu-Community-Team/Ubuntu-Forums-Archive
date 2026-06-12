---
title: "No Sleep and No Flash"
date: 2005-03-20
forum: Apple PPC Users
---

### Post by areitze on 2005-03-20
hi Guys,

i posted on Friday this samequestion but it seems that with the change in the this forum site, my post was lost...  :-(

Well  anyways, i have ubuntu Hoary installed and running very well I might Add (incredible how much more efficient and faster my iBook has become now), but i can't make it sleep, and I don't have flash capapilities on firefox...  I've installed these alternative plug ins that were recomended to me...  they where installed by Syntaptic, but still doesn't work, I doo feel that it's trying to read them, but can't play them...  Now this is very disturbing since almost all web sites are with flash, and a few are only flash so this is troublesome...

For the sleep issue, it does go to sleep, but it doesn't wake up, it freezes right away...  I've heard of this HAL app, but i don't have a clue what it is..  I really don't  know how to use it nor install it if it's not through synaptic or APT-GET for that matter.

Well thx again for any help you guys can give me here...

All the best,
Andrés.-

---

### Post by callipeo on 2005-03-21
[ I assume you are using an iBook G4]

[Sleep]
The biggest issue seems to be related to the graphic card. You can try to do "sudo dpkg-reconfigure xserver-xorg" and disable the loading of the "dri" module; then reboot (or restart gdm), and the sleep should work.

[Flash]
Bad news: if you have installed the libflash-* packages, there is nothing more you can do. Macromedia doesn't release its plugin for the powerpc architecture. Maybe you can go to "about:plugins" in firefox and check if the plugins are actually loaded.

---

### Post by DJ_Max on 2005-03-21
Actually, they do release binaries for the Mac OS on powerpc, but not for Unix/Linux powerpc. I use the swf-player from the ubuntu repositories, and it works OK, but not perfect.

---

### Post by Pineault on 2005-03-21
[QUOTE=callipeo][ I assume you are using an iBook G4]

[Sleep]
The biggest issue seems to be related to the graphic card. You can try to do "sudo dpkg-reconfigure xserver-xorg" and disable the loading of the "dri" module; then reboot (or restart gdm), and the sleep should work.

Callipeo, I've been trying to get sleep going on a G4 Ibook (1gig) and it just doesn't work, seeing it works on yours I want to go through the config and see what I'm doing wrong.
I've got the machine running on Hoary with latest kernel image (2.6.10?), haven't gotten around to compiling my own kernel yet.  I have disabled DRI as indicated above.
When I close the lid (after unplugging all USB devices), my screen goes blank and the machine goes to sleep, when I open the lid two bad things happen, either USB doesn't work anymore, or worse, and this happens most frequently, my screen never comes on again, I hear the hard disk waking up , but have to stumble through a reboot...
Have you played with _powerprefs_... I have, used it to activate sleep and also to time screen blanking, have turned all these options off but still get the blank screen or USB problem...

---

### Post by Knome_fan on 2005-03-22
1. Here's your friday post:
[http://ubuntuforums.org/showthread.php?t=20803&highlight=sleep+ibook](http://ubuntuforums.org/showthread.php?t=20803&highlight=sleep+ibook)
(The search button really helps. ;-D)

2. About the sleep issue:
You don't have to install HAL, it is already installed and it is the program causing the problem. In short, HAL is one of the programs that Gnome needs to be able to automatically mount CD drives, etc.

The problem is that HAL somehow prevents G3 ibooks from waking up after the have been suspended. Now the workaround for this problem is to stop HAL when the ibook is suspended and restart is after it woke up again.

The script in the bug report I linked does just that.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39)

Now to get it working do the following:
1. Copy and past the script from your webbrowser into a text editor. The script is the part starting with #!/bin/sh and ending with esac.
Now save the script as hal.

2. Now you want to tell ubuntu to use this script when suspending and waking up. To do that copy the script to /etc/power/scripts.d/ 
You'll have to be root to do that, so in the directory where you save the script type:
sudo cp hal /etc/power/scripts.d/

Now you'll have to make the script executable, that is, allow linux to execute it as a program, otherwise it would just be a text file.
sudo chmod +x /etc/power/scripts.d/hal

All you have to do now is to tell your ubuntu to actually use the script in the case an event occurs, that is you suspend your ibook or wake it up. To do this you have to link the script from /etc/power/scripts.d/hal to /etc/power/event.d/hal.
sudo ln -s /etc/power/scripts.d/hal /etc/power/event.d/hal

That should be it.

Hope this helps.

---

### Post by callipeo on 2005-03-22
[QUOTE=Pineault]I've got the machine running on Hoary with latest kernel image (2.6.10?), haven't gotten around to compiling my own kernel yet.  I have disabled DRI as indicated above.[/QUOTE]

Ok, I use the "standard" 2.6.10-5-powerpc kernel image.

> When I close the lid (after unplugging all USB devices), my screen goes blank and the machine goes to sleep, when I open the lid two bad things happen, either USB doesn't work anymore, or worse, and this happens most frequently, my screen never comes on again, I hear the hard disk waking up , but have to stumble through a reboot...

For the USB problem, maybe you should follow the instructions at [https://bugzilla.ubuntu.com/show_bug.cgi?id=7619](https://bugzilla.ubuntu.com/show_bug.cgi?id=7619)

For the screen problem, I must admit I have no clue of what your problem could be. Do you use the kernel framebuffer device interface (if I remember correctly it is "Option UseFBDev" or something like that in xorg.conf)? If so you can turn it off, but I don't really know if doing that will actually help you.

I've not a particularly customized powermanagment setup, except for the usb workaround suggested above.

---

### Post by Pineault on 2005-03-22
[QUOTE=callipeo]Ok, I use the "standard" 2.6.10-5-powerpc kernel image.


For the screen problem, I must admit I have no clue of what your problem could be. Do you use the kernel framebuffer device interface (if I remember correctly it is "Option UseFBDev" or something like that in xorg.conf)? If so you can turn it off, but I don't really know if doing that will actually help you.


Well disabling framebuffer didn't work, going towards a debian kernel, 2.6.11 that I will compile myself, seems only solution

---

### Post by callipeo on 2005-03-22
[QUOTE=Pineault]Well disabling framebuffer didn't work, going towards a debian kernel, 2.6.11 that I will compile myself, seems only solution[/QUOTE]

Then maybe you will have luck with the latest kernel image, built against linux-source 2.6.10-29. Quoting from the changelog:

* Add suspend support for uninorth agp on ppc:
    - Add patch uninorth-agp-ppc-suspend.dpatch.

---

### Post by areitze on 2005-03-23
> **Knome_fan]1. Here's your friday post:
[http://ubuntuforums.org/showthread.php?t=20803&highlight=sleep+ibook](http://ubuntuforums.org/showthread.php?t=20803&highlight=sleep+ibook)
(The search button really helps.  said:**
> https://bugzilla.ubuntu.com/show_bug.cgi?id=1940#c39[/url]

Now to get it working do the following:
1. Copy and past the script from your webbrowser into a text editor. The script is the part starting with #!/bin/sh and ending with esac.
Now save the script as hal.

2. Now you want to tell ubuntu to use this script when suspending and waking up. To do that copy the script to /etc/power/scripts.d/ 
You'll have to be root to do that, so in the directory where you save the script type:
sudo cp hal /etc/power/scripts.d/

Now you'll have to make the script executable, that is, allow linux to execute it as a program, otherwise it would just be a text file.
sudo chmod +x /etc/power/scripts.d/hal

All you have to do now is to tell your ubuntu to actually use the script in the case an event occurs, that is you suspend your ibook or wake it up. To do this you have to link the script from /etc/power/scripts.d/hal to /etc/power/event.d/hal.
sudo ln -s /etc/power/scripts.d/hal /etc/power/event.d/hal

That should be it.

Hope this helps.




Now this should be posted as a FAQ...  IT WORKS!!!!!!!!!!!!!!!!   thx so much, I basically understand what I did, but I would have never been able to do it since I have no clue under those text modes...  I copied all the comands you gave me and it definitly works....  

I'm so happy, my use of sleep under os X was intense, I use it all the time...  You have no idea of how much you have helped me...!!!!

Now I need to get Flash working...  ;-)

Andrés.-

---

### Post by prio on 2005-04-04
Hi,
Im at work at the moment so can't test this till tonight but I am just wondering will this work with a powerbook g4?

---

### Post by poofyhairguy on 2005-04-04
[QUOTE=areitze]
Now I need to get Flash working...  ;-)
[/QUOTE]

I'll tell you right now what you have to do. Use MOL to run OSX or OS9 inside of Ubuntu for sites you need. Thats how you get flash to work.

[http://www.maconlinux.org/](http://www.maconlinux.org/)

For me, I said fuke it. I use this plugin:

[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

To block flash stuff in Firefox (I can click to play them with free pluggins). To me its seems that 90% of the time flash is used for advertisments.

---

### Post by luna6 on 2005-04-07
I am guessing the answer is no, but have to ask anyways..if I install mac on linux on my powerbook g4 with hoary....would the MOL (os X) be able to use the wireless airport chip and I would be able to access wifi spots inside MOL, running in hoary?

---

### Post by prio on 2005-04-07
You guessed right I'm afraid.

---

