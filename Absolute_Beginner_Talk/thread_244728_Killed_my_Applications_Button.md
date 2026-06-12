---
title: "Killed my Applications Button"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by gjprice on 2006-08-26
Hi Complete Newbie to Linux here.  Have been motoring on quite well and have hit a bit of a wall ](*,) with something really simple I'm sure.  

On clicking the Applications button nothing happens (well it goes dark). Have right clicked the properties and tried the Use default desktop menu file button with no luck. Not sure where to look under the Custom menu file option.

Would appreciate if someone could look and tell me how to get it running again. Am launching programs off Alt+F2 at the minute, getting annoying.

Cheers!

---

### Post by gn2 on 2006-08-26
Right click on the panel at the top, 
select "Add to Panel" 
scroll down to "Utilities" section, 
highlight the "Menu Bar" (has Ubuntu logo above it) 
and click on the +Add button.

Hope that helps

---

### Post by gjprice on 2006-08-26
Thanks for quick reply.

sorry should have clarified (using xbuntu). Got similar options by right clicking and adding new item. Added Xfce Menu which gives a pop-up menu rather than the drop down style.  Button for Applictions still not working.  Would removing it from the panel make it available for reinstalling? (with correct shortcut address)

Thanks

---

### Post by muep on 2006-08-26
Have you tried logging out and back in? The XFCE in Xubuntu is a beta version so it might have some bugs in it. Maybe the menu applet just crashed?

---

### Post by gjprice on 2006-08-27
Have deleted both the application menu and xfce menu and re-added the xfce menu option. Still have a dead button.  The xcfe menu did work for a while but not anymore. Have tried logging in and out and restarting several times to no avail.  Can add the weather and battery monitor etc without any problems.

Any other ideas. Can the applet be reinstalled. If so how?
Thanks all.

---

### Post by gjprice on 2006-08-27
Am now able to get the Xfce4 Appfinder using the Quick Launcher =D>  only but not by adding a simple Xfce button! ](*,) ](*,)

---

### Post by SoloSalsa on 2006-08-27
Don't worry, everyone runs into this  (like me).
This is not specifically Xubuntu's fault, but rather the build of XFCE it uses.
You will need to update as soon as possible, and it will go away.  But in the mean time, there is another thread with all the answers...  Let me find it...
Done!```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```
And the thread that talks about it is [here]("http://www.ubuntuforums.org/showthread.php?t=227684&page=2&highlight=xubuntu+menu").
Glad to help.

---

### Post by gjprice on 2006-08-27
Beautiful!!\\:D/ 
Thanks SoloSalsa!

---

