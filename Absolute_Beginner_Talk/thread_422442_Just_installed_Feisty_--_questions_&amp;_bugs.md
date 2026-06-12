---
title: "Just installed Feisty -- questions &amp; bugs"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Znupi on 2007-04-25
I can say that my Ubuntu 7.04 installation went as smoothly as possible -- I'm amazed!
Although, as any new user, I have some questions:
1. Is there any way to write to a NTFS partition? It's awesome you can read from one but it would be even better if you could write to it!
2. I have that "Restricted Drivers" icon under "Administration" which says something about an ATI accelerated graphics driver.... should I install that? What would happen if I would?...

I have enabled the Desktop Effects and they are just awesome! One question though: I saw that on other systems with such visual effects, the opacity of windows can be changed by clicking on the window's caption and scrolling? Can I somehow enable that in my Ubuntu, or is it not available yet?

Some bugs I noticed using the Desktop Effects:
1. If I dare go in to "Preferences" in the workspaces menu -- to change workspaces number -- it resets to 1 and the only way to change it is by deactivating 'workspaces on a cube', setting the number of workspaces to whatever I need, and activating the option again.
2. Screensavers lock up, they animate for 10-15 seconds and then they simply stop.
3. Some windows -- when maximized, their contents don't maximize and the whole window locks up, and I have to restore/maximize multiple times... -- the window that does this the most is Firefox...

---

### Post by aberry5555 on 2007-04-25
For the first set of questions:

1. Yes, there is but you'll have to install a program called NTFS-3G and change your /etc/fstab file to suit it.
2. Yes, you can do that, what it would mean is that you would be able to use 3D much better than on the standard drivers. It does, however, require a bit of setting up first (and you also have to double check you're on ATI). By the sounds of it some of the problems you're having are somethign to do with your graphics drivers, though I wouldn't install it from synaptic as this doesn't always work out.

If you want to install the drivers try this page: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This might, hopefully, fix the problems you are having with the x-server.

---

### Post by mahiyar on 2007-04-25
Welcome to Ubuntu
 
1.For enabling read write capabilities read/follow this [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
 
2.ATI restricted drivers give you 3d graphic capabilities and the works, and is enabled at the tick of a button. If you have a good (recent) ATI card by all means enable it.
 
By enabling it your desktop effects experience should improve drastically (I'am surprised that desktop effects got enabled without first implementing the restricted drivers)

---

### Post by xopher on 2007-04-25
2. If you enable the restricted ATI drivers (fglrx), you will have to set up XGL for getting 'desktop effects' working. So I'd think it over. With the open-source drivers you can use AIGLX, which is a much better choice.

---

### Post by Znupi on 2007-04-25
Funny thing is, I'm not sure about what video card I have...
Most probably it's an Asus Radeon X550 w/ 512MBs. The thing that confuses me is that on Windows, I had to install the ATI drivers for it to work (ATI Catalyst).
So, should I try to install the restricted drivers? :-/

**EDIT:** I was able to install ntfs-3g -- as usual, it was extremely easy! Thanks a lot for the help :).

---

### Post by phelixnyc on 2007-04-25
You could always use automatix  to mount NTFS drives and it allows you to write and read the drive.

---

### Post by Znupi on 2007-04-25
> **phelixnyc said:**
> You could always use automatix  to mount NTFS drives and it allows you to write and read the drive.
I don't need to, I installed ntfs-3g and it works perfect.

So, should I install the driver? :-s, I don't want to mess things up and make Ubuntu stop working...
Also -- is the opacity thing possible? :D

---

### Post by compmodder26 on 2007-04-25
Let me ask this.  Is your desktop sluggish since you've enabled desktop effects?  If it isn't then I'd say that the open source drivers are working properly and you already have 3D enabled.  So, no need to install any more drivers.

---

### Post by Znupi on 2007-04-25
> **compmodder26 said:**
> Let me ask this.  Is your desktop sluggish since you've enabled desktop effects?  If it isn't then I'd say that the open source drivers are working properly and you already have 3D enabled.  So, no need to install any more drivers.
Yes, it is a bit sluggish (a really tiny bit -- i expected it to be a LOT more sluggish with the effects enabled, but I guess I just have to accommodate with the idea that Linux is not Windows :))... And no, I don't have the restricted drivers activated.

---

### Post by aberry5555 on 2007-04-26
If it's based on an ATI card then it should work with the ATI drivers, you could always try them and see what happens and, if they don't work properly, you can disable them again afterwards. If you need to get them working try using the script I posted earlier as, with experience from earlier distros (and seemingly with this one from other posts I've read) the repositories don't install the fglrx drivers properly.

---

### Post by Znupi on 2007-04-26
I Installed the drivers and everything seems to be working fine, but... The Desktop Effects don't work :(.
When I go to System -> Preferences -> Desktop Effects, I get an error saying "The Composite extension is not available" :( what should I do? I really like the effects... should I uninstall the driver?

---

### Post by Znupi on 2007-05-02
I uninstalled the driver, the effects are working more or less fine... But what should I do? They have some small glitches, is there any way to get them working with the drivers installed, too?

---

