---
title: "Newbie questions"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by JRV on 2007-06-13
Okay, it installed.  

How do I log in as root?
When I attempted to log in as root from the main log-in screen I got a message telling me I could not log in as system administrator from this screen.

I needed to make some changes to my /boot/grub/menu.lst file.  
The system would not let me save the file once I edited it.
I made the changes by booting Puppy Linux from a USB pen drive.  I'm sure this is not the best way.

How do I get a screen resolution greater than 1024x768?

I have an Acer 24" monitor with a native resolution of 1920x1200.  After paying for this monitor I need to be able to use it.  
The only choices Ubuntu gives me are 640x480, 800x600, and 1024x768.

---

### Post by ctsiow on 2007-06-13
> **JRV said:**
> Okay, it installed.  

How do I log in as root?
When I attempted to log in as root from the main log-in screen I got a message telling me I could not log in as system administrator from this screen.

I needed to make some changes to my /boot/grub/menu.lst file.  
The system would not let me save the file once I edited it.
I made the changes by booting Puppy Linux from a USB pen drive.  I'm sure this is not the best way.

How do I get a screen resolution greater than 1024x768?

I have an Acer 24" monitor with a native resolution of 1920x1200.  After paying for this monitor I need to be able to use it.  
The only choices Ubuntu gives me are 640x480, 800x600, and 1024x768.
what graphics card do you have in your system? Do you have the correct drivers for linux?

---

### Post by limelightos on 2007-06-13
don't know about your login probs but have you installed the drivers for your display?

---

### Post by HotShotDJ on 2007-06-13
> **JRV said:**
> I needed to make some changes to my /boot/grub/menu.lst file.
```
gksudo gedit /boot/grub/menu.lst
```
use either sudo (for terminal commands) or gksudo (for gui apps in gnome) to run as root.  No need to login as root.

---

### Post by JRV on 2007-06-13
The graphics card is an Evga eGeforce-6600 PCI Express.

How do I find and install drivers?

---

