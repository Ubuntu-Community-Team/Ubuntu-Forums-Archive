---
title: "My Startup Usplash is dissolving"
date: 2008-08-10
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-08-10
Hi,
  Using the Startup Manager, I experimented with several different .so files to have different Usplash experiences...I perhaps made the mistake of trying the higher resolution settings like 1600 x 1200. 

Those settings ARE options that are available in the Startup Manager, but I've heard through the grapevine that in general, 1024 x 768 is really the highest resolution possible in the boot areas. 

But trying to get things back to square has not been so straightforward; trying the higher settings caused the graphics to get weird and even though I'm back to the basic settings of 1024 x 768 / 8-bit, the graphics now look grainy and dissolved. 

The colors are all wrong and almost solarized. 

I've tried these steps but with no results: 
- Uninstalled and re-installed Startup Manager;
- removed all .so files and themes except for the default;

I can't see what else to try. I appreciate any help or suggestions.

Many Thanks, 

Frank B.

---

### Post by VHDLnub on 2008-08-11
Hey Brightbelt, I JUST got thru getting usplash to run with two of the basic usplash-theme's "usplash-theme-debian, usplash-theme-ubuntu", with my "menu.lst" set to "vga=791". I had to set the frame buffer to 791, in the "menu.lst" file to get it to work. These two ubuntu pages helped some:
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash) 
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
I made sure I ran "sudo update-grub" then "sudo update-initramfs -u", after the changes.

---

### Post by cyberdork33 on 2008-08-11
> **VHDLnub said:**
> I had to set the frame buffer to 791, in the "menu.lst" file to get it to work.
In that case, I'd guess that the framebuffer resolution set at boot and the resolution of usplash need to match to avoid distortion. 

Here is a table of VGA values you can use:
[http://www.rickycampbell.com/table-of-framebuffer-resolution-values/](http://www.rickycampbell.com/table-of-framebuffer-resolution-values/)

Note that sometimes they will not work even though the monitor / card should support that resolution. 791 is usually a safe value to try though.

---

### Post by Brightbelt on 2008-08-11
Thanks guys! I'm a little slow getting back, but Thanks for the ideas. I may yet have to continue this thread depending upon my results.

---

### Post by Brightbelt on 2008-08-11
The 791 works !! Many Thanks ! However, there's something I can't explain:

Thanks Cyber for your table of values; by your table, my VGA should be set at 773. And in my menu.lst file it WAS already set at 773.  

'773' reflects the 8-bit / 1024 x 768 setting I have chosen in the Startup Manager as well. But it didn't work, even though 773 reflects that setting exactly...why the dissolving/solarization of my usplash colors ??

Oh well. :confused: Many Thanks for helping; at least it works :)

---

### Post by brambles on 2008-08-11
This may not be what bit you but I had a similar problem recently after playing about with startup-manager which was caused by a different resolution being set in /etc/usplash.conf.

Cheers M

---

### Post by Brightbelt on 2008-08-12
Thanks Brambles. I'll look into that.

---

