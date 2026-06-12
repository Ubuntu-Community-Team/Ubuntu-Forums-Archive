---
title: "Should I format my hard drive?"
date: 2014-02-27
forum: Any Other OS
---

### Post by thedoctor2016 on 2014-02-27
I really messed up and I need help. I have both Windows 8 and Ubuntu (I think it's 13.04). When I bought my PC, it came preinstalled with Windowss 8. So, while I was using Windows, I deleted a graphics card driver I thought was useless. Turned out I needed it, and now when I try to boot to Windows from the boot menu/screen I see the blue Windows sign and a spinning loading animation. Once it goes away, my monitor flickers every 2 seconds from no input to the default black screen monitors show when they aren't showing anything. I used Ubuntu for a while. I thought I was smart enough to figure out how to update the graphics driver, but I messed up and now when I boot to Ubuntu I get that default black screen. What I want to know is, do I need to format my hard drive to fix this? I have a Windows 7 disc so I don't mind I just don't know how. Or is there a way to use a command line or "Advanced options for Ubuntu" on the boot menu to completely reinstall Ubuntu? My biggest concerns are partitions. I don't know much about them but I think that's what's keeping me from installing Windows 7 on my PC along with the other two broken OSs. If anyone has any other idea, I would be very grateful.

---

### Post by mansonfan78 on 2014-02-27
Have you tried the nomodeset flag when booting Ubuntu?  At the grub menu highlight Ubuntu and press e to edit, find the line that ends with "quiet splash" and enter the word "nomodeset" at the end so it reads "quiet splash nomodeset" (no quotes).  That should allow you to boot into Ubuntu in a basic graphics mode and then install the video driver.

---

### Post by buzzingrobot on 2014-02-27
Doesn't Windows have a recovery/Safe Boot option, or something similar, that would allow a new driver to be installed via Device Manager?  It's been a long tine, but I seem to recall that.

---

