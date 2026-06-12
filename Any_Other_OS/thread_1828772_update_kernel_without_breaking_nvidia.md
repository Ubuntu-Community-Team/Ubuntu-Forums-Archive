---
title: "update kernel without breaking nvidia?"
date: 2011-08-19
forum: Any Other OS
---

### Post by Duncan Williams on 2011-08-19
Last time I did a kernel update (2.6.38-10-generic)

It broke my nvidia drivers and I ended up having to re-install my operating system and all the hassles of re-updating and re-customising. I have backed up all packages, etc. but don't want it to happen again.

In my present updates there is a number of installs for:
Version 2.6.38.11.26: 

I have a few ideas as to how to do this update without breaking video drivers. BUT.

[B]>  Has anyone done the update with nvidia (current-280)?
>  did it break your drivers?
>  What is the best way to update the kernel without this problem?
[/B]

I am using `Peppermint' which is based on ubuntu 11.04 
(with LXDE and a bit of Mint)

---

### Post by Frogs Hair on 2011-08-19
The PPA at the link will keep your driver up to date . Back when I started with Wubi 9.10 I had to remove the Nvidia current driver , Update the kernel and reinstall the driver or face a black screen . That issue is supposed to have been fixed . I know your not using Wubi but it may be a work around . It is much easier to reinstall Nvidia current than the driver from the website , but the PPA may make that easier. [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by Duncan Williams on 2011-08-19
@Frogs Hair,  thanks for your post.
I am using the X Swat ppa and thats how I installed the 280 driver.

This was one idea I had 
> to uninstall nvidia, fall back to nouveau, install updated kernel, reboot, re-install nvidia current 280 from X Swat ppa.

So you are saying that this will work and I should have no problems doing it this way?

again thanks for your response.

---

### Post by Frogs Hair on 2011-08-19
> **Duncan Williams said:**
> @Frogs Hair,  thanks for your post.
I am using the X Swat ppa and thats how I installed the 280 driver.

This was one idea I had 
> to uninstall nvidia, fall back to nouveau, install updated kernel, reboot, re-install nvidia current 280 from X Swat ppa.

So you are saying that this will work and I should have no problems doing it this way?

again thanks for your response.

All I can add is that this saved me from reinstalling Ubuntu every time I had a kernel update , that got old after two updates .

---

### Post by Perfect Storm on 2011-08-19
Moved to Other OS/Distro Talk.

---

### Post by Duncan Williams on 2011-08-20
Don't really understand the move as this distro is based on natty 11.04.
As far as I know my problem is the same in straight ubuntu 11.04

If it isn't , then I should be ok to update without broken video drivers.
I have raised this issue in `peppermint forums' and the reason I raised it here was to get more info and find out what others were doing.
This thread will probably get buried now.

Anyway I seem to have got one confirmation and that will have to do me.

I will leave the kernel update until, I feel upto the possibility of doing a complete install again.

I was under the impression that it was a security update, but so be it.

---

### Post by drawkcab on 2011-08-20
Not to hijack but I have recently noticed a correlation between kernel updates and the annoying video tearing/artifacting that everyone's always complaining about on their nvidia machines.

If I reinstall ubuntu from scratch, update and then install my drivers -->  no tearing.  Once I run a kernel update--> tearing.

These phenomenon have to be related methinks.

---

### Post by Duncan Williams on 2011-08-21
You may well be right there, I have a fairly old, underpowered machine but no tearing or other video problems since I changed the graphic card and sorted my drivers, window manager and other stuff out.

This is why I am worried about the kernel update!
(as in breaking or affecting my video drivers)

I have decided to give it a miss and when I am in the mood jump straight to developers kernel (currently 3.03 I think)

Then I won't need kernel updates for ages, and if it falls, will drop back.

To much painstaking customising on this system to blow it out the window at present.

---

