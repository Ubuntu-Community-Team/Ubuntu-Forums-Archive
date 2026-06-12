---
title: "Running Ubuntu: Loading Kubuntu?"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-17
*Divulging from [this thread](http://ubuntuforums.org/showthread.php?t=318530).*

I've encountered a weird problem. Well, it's not so much a problem as it is annoying. Whenever I boot up the computer the initial loading screen is no longer the Ubuntu screen; Instead, I get a screen with a blue loading bar and blue text reading "Kubuntu". But the weird part is that I am running Ubuntu Linux (6.10 Edgy to be exact).

This occured directly after running [this command](http://ubuntuforums.org/showpost.php?p=1888563&postcount=10). After running [that command](http://ubuntuforums.org/showpost.php?p=1888563&postcount=10) I restarted my computer to let the update take effect, and that's when I noticed my new Kubuntu loading screen.

Is there any way to remove this screen, or replace it with my previous Ubuntu screen?

*Note: When I log off I see the Ubuntu loading screen still, meaning that I only get the Kubuntu screen when logging on.*

---

### Post by dbbolton on 2006-12-17
hihi, i had the same problem. did you uninstall the kubuntu artwork/splash packages ?

---

### Post by aysiu on 2006-12-17
Try this:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by Pobega on 2006-12-18
Thanks for the page, but it didn't work for me!

When I typed * sudo update-alternatives --config usplash-artwork.so* my terminal just told me:
[i]
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
[/i]

I was messing with Kubuntu desktop yesterday which might be the problem (I've uninstalled it since then), should I reinstall and then try the command again?

**Edit:** I was trying to uninstall Ubuntu-Desktop then reinstall it, but I get some weird errors.

[i]pobega@ubuntu:~$ sudo apt-get remove ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/i]


[i] pobega@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: nautilus-sendto but it is not going to be installed
E: Broken packages
[/i]

---

### Post by samjh on 2006-12-19
I have this exact same problem.

My initial installation was Kubuntu 6.10, and I had just switched to Ubuntu, following the instructions on these two pages:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

During boot-up, it shows the Kubuntu splash screen, but my shut-down splash is Ubuntu.  I am running Ubuntu (ie. Gnome).

**Solution found:**

The problem has been fixed by:

1. Open Synaptic.
2. Find the packages *usplash* and *usplash-theme-ubuntu*.
3. Completely remove the two packages.
4. Reinstall the two packages.
5. Restart computer.

:)

If you still have *ksplash* and its relate packages still installed, they should be remove too, I guess.

---

### Post by Levander on 2006-12-30
I just tried removing usplash and usplash-theme-ubuntu with aptitude.  Apparently, these are depenedencies of ubuntu-desktop, the removal of which isn't a good idea.

I don't use synaptic, but did you tell synaptic to ignore depencies somehow, so it would not touch  ubuntu-desktop, but still uninstall usplash and usplash-theme-ubuntu?

---

### Post by Pobega on 2006-12-30
No, they never installed. But I resolved it by uninstalled kubuntu-desktop and ubuntu-desktop, and then reinstalling.

---

### Post by Levander on 2006-12-30
I just got rid of the kubuntu usplash without having to uninstall and reinstall ubuntu-desktop.  Instructions are here:

[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

I guess the reason that the kubuntu splash screen was still being brought up on boot is because when you install a new usplash, it somehow gets copied from where you install it into all the boot files, messed in there with grub and initramfs.  The 2nd command, that reconfigures linux-image must go back and read which usplash images you have installed,  and copy it back in with the boot files....  So, when you reconfigure with this 2nd command, it overwrites what was copied into the boot files when you installed kubuntu-desktop.

---

### Post by Pobega on 2006-12-30
Well my initial guess as to why was because of ABC Order. Xubuntu never caused any problems, but Kubuntu did. K > U > X. But I guess that was wrong :P

---

