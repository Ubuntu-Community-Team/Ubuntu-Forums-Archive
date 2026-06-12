---
title: "Xubuntu questions - browsing Samba shares and adding programs to menu"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Fraoch on 2007-08-10
I've been using Ubuntu 6.06, 6.10 and 7.04 in both 64-bit and 32-bit versions on two machines now, and I'm getting (a little) experience.

I just resurrected a third, old machine (AMD K6-2 400 MHz, 192 MB RAM) where I installed Xubuntu 7.04.  I'm trying to do all the things I'm doing with the other two machines on this one, but I've hit two snags:

1.  How to browse samba shares?  Easy enough in Ubuntu, Places - Network, but in Xubuntu there is no "Places" menu and I can't seem to add one by right-clicking the task bar.  I can add lots of other items, just not "Places" or anything that indicates network shares.  Incidentally other machines can view the Xubuntu machine's samba shares just fine.

2.  How to add items to the Applications menu?  In Ubuntu, right-click and "Edit Menus".  But when I edit menus in Xubuntu, I can include/exclude certain system tools and add new individual items, but I can't seem to add items to an existing menu.  I'd like to add something in Graphics - easy in Ubuntu, but I can't seem to edit the Graphics menu in Xubuntu.

Any pointers?  Thanks.

---

### Post by felicity on 2007-08-10
For network share file browsing in Thunar there's a great tutorial that works well [here]("http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu").

For customizing the xfce4 menu, you can follow a guide [here]("http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/"). That Xubuntu blog site also has a lot of other tips that may help if you're new to xfce4.

---

### Post by euler_fan on 2007-08-10
About SAMBA . . . no clue. Good luck.

About menus . . . 

Xubuntu (if I remember correctly) does have a menu editor more along the lines of Gnome. Problem is that it is not exactly intuitive (last time I checked).

The menu is configured using an XML file and the Xubuntu site has a guide for customizing it. Googling for it should pop it up. 

However, once you get into the file, there are two problems. First, rather than creating a large XML file where everything is laid out explicitly, there is a call to an automatic menu builder somewhere else. Not exactly sure how this all works, but it results in the default menus.

The fact that it is all done using XML means you can still manually add entries if you hand-code them in. If you are really bored or insist on your menus being exactly your way you can even code up complete menus from scratch. The syntax is relatively straightforward, especially if you have some experience with coding HTML as it is pretty much all tags.

One suggestion is that if you decide to hand-code a menu, keep a copy of the code to generate the default menus in your new one somewhere until you are done customizing. That way you have access to everything the entire time.

---

### Post by Fraoch on 2007-08-10
Wow, thanks for the quick responses!  I'll try them out.

---

### Post by ugm6hr on 2007-08-10
In case you can't get the thunar network browsing tutorial to work - try pyNeighborhood.  It's dead easy - you can see how I did it by seeing the link in my signature.

---

### Post by Fraoch on 2007-08-10
Thanks ugm6hr.  The biggest problem I'm having is the shared resources won't be up all the time - if this is the case, mounting them causes thunar to crash.

So as explained in the fuse tutorial here: [http://ubuntuforums.org/showpost.php?p=3167443&postcount=79](http://ubuntuforums.org/showpost.php?p=3167443&postcount=79) I'm looking for something that can temporarily mount (or even just browse) a share if it's present, like Ubuntu - Places - Network, and be graceful if it can't find the share, not displaying it rather than crashing all file system GUIs.

So I've moved on to editing the menu, which brought me here: [http://tehpost.blogspot.com/2006/09/xubuntu-xfce-menu-items.html](http://tehpost.blogspot.com/2006/09/xubuntu-xfce-menu-items.html) which is where I'm stuck because I can't seem to create new items in /usr/share/applications even when running as root, the command is accepted but the file doesn't get created.

---

### Post by ugm6hr on 2007-08-10
> **Fraoch said:**
> Thanks ugm6hr.  The biggest problem I'm having is the shared resources won't be up all the time - if this is the case, mounting them causes thunar to crash.

So as explained in the fuse tutorial here: [http://ubuntuforums.org/showpost.php?p=3167443&postcount=79](http://ubuntuforums.org/showpost.php?p=3167443&postcount=79) I'm looking for something that can temporarily mount (or even just browse) a share if it's present, like Ubuntu - Places - Network, and be graceful if it can't find the share, not displaying it rather than crashing all file system GUIs.

Yes - pyNeighborhood is what you are looking for.  It searches for the network drive each time (if you ask it to).  If the network drive doesn't exist - the mountpoint will still appear in thunar - but it will be empty.

Unfortunately, there is no easy way to tell if it's *actually* empty or not present from thunar after mounting with pyNeighborhhod. - you have to research in pyNeighborhood.

---

### Post by Fraoch on 2007-08-11
BTW I did get the menu editing thing to actually work, although it took a couple of reboots.

---

