---
title: "usplash - bootsplash problem, GRUB settings"
date: 2006-10-17
forum: Art &amp; Design
---

### Post by linuxguy on 2006-10-17
I have a problem with usplash. My screen resolution is 1280x1024. After GRUB loads, the splash screen is positioned in the upper-left corner of the screen at a 1024x768 resolution. I have installed Dapper many times before, on this computer, but the splash screen has always been centered properly -- until the last installation I did.

I edited the menu.lst file to set a framebuffer of 794 which corresponds to a 1280x1024 resolution. After that, I noticed that the splash screen was sharper, but still not centered.

Another bug(?) I encountered was that if I ran update-grub after saving a modified version of the menu.lst file, it would revert back to the original settings. To keep the new settings I have to just save the file but skip the update-grub command and just reboot.

A lot of google results pointed to editing a "/etc/usplash.conf" file, but I do not have that file. I reinstalled the usplash package via Synaptic but to no avail. I ended up disabling the bootsplash altogether. I'm running Dapper 6.06.1. Any ideas?

---

### Post by jonah1980 on 2006-10-26
are you on amd64, i've got a similar prob on my amd64 edgy box...

---

### Post by IbeeX on 2006-10-28
> **jonah1980 said:**
> are you on amd64, i've got a similar prob on my amd64 edgy box...

Same thing here :)

---

### Post by Mongoose on 2006-10-29
Here's what I have in mine.  I also updated the alternatives for the usplash, but I still had issues.

[root@namie:~]$ cat /etc/usplash.conf 
# Usplash configuration file
xres=1280
yres=1024

---

### Post by jonah1980 on 2006-10-29
yeah seems weird no fix has been released for this yet. i've had edgy for a few weeks now and still naff usplash screen... what's going on, surely it shouldn't be a big thing to fix??

---

### Post by Mongoose on 2006-10-30
Setting /etc/usplash.conf as:
<code>
# Usplash configuration file
xres=1280
yres=1024
</code>

and then setting /boot/grub/menu.lst to match that ( vga=794 ) resolution makes the 'test screen' fill the monitor.  However it seems update-grub wipes your changes, and cocks up.  I assume it's a package bug, since I don't want any automated process rolling back my changes like that.   I'm on edgy x64 and had a custom usplash before upgrading.  

I'm going to follow the entire HOWTO @ [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto) again and if that fails just revert the alternative to the usplash shipping with edgy.  I don't reboot often, but when I do I'll tell you if it works.   ;)


Edit:

Yeah after I did this the graphics work, but I didn't get any text.  It might just be the text is black.  Hard to tell.   =)

---

### Post by solva on 2006-11-03
I'm having the same problem with Edgy/AMD64.  I've tried fiddling with my usplash.conf settings and passing through a vesafb value to the kernel, but to no avail.

Also, I've got an alterative usplash and instead it's showing the test card.

---

### Post by jonah1980 on 2006-11-03
i've submitted this to lunchpad, can all you guys with same problems also get it on there somewhere and hopefully someone will sort it? thanks if you can help report it.

---

### Post by jonah1980 on 2006-11-03
this is the bug:

[https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545)

---

### Post by seatmanu on 2006-11-04
I had the same problem where not only the resolution was incorrect but also the splash was not centered

I just fixed it and I am using the following usplash as well
[http://ubuntuforums.org/showthread.php?t=278301](http://ubuntuforums.org/showthread.php?t=278301)

The way to do it:

open your /boot/grub/menu.lst

in the following section, change the vga.. I did it in the defoptions but realize that the generated file was still creating a vga=771 due to the following section.

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1cbaac11-59db-4a7c-a2c9-271683bae2c2 ro **vga=794**

Then I ran
sudo dpkg-reconfigure linux-image-$(uname -r)


You can check the results in the /boot/grub/menu.lst as you will see all the options entries with the correct vga this time


title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,3) 
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=1cbaac11-59db-4a7c-a2c9-271683bae2c2 ro vga=794 quiet splash vga=794
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot


Don't forget to make your /etc/usplas.conf to match the vga resolution you chose. for 794 , I have the following
 cat /etc/usplash.conf 
# Usplash configuration file
xres=1280
yres=1024


Reboot! and there you go! you have the uspash with your new resolution (this one being 1280x1024) :)

---

### Post by jonah1980 on 2006-11-04
thanks for the tips but it's still the same for me.

i did everything you said but used the 795 value instead of 794 and it's still up in top corner and looking manky...

---

### Post by jonah1980 on 2006-12-14
ok here's the fix guys:

[http://www.ubuntuforums.org/showthread.php?t=304673](http://www.ubuntuforums.org/showthread.php?t=304673)

i stil haven't got round to trying it yet though!

---

