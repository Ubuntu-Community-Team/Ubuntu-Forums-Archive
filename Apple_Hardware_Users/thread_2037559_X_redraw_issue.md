---
title: "X redraw issue"
date: 2012-08-04
forum: Apple Hardware Users
---

### Post by iamgnat on 2012-08-04
Hello,
I'm getting back to Linux on my desktop (laptop) for the first time  since 2001. I've been testing it out on a work provided Lenovo for the  last couple of weeks and found kubuntu was the best fit for me. So now  I'm ready to commit on my personal laptop and my normal work laptop  (both Macs). This morning I started with my personal laptop.

My personal laptop is a MacBookPro3,1 (64bit/4GB/200GB) and my work  laptop (not the loaner Lenovo) is a MBP6,1 (64bit/8GB/500GB).

The install went fine from a Mac specific 64bit ISO of 12.04 that I  burned on to a CD (the normal ISO just froze after selecting "Start  kubuntu" in a test-only menu (not the blue background menu I get from  the Live CD)). After the install once I've logged in it doesn't appear  that my mouse clicks or typing has any effect. If, however, I force the  screen to redraw by (for example) minimizing a window I can see that  what ever I did indeed had the desired effect.

For example if I have a terminal open I can't see anything I type or the  output from whatever I execute until I minimize and restore the window  (but then it is frozen again until another round of minimizing and  restoring).

I booted my work MBP off the install disk and everything worked fine. I  tried booting my work laptop off my personal laptop's hard drive using  Apple's target disk mode, but GRUB complained about not having a boot  device (I assumed this had to do with my partitioning, but after  reinstalling (see below) that feature I love most about Macs still  doesn't work). Next I booted my personal laptop off the live CD and  everything worked just fine, so assuming that maybe my overly  complicated partitioning had something to do with it I reinstalled  Kubuntu and let it do it's recommended single partition install. After  rebooting onto the fresh install it had the same input issue.

Since the laptop does use a Nvidia card and I've read a bit about issues  there I did try installing the nvidia-current package but it didn't  seem to have any effect.

This issue occurs with the built in track pad and keyboard as well as with external devices.

I haven't been able to really test it (since doing anything is a real  PITA like this) but I've noticed that the desktops widget seems to be  saying that what ever is on my current desktop is also on the second  desktop as well. Booting off the Live CD on either laptop does not show  that same behavior.

Does anyone have any idea what is going on and how I can fix it?

I wouldn't apply for a job as a Sys Admin, but I've been using Linux and  UNIX environments since the mid-90s so you hopefully shouldn't have to  speak too slowly at me as I am comfortable on the command line.

Thanks,
-dave

---

### Post by 2blue on 2012-08-04
I have no idea how to go about it, but like you mention it sounds like a graphics card or GUI related issue. You somehow have managed to install nvida driver package in a difficult situation, and no change? 

Have you tried something very simple like "sudo apt-get updates" and a reboot? It must be challenge to know when to type password and if you are asked to type "Y" for yes, and stuff like tab-key when asked to accept restricted stuff; which might be an issue with some nvida-drivers.

Weird errors have occurred sometimes if I have not remembered to burn CD on lowest speed, or forgotten to do a md5 filesum-check on the iso-download.  But if it boots and run fine as live CD, I`m not sure if these concerns are applicable. There used to be a CD health check function, but I`m not sure it is there anymore. 

The experts will hopefully get on your case soon. 

Regards

---

### Post by iamgnat on 2012-08-04
> **2blue said:**
> I have no idea how to go about it, but like you mention it sounds like a graphics card or GUI related issue. You somehow have managed to install nvida driver package in a difficult situation, and no change?

Have you tried something very simple like "sudo apt-get updates" and a reboot? It must be challenge to know when to type password and if you are asked to type "Y" for yes, and stuff like tab-key when asked to accept restricted stuff; which might be an issue with some nvida-drivers.
Yes I did and no there was no change.

Yes it is a pain, but knowing how sudo and apt-get work help to get ahead of it, but lots of minimizing and restoring the terminal window is involved.

On a whim I just installed ubuntu-desktop (talk about a lot of minimizing/restoring!), switched to lightdm, and tried Unity and it worked fine. I switched back to KDE (still with lightdm) and it went back to being problematic.

So I'm pretty sure this is a KDE issue now, but as the Live CD works I'm assuming it's a config issue.

Does anyone know what might be different about the KDE configuration on the Live CD vs what it installs? Alternatively can someone tell me how to mount the internal HDD when I boot from the the Live CD so I can troll the directory structure for differences?

Thanks,
-dave

---

### Post by iamgnat on 2012-08-04
Got an answer from another forum (and now that I know it's a KDE problem it was also a bit easier to Google for info on what seems to be a common-ish issue). Apparently it is an issue with the Desktop Effects and turning them off takes care of the issue.

---

