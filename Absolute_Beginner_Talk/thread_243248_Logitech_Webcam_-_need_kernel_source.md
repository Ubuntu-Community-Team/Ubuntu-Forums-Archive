---
title: "Logitech Webcam - need kernel source"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by docshawnc on 2006-08-24
I'm new (very) and this is my first post.  I had (past-tense) my logitech webcam working under 6.06 prior to the recent x-server debacle and a resultant complete re-install (I thought I broke it).  Now, after trying to re-install the logitech orbit webcam (using the PWC driver via Synaptic Pkg mgr) it's not finding the device at /dev/video0.  The links I've found suggest grabbing the current driver and doing things from the command line.  Here-in lies my problem - this method requires that you have the kernel source available - which I apparently do not.  It's got to be a no-brainer but I'm at a loss.
    So......just how would I go about doing this?  Here is the link to the method [http://www.saillard.org/linux/pwc/INSTALL.en](http://www.saillard.org/linux/pwc/INSTALL.en)
    Any help with getting this beast running again would be greatly appreciated - shawn

---

### Post by Iarwain ben-adar on 2006-08-24
Hi,
welcome to the forums :D

For the source,
type the output of this command in your graphical apt-get (Synaptic or Adept)
```
 uname -r
``` and then see if there is a src available for your kernel :D


Iarwain

---

### Post by docshawnc on 2006-08-24
Hi -
It brings back 2.6.15-26-386
as the kernel - my problem is that when I try and do the 'make' for installing the webcam driver, it says the kernel source isn't available.  Do I need to download it? and if so, how do I do that? - your help is greatly appreciated

---

### Post by Iarwain ben-adar on 2006-08-24
Good :)
now try this in your console
```
sudo apt-get install kernel-headers-2.6.15-26-386
```


It could be that i entered the package name incorrectly, but if such is the case, just fire up Synaptic (or Adept) and type this in the "search" field: 2.6.15-26-386

That should show you three packages, and you have to install the "kernel-header" file.


Iarwain

---

### Post by docshawnc on 2006-08-24
Got it!  thank you.  Now to see if the rest of the install goes well (I might be back:)

---

### Post by Iarwain ben-adar on 2006-08-24
Glad you got it :D

Let me know if it goes ;)


Iarwain

---

### Post by docshawnc on 2006-08-24
Just finished the install and it works great!  Just needed the headers - thanks again.

Now if I could just get proftpd configured so that the users/groups would work right, WinXP would be history.

---

### Post by Iarwain ben-adar on 2006-08-24
Glad it works :D

Can i help you with the proftpd thingy? (please know that i don't know much about proftpd, but i'm more than happy to try :D )


Iarwain

---

### Post by docshawnc on 2006-08-25
Well, I've made some progress with proftpd (at least it connects on a non-standard port, and passive works) - still have some reading/playing to do but the offer is much appreciated :cool:

---

