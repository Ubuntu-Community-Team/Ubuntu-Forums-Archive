---
title: "Dual Monitor Set-Up of XP/ VMWare on Ubuntu"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by tikbjamin on 2007-03-13
I am having trouble setting up my dual monitor system (2x Dell 18.1" UltraSharp flat panel) with a screen resolution that utilizes all the screen real estate on both monitors and produces a picture that I can look at for 10 or more hours per day.  I used the TwinView in Ubuntu to set up the screen.  With one resolution I get a good picture but on only one screen and the Full Screen option is centered on about 55%  of both monitors.  I plan to use them on FS mode. 

I need to get this project completed in the next couple days and greatly appreciate once again the help of the community.

Thanks,
TBJ.

---

### Post by chuckyp on 2007-03-13
Check out xinerama package this may help you out.

---

### Post by tikbjamin on 2007-03-13
I read here [COLOR="DarkRed"]http://lnxwalt.wordpress.com/2006/12/26/vmware-player-maximum-screen-resolution/ [/COLOR]that the vm gets its maximum screen resolution from the host OS and that I can edit the .vmx file to adjust screen resolution.  I can see the file in /var/vm/vmware/VirtualMachines/Windows XP Professional.vmx when I do a search of the File System for a *.vmx file.  How do I open this to edit it though?

TBJ.

---

### Post by tikbjamin on 2007-03-13
Chucky or anyone else,
My current dual monitor setup works fine in Ubuntu.  I have a problem when I work in my VM.  I plan to run XP only programs in this VM and need 100% of my screen real estate.  Does Xinerama provide any advantage over TwinView in VM mode? 

I imagine I would have to remove, maybe reinstall stuff.  It took me a while to get this far, hence my hesitation to change anything just yet.  But I will, if I must.

TBJ.

 > **chuckyp said:**
> Check out xinerama package this may help you out.

---

### Post by veloce on 2007-03-13
Xinerama will probably not be an improvement if you have twinview working.  However, all the dual-head systems seem to work slightly differently so it just might.

Before doing that though, I would suggest trying a different means of interacting with your vm: rdp.  I use gnome rdp because it allows me to define an arbitrary screen resolution - I can have use 1270x996 instead of 1280x1024 and it fits within a window on my 1280x1024 screen.

Both gnome rdp and terminal server automagically did what I think you are after in full screen mode.  They made a single windows desktop across the two screens.  Unfortunately for me, my screens are different resolutions - some of my desktop was "off screen".  If yours are the same this may be just what you want.

This requires a virtual network to be setup - I use host only networking.

---

