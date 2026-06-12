---
title: "Ubuntu Install &amp; LiveCD - Confused =\"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by DennHenda on 2006-07-10
Hey guys.  I installed Ubuntu with this CD my bro gave me.  Version 5.10.
Well, it formatted the hard disk, went through the procedure stuff and all that.

I tried booting it after the installation and it stopped at this blank screen with the little line blinking at the top left.

My dad restarted it and popped in the Live CD, and it booted up.  But I'm guessing that it isn't using the stuff I just installed when using the Install CD.  I also read somewhere that there was an install thing on the Live CD, and I don't know anything about it other than that. >_<

So my question is...Did something go wrong during the installation I first tried, and that's the reason it wouldn't boot up?  If you need more information with PC specs, ask away.  Not sure what info you'd need to help me out.

Completely new to Linux, I usually use Windows.  My brother was using Linux to run some online game servers, and I decided I wanted to give Linux a try.
Thanks in advance.

---

### Post by raldz on 2006-07-10
5.10 is quite old, you could download the latest Ubuntu 6.06 here:

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

The "Install" in the Live CD is a feature of 6.06..

---

### Post by Kyran on 2006-07-10
I could be a graphic issue. Try booting up in recovery mode and typing dpkg-reconfigure xserver in the console. Follow the promps and such, paying special attention to graphic and monitor settings. (Especially the section on identifying the monitor if you've got an nVidia card.)

> 5.10 is quite old, you could download the latest Ubuntu 6.06 here

Some poeple like the classics, or are just waiting for their new cds to arrive. :D

Ubuntu 5.10 doesn't have an install from Live CD option, 6.06 has that feature.

---

### Post by tonyp1969 on 2006-07-10
You can pick up the latest ubuntu DVD from pretty much all the Linux magazines at the moment.

---

### Post by raldz on 2006-07-10
> **Kyran said:**
> 
Some poeple like the classics, or are just waiting for their new cds to arrive. :D


I just assumed that it's his frist time to install ubuntu, and 6.06 is definitely easier to install than 5.10..;) ;)

---

### Post by DennHenda on 2006-07-10
Yeah, it is my frist time installing.  I attempted that 6.06 now.  I think the same thing happened...I ran using the LiveCD, and installed using the Install thing on the desktop.  Went through all the stuff and got it all installed.
After I hit the restart button and it shut down, I took out the CD and started rebooting.  Got to that same screen with the blinking line thing again.  Any more suggestions?  ._.

---

### Post by elemental666 on 2006-07-10
Are you installing on a laptop or desktop? Make/Model of machine?  What kind of video card do you have (make/model)?  Do you get any post warnings during boot?  What happens when you go into recovery mode?  We need more info.

---

### Post by gingermark on 2006-07-10
It sounds to me like a graphics driver problem. Select "recovery mode" as Kyran suggested, and when you get to the command prompt type ```
dpkg-reconfigure xserver-xorg
``` Accept the defaults, except for when you need to select the video driver. Here select "vesa". Then reboot.

This should then allow you to boot into X (the graphics part). We can the hopefully sort out the right driver for you. Assuming these instructions work, let us know what video card you have.

---

### Post by DennHenda on 2006-07-10
Well, I can't figure out how to get it into "recovery mode."  But I'm installing on a desktop - I've got a Gateway model E3200 with onboard video.  I don't think I get any post warnings or anything.
Thanks again, guys.  I guess if I can get into "recovery mode" it should be smooth sailing.

---

### Post by gingermark on 2006-07-10
When you turn your computer on you should be greeted with GRUB - a bootloader. It should provide the option to boot into recovery mode.

---

### Post by DennHenda on 2006-07-11
Well, theres the problem...I don't get the grub when I start it up.  That flashing line thing comes before it, I suppose.
It shows the Gateway logo and a progress bar.  When it gets done with that, it stops everything.
Only thing it seems I can do is go into the setup and change BIOS.

---

### Post by elemental666 on 2006-07-11
hmmm, you don't ever see a countdown or anything

boot from the live cd and run lspci and paste the results here so we can see what video chipset and the like you have.

---

