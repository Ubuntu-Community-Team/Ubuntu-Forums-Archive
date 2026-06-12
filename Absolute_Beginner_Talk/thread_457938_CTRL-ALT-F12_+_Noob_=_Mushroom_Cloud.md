---
title: "CTRL-ALT-F12 + Noob = Mushroom Cloud"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-05-29
Quick post, details later tonight when I have more time:

I hit CTRL ALT F12 and ended up with a blank screen, no prompt.  I hit CTRL ALT F2, logged in as my user and did a sudo reboot.  Now X won't start.

I get an error saying the nVidia drivers have the wrong version or something like that, and that "no screens are configured".  I'll get the exact error posted later tonight.

I've renamed xorg.conf.backup to xorg.conf with no luck.  That was the only thing I could think of.

Note:  The nVidia drivers I am using are the ones from Bayrl. (or however it's spelled)

I'll check back in on this thread in about 16 hours.  

Thanks!

-Doc

---

### Post by EdThaSlayer on 2007-05-29
Try using "sudo dpkg-reconfigure xserver-xorg". Paste that command in your terminal(or the bash log in screen for you) on the affected computer. :)

---

### Post by apjone on 2007-05-29
Try installing envy. I use it to install my nvidia drivers and it configures Xorg for you. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . 

Its more likely that a update skewed your xorg not ctrl-alt-f12 .

---

### Post by Cicatrix on 2007-05-29
This might be because your kernel has been updated, but you haven't reinstalled your Nvidia drivers (if you installed them manually from a file). Anyway, a quick fix that would allow you to enter X again, is either to edit the xorg.conf file and change the "driver "nvidia"" section to "driver "nv"", or, to reconfigure X with the package script "sudo dpkg-reconfigure xserver-xorg".

---

### Post by steve.horsley on 2007-05-29
I agree with cicatrix. All the Ctrl-Alt-Fx does is switch between virtual terminals. F1-F6 are text terminals, and F7 is the GUI. F8-F12 are normally blank. So the Ctrl-Alt-F12 was not the cause of your problem. There was however an update to the kernel for Feisty released yesterday, and if you're not using the nVidia drivers that come from the Feisty repos, you will have to recompile your drivers for the new kernel. Changing from nvidia back to the nv driver will at least get X going again until you can reinstall the nVidia drivers.

---

### Post by Doc.Caliban on 2007-05-29
Wow, thanks everyone... I agree that it was the update.

Will sudo dpkg-reconfigure xserver-xorg help in this case?

If not, do I have to install special nVidia drivers from the Beyrl project?  (I seem to remember having to do that to get all of the stuff to work right.)

Thanks again!

-Doc

---

### Post by Tux Aubrey on 2007-05-29
Yeah, your Ctrl-Alt-F12 experience was equivalent to entering the Linux Matrix without Lawrence Fishburn.  You can always get back to Kansas with Ctrl-Alt-F7

 
I had the nVidia driver problem after the kernel upgrade.  Apparently I originally installed the drivers the WRONG WAY and was being punished for not having the restricted modules correctly installed.  If yours is the same, try this command after logging in to terminal mode:


```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```


It worked for me and comes from the head of TSEliot hizelf..

---

### Post by Doc.Caliban on 2007-05-29
> **Tux Aubrey said:**
> Yeah, your Ctrl-Alt-F12 experience was equivalent to entering the Linux Matrix without Lawrence Fishburn.  You can always get back to Kansas with Ctrl-Alt-F7

 
I had the nVidia driver problem after the kernel upgrade.  Apparently I originally installed the drivers the WRONG WAY and was being punished for not having the restricted modules correctly installed.  If yours is the same, try this command after logging in to terminal mode:


```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```


It worked for me and comes from the head of TSEliot hizelf..



Are you running Beyrl?

---

### Post by Doc.Caliban on 2007-05-29
sudo dpkg-reconfigure xserver-xorg did not help.  Either it was not going to fix it at all, or I didn't answer all the questions correctly.  I find it odd that Ubuntu can install and figure all of that out for itself, but there's no automated reconfiguration utility...?

So I'm still not sure what to do...  is it an issue with restricted driver installation methods, or just a driver issue in general?

I'll check back tomorrow evening.  Thanks for the ideas!

-Doc

---

### Post by Cicatrix on 2007-05-30
"sudo dpkg-reconfigure -phigh xserver-xorg" should do the trick, just note in the first screen to select the driver "nv" instead of "nvidia", and if "nv" doesn't work, then try "vesa". All the other questions should be easy to answer. Or, you can manually edit your xorg.conf file, by typing "sudo nano /etc/X11/xorg.conf", in this file, scroll down to the section entitled "device", there you should find a line called driver. Change this from nvidia (presumably) to either nv, or failing that, vesa. Then press ctrl+o to save it, ctrl+x to exit nano, and then either type "startx" or "sudo /etc/init.d/gdm restart" to start x. This method should get you back into a working X, but you won't have 3d acceleration, but once in X, you should have an easier job recovering.

Or, a alternative method, to see if it is the kernel update that caused this:
While your computer is booting up, in the GRUB menu (the place where you can choose Windows or Ubuntu) choose the line with the version 2.6.20-15 instead of 2.6.20-16. If this works, then you know it was the kernel update that broke it.

---

### Post by Doc.Caliban on 2007-05-30
> **Cicatrix said:**
> Or, a alternative method, to see if it is the kernel update that caused this:
While your computer is booting up, in the GRUB menu (the place where you can choose Windows or Ubuntu) choose the line with the version 2.6.20-15 instead of 2.6.20-16. If this works, then you know it was the kernel update that broke it.

Bingo.  I'm in.

So, it's the kernel update.  Now that we know that for sure, what is the best course of action to get me up and running with 2.6.20-16 and Beryl?  I think I remember having to install drivers sourced from the Beryl project to get everything working...

**I really appreciate all of this help, from everyone.  I worked at MS for almost 10 years and I know Windows inside and out, but this is all new to me and it's frustrating and fun at the same time.  This kind of community help really makes it a lot easier to learn.  Thanks!**

-Doc

---

### Post by steve.horsley on 2007-05-30
Your drivers will not work without being recompiled for the new kernel. If you installed a binary, you need a replacement. If you compiled as part of the installation process, you can just recompile.

I have beryl working with the drivers from the Ubuntu distro - package nvidia-glx-new. I would suggest you ditch the funny drivers and install the official repo ones.

---

### Post by Doc.Caliban on 2007-05-30
All done.

I installed the latest beta drivers from nVidia and I'm up and running just fine again.  Sorry to cause such a big thread over nothing more than a kernel update and my lack of knowledge!

Thanks again,

-Doc

---

### Post by steve.horsley on 2007-05-31
Don't let it worry you. If you're asking the question, there are probably many more people looking for the answer to the same question, and they'll find it here. I have learned loads here, but asked very few questions myself.

---

