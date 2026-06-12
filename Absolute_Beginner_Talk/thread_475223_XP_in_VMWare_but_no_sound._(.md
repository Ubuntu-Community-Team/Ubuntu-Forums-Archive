---
title: "XP in VMWare but no sound. :("
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by nukkariffic on 2007-06-15
I just got XP running in VMWare, but there is no sound.  I was just wondering if anyone here had any suggestions on how to fix this.

Also, I don't know how to get my graphics card recognized within the VM.  I can't play games, which was my whole reason for doing this. 

Thanks. :)

---

### Post by whistle on 2007-06-15
Which VMWare version are you using? I think some (or all) of them default to not having a sound adapter installed... in the lower right hand corner there should be a speaker icon - is there a red X through it?

And I'm pretty sure VMWare uses its own virtual graphics card, and you can't really play 3D games on it... sorry :(

---

### Post by aktiwers on 2007-06-15
You wont be able to play games in Vmware sadly.. as the virtual video card cant handle 3d acceleration.. 

For the other problem.. did you remember to install Vmware Tools?

From Peturr's guide:
 You will definately want to install the VMWare tools, when windows has been installed. This will **speed up your Windows responsiveness **[LIST]
[*] Make sure your Windows Virtual Machine is Running and visable/selected. (Not in FullScreen)
[*] Go to the VM menu (on the top in the VM Server Console)
[*]Select Install VMWare Tools. 
This will start a installation wizard in your WIndows Environment. Just install the stuff and you will have better mouse and system responsiveness.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

If that doesnt fix your sound problem, in Vmware goto:
Edit Virtual Machine

And make sure your soundcard is enabled.[/LIST]

---

### Post by raja on 2007-06-15
The virtual machine doesnt see 'your' video card, but the video card of the virtual machine - which doesnt give a great performance for 3 D games. 
As for sound, try changing the sound driver - it may work with a different choice.

---

### Post by nukkariffic on 2007-06-15
Gracias, got it fixed. :)

As for the video... that sucks. :P

I guess it's back to flanagling Wine into doing it what I want it to do. :(

---

### Post by the8thstar on 2007-07-29
What soundcard should I put? I'm using HDA Intel.

---

### Post by Kosimo on 2007-07-29
I had some similar problem.
I found the way to enable it.  

You shouldn't be using your soundcard before start the virtual machine. 
Close any music player you may have running.
Close GAIM (or PIDGIN)  /yes...
Then run the virtual machine.
If you installed the drivers and the vmware tools it should work.

---

### Post by the8thstar on 2007-07-29
I tried your idea but I'm still having the problem. 

Anytime I change the sound.dev to anything it brings it right back to "sb16" frustrating!

---

### Post by arethz on 2007-10-27
I always get this problem if I run the Chat messenger and Vmware at the same time... Weird..

---

