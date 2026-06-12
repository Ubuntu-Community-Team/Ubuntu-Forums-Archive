---
title: "Argh!! Booting into terminal and Win network probs"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Clumber on 2007-03-24
I just spent over 2 hours searching these forums, and linux forums in general.  I just **know** that I don't have a unique pair of issues here, but I am apparently not of the "right mind" to use the correct search terms or something.

2 unrelated issues:
A. While researching the below issue for solutions, I stumbled onto Automax and decided that might be cool, and used it to install several packages for trying out.  After rebooting, now my computer logs into the terminal and I have to type "xstart" to get back my GUI happy Gnome desktop.  Yes, I know better than to install multiple things without making sure each works first, but oh well. _How do I get it to boot into Gnome automatically again??_

B. Original issue is I cannot seem to get access to my Win boxes. Ubuntu sees the windows network, sees the workgroup, and sees the Win boxes, but if I try to open any of the Win boxes, I get a huge error box that (in part) reads,
*      The contents of the file indicate that the file is of type "x-directory/smb-share". *
**and further**
  *  To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. *

**Huh???**  Long time ago I was playing with a SUSE distrib and had no problems setting it up to happily mount and see Win XP and Mac boxes.  Have I gotten stupider?:confused: 

Detail info:
   Win boxes are XP SP2 and a couple Vista boxes.
   Using Ubuntu 6.10
  I am a n00b for Linux and Ubuntu, but very fluent and exp with Windows, and am even a state gov. tech support Win boxes for a living.

Many TIA!!  I am hoping to avoid reinstalling Ubuntu, since I have already done some work and customization on this setup.

---

### Post by Wally68 on 2007-03-24
Sounds like gdm (gnome display manager  AKA the login screen) has been removed from /etc/init.d. Run the following commands to add it back in there:


```
sudo rc-update add gdm default
sudo  /etc/init.d/gdm start

```The first command adds gdm to the default runlevel, usually runlevel 3. The second, of course starts gdm.

I can't help you with the samba portion of your question, sorry.

---

