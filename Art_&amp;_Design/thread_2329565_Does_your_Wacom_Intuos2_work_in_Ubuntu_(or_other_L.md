---
title: "Does your Wacom Intuos2 work in Ubuntu (or other Linux)?"
date: 2016-07-03
forum: Art &amp; Design
---

### Post by wacomlinuxuser1234 on 2016-07-03
ATTN: It seems 'Hardware' would be a better place for this thread. Can someone with sufficient privileges please move it there? Sorry for inconvenience!     Hello all,  I am currently investigating a bug in the Linux Wacom driver relating to USB Intuos2 tablets.  In order to work out this bug, I need to know how common issues are.   If those who have an Intuos2 tablet and uses Ubuntu (or other distribution) could answer the following questions, it would be a great help!        
[list]    
[*]1. Which distribution and version are you running (e.g. Ubuntu 14.04, Debian 8.5, Fedora 24)? 	      Optional: the kernel version (find by running 'uname -a' in terminal)    
[*]2. What size Intuos2 do you have?     
[*]3. Is your Intuos2 stylus recognized as it should be in Linux if you start the computer with the tablet connected? 	 Optional: which programs are you using?    
[*]4. Does your Intuos2 stylus continue to be recognized when the tablet is hotplugged (unplugged and plugged back in when the computer is still running)?    
[*]5. Have you confirmed that the tablet works fine in Windows/OSX?    
[*]6. Any extra information such as quirks you have found to get it working.    
[/list]
          My answers:        
[list]   
[*]1. Operating system: Debian 8.5 with kernel 3.16.0-4-amd64   
[*]2. Intuos2 6x8 (A5)   
[*]3. Stylus is recognized if I start computer with tablet connected. Works as pen in MyPaint and GIMP, and as a mouse in other programs.   
[*]4. Stylus is no longer properly recognized when tablet is hotplugged.   
[*]5. Not confirmed working in Windows/OSX, however as it works in Linux (expect hotplugging) this is not super relevant.   
[*]6. Instead of restarting computer after hotplugging, I can run 'sudo rmmod wacom && sudo modprobe wacom'. The stylus is then properly recognized.   
[/list]
         Thank you for your time!  -------  Note: If you are running in to issues with your Intuos2 tablet (even if you are not using it in Linux) have a look at this page for a way to reset your tablet. I have not tried this as it requires Windows / OSX. [http://maggiewang.com/2007/08/21/how-to-fix-an-unresponsive-wacom-intuos-2-tablet](http://maggiewang.com/2007/08/21/how-to-fix-an-unresponsive-wacom-intuos-2-tablet) but it may be of some help.

---

