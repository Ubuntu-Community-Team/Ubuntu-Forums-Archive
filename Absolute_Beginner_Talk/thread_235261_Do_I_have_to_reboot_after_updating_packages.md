---
title: "Do I have to reboot after updating packages?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by dr_d on 2006-08-12
Just wondering, is a reboot required after installing updates?

Because I've heard a lot of ppl saying that it's not.

And while I'm a big supporter of the "reboots are for hardware changes" attitude, i want to find out the facts.



For example, say I upgrade my compiz and compiz-gnome (new ones are released every day lol)... well would it replace the already running executable? or just put the new one in the folder and a start up script so that the change will be made upon next reboot?

Assuming that is *does* overwrite the already running executable (which in the windows world at least would be considered quite hackish) then it would have to also replace what's running in memory. And unless we're talking overwriting the memory space of another process (which is damn hackish), then I'm assuming we're dealing with a process restart.

But after installing the compiz update, I didn't ever see any visual changes... and xserver wasn't restarted..... so that leads me to suspect a start up script to install the new version....


what's the bottom line... do i need to reboot or not?

cheers!

---

### Post by NetworkGuy on 2006-08-12
My two cents..

I've heard it said that you only need to reboot if you update the kernel.  I usually reboot everytime I retreive updates.  Maybe not immediately, but usually before I go to bed for the night.

Not the definitive answer you are probably looking for, but hopefully helpful.

---

### Post by thunderduck3141 on 2006-08-12
i would do it ASAP, because if you do more installs / compiling some of the updates may not be sensed

---

### Post by bulldog on 2006-08-12
You don't have to reboot after updates.
If compiz has been updated and you wanna be sure it's loaded,simply log out and in.
When you download and install a new kernel you have to reboot to use the new kernel.
You will see a blue sign along your update icon which tells you to reboot.
In other cases it's not a problem when you don't reboot.

---

### Post by dr_d on 2006-08-12
NetworkGuy, yeah this is exactly what i've been doing..

bulldog, oh so you *do* have to log in and log out... hmmm in my mind this is almost the same as rebooting.

I'll probably continue to reboot after updates... Thanks for the info guys.

---

### Post by TFX360 on 2006-08-12
After a XGL/Compiz/Quinn update I somtimes reboot. Mostly because my gnome session manager (sometimes) goes beserk. And Compiz is quite unstable in the resizing when just did other action thing :D. Other than that I only boot after a kernel update. That also means recompiling all stuff you compiled. Be wary of that :D. In my case most importantly recompiling the ATI driver for my X800XT.


Kind regards,


TFX

---

### Post by Anduu on 2006-08-12
Usually if anything that is running is updated a logout/in is required.

Kernel or hardware stuff...reboot.

---

### Post by az on 2006-08-12
The notifier applet will tell you that a reboot is required after you install a new kernel.  It may also do so when udev is updated, but the last time I checked, the only postinstall script that make the notifier tell you to reboot were linux-images.

Those are (in theory) the only packages that will require a reboot, and you will be notified of it.

---

### Post by dr_d on 2006-08-13
well i make a point of only using .debs on my nix partition... one of the things i love about ubuntu is how packages are all managed from one center location.. and i dont want to break this by compiling anything.... if i need to use something that isn't in the repo's i;ll use it on my windows partition.

compare this to windows... each program is phoning home independently of everything else to check for it's own updates... programs are bloated because of all the attempts to protect the code from crackers..

so yeah. no compiling for me :)

---

### Post by bonzodog on 2006-08-13
when doing any updates to the graphical front end, you will only need to restart X. This can be done with ctrl-alt-bkspc.

You should only need to reboot for sysvinit, kernel, or udev updates.

---

