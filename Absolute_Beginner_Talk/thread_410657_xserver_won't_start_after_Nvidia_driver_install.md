---
title: "xserver won't start after Nvidia driver install"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ffejrey on 2007-04-16
I just installed 7.04 and used the Restricted Driver Manager to update the drivers for my 8800GTS.  When I restart it tells me that the xserver couldn't start.  The error message I got was "no screens found."  I looked in the xorg.conf file and it listed the nvidia drivers.  I tried searching around for an answer but I couldn't find anything that helped.  

Thanks in advance.

---

### Post by Stickymaddness on 2007-04-16
> **ffejrey said:**
>  I looked in the xorg.conf file and it listed the nvidia drivers.  I tried searching around for an answer but I couldn't find anything that helped.  

Thanks in advance.

Are you sure that your xorg.conf is set out correctly?

---

### Post by al1b1 on 2007-04-16
Do you have an intergrated graphic card and has your card worked on other distros?

---

### Post by ffejrey on 2007-04-16
> **Stickymaddness said:**
> Are you sure that your xorg.conf is set out correctly?

Well...no but it is set to Nvidia....

---

### Post by ffejrey on 2007-04-16
> **al1b1 said:**
> Do you have an intergrated graphic card and has your card worked on other distros?

I don't have an integrated graphics card,  7.04 is the only distro that I got to work with my card, probably because none of the others have drivers for it built it.  I am using it now without the official drivers though.

---

### Post by ffejrey on 2007-04-16
Well could someone tell me how to save my xorg.conf file while using commands then?

---

### Post by rsambuca on 2007-04-16
if you type ```
sudo nano /etc/X11/xorg.conf
``` you can edit directly in the terminal.

For now, I would recommend changing the nvidia driver back to nv, and then restarting.

Then you can re-install the nvidia driver (but you may need to install the linux-restricted-modules first through synaptic)

---

### Post by ffejrey on 2007-04-16
Well I've tried installing the driver multiple times through the "Resictred Drivers Manager"...

---

### Post by rsambuca on 2007-04-16
Have you installed the correct version of the linux-restricted-modules for your kernel?  Open up Synaptic Package Manager and search to see what you have installed.

---

### Post by ffejrey on 2007-04-16
I had just used the Update Manager so I should have the latest linux-restricted-module

---

### Post by rsambuca on 2007-04-16
You should have?  Or you do have?  Why don't you check?

---

### Post by ffejrey on 2007-04-16
Does 2.6.20.5-15.20 sound right?

---

### Post by rsambuca on 2007-04-16
That should be the correct one, assuming you have the latest kernel for Feisty.  There have been a lot of problems with Feisty and nvidia kernels as of late.

Try removing the nvidia driver and re-installing.

---

### Post by iamajd on 2007-04-16
> **rsambuca said:**
> There have been a lot of problems with Feisty and nvidia kernels as of late.

Ha!  Thats an understatement!  Since I upgraded to Fiesty last month, I've been stuck using the "nv" driver.  It seems like no matter what I do to get the "nvidia" driver working, it always fails.  I have pretty much gotten every possible nVidia error message.  Feels that way anyway.

I've tried every version in the repositories.  I've tried many of them on different kernels that I hadn't uninstalled yet.  I've tried several versions from nVidia's site and I've tried THEM of different kernels, too.  I am afraid that, at this point, even if something **were** to work, it would fail because I probably have all sorts of different versions of kernel modules lying around everywhere.

Is there an official way to remove a nVidia driver made from nVidia's website?  Because one of the many (many) error messages I've gotten is the "API mismatch" error.  

Is there some central place on the Ubuntu servers where we can monitor the progress of this problem?

I love Ubuntu.  I've been using it for over a year now, maybe two (though not exclusively).  I am not a noob, but I am definitely not well-versed in GNU/Linux.  I am also very, very slow to seek help.  I fully believe in the power of Google and I have found that most of my problems have been resolved, somewhere, somehow, and that enough diligent searching will lead to a solution.  But in this case, I keep ending up empty handed.

Not having a fully functional graphics driver makes Ubuntu significantly less worthwhile to me.  :(

---

