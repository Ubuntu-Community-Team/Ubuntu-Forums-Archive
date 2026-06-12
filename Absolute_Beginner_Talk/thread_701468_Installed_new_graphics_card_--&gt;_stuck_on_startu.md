---
title: "Installed new graphics card --&gt; stuck on startup"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Jessica Lynn on 2008-02-19
A little background:
I'm definitely a noob when it comes to ubuntu.  I bought an eeepc, put on xubuntu, loved ubuntu, needed more, and then installed dual boot xp/ubuntu 7.10 on home desktop :)

Everything installed perfectly on my home desktop but when I went to put on Compiz I had graphics problems.  I looked into the problems and realized that my graphics driver was not compatable with compiz... so i went out and bought a new graphics card.  It had to be a PCI slot card b/c...well... it's my first non-hand put together desktop computer.  The graphics card was part of the motherboard (gateway).  

Probem:  
After physically putting in the new graphics card and trying to boot to ubuntu I get nowhere.  I'm stuck on the 3d notch of the pretty little orange progress bar to getting into Ubuntu. :(

I miss being able to boot into ubuntu!  I'm really starting to get tired of windows :(

The graphics card I installed was an ATI card, I believe.  I checked out its compatability (with compiz at least) before installing it.  Everything was compatable.  I'm currently very far away from my desktop computer so if the name of the graphics card is important to fixing this problem i'll be able to get it to you tonight :)

I just don't kow what to do. If I have to reinstall or do a fix with Ubuntu that's find but I'd rather not :)

---

### Post by paultag on 2008-02-19
I have not used ATI for a while now, so if anyone can give advice about AIGLX (I think...) it would be awsome.

As for the rest of it, check to see where it is hanging up. on boot press Ctrl+Alt+F1, and watch the text. If you could tell us at what point it hangs, and what it says, it would help a lot.

Cheers,
Tag

---

### Post by dstew on 2008-02-19
If you install a new card, at some point you will have to reconfigure your Xserver software to use the new card. If you can get to a command line, enter```
sudo apt-get reconfigure xserver-xorg
```Answer the questions the best you can (there are good explanations) and after you get back to the command line enter```
startx
```Once you have a functional interface, you may need to install a restricted driver. Check in the Restricted Drivers Manager tool in the System --> Administration menu.

---

### Post by Jessica Lynn on 2008-02-19
Thank you so much for the responses :)

I checked the graphics card and it's different than what I thought.  It's a NVIDIA GeForce FX 5500.

When I tried to get back into Ubuntu, and trying to get to the non-graphics side, (ctrl_alt+f1, 2, 3...etc) nothing happened.  I stayed at the loadup screen :(  Am I doing it wrong? When I do that with the eeepc it switches over just fine.  

I restarted and instad of just choosing 7.10 I went to the recovery mode... lots of things scrolled on the screen but the line it stuck on was:
[ 35.956243]EIP:[<c011e466>] native_apic_write_atomic+0x6/0x10 35:ESP 0068:f7f1ff54

---

### Post by paultag on 2008-02-19
> **Jessica Lynn said:**
> 
When I tried to get back into Ubuntu, and trying to get to the non-graphics side, (ctrl_alt+f1, 2, 3...etc) nothing happened.


does this mean that it stays at the screen with a big graphical Ubuntu and logo, or a black screen? If you use Ctrl+Alt+F1, and its blank switch to Ctrl+Alt+F8 After. There should be at least a little text saying kernel loaded, or kernel is missing / corrupt / broken

> **Jessica Lynn said:**
> 
  I stayed at the loadup screen :(  Am I doing it wrong? When I do that with the eeepc it switches over just fine.  

I restarted and instad of just choosing 7.10 I went to the recovery mode... lots of things scrolled on the screen but the line it stuck on was:


**[ 35.956243]EIP:[<c011e466>] native_apic_write_atomic+0x6/0x10 35:ESP 0068:f7f1ff54**

This is our issue I think.

See a related post with the same issue here:
[http://ubuntuforums.org/archive/index.php/t-427834.html](http://ubuntuforums.org/archive/index.php/t-427834.html)

Cheers,
Tag


::EDIT::

There seems to be a few ways to get around this, it looks like an ACPI issue, take a look at that thread
-T

---

### Post by paultag on 2008-02-19
Hey All:

Just got a message from JoshuaRL :

> 
Hey, I have an idea what the problem is:
[http://ubuntuforums.org/showthread.php?t=570098](http://ubuntuforums.org/showthread.php?t=570098)

post #2.

I'm not on my Ubuntu box so I can't get the exact pathname for the blacklist file. So I thought I'd pass it along to you.

She'll probably need to reconfig xorg after blacklisting to get it configured for the PCI slot and nvidia driver.


Awesome advice, Thanks Josh -- worth looking into

Cheers,
Tag

---

### Post by JoshuaRL on 2008-02-19
> **paultag said:**
> Hey All:

Just got a message from JoshuaRL :



Awesome advice, Thanks Josh -- worth looking into

Cheers,
Tag

Heh, I was trying to give you an assist.

But yeah, that may be the issue since Linux doesn't care much about BIOS.

I would try the dpkg-reconfigure xserver-xorg first, but if that doesn't work then that link would be the issue.

If you wanted to double check after doing all that to see if it is set up correctly you could go into /etc/X11/xorg.conf and check to see that the nvidia driver is installed and that the path for the video card is for PCI 0.0.2 (if I remember correctly).

---

### Post by paultag on 2008-02-19
> **JoshuaRL said:**
> Heh, I was trying to give you an assist.

no worries, I don't take credit when I don't deserve it, haha.

---

