---
title: "Don't display mounted drives on the gnome desktop"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by tcollogne on 2006-07-21
I have a number of partitions that I mount at startup using fstab.
I find a little annoying that the drives that get mounted, are displayed as desktop icons.

Is it possible to prevent this. I mean can I mount partitions a startup without displaying them as shortcut icons on the desktop.

By the way I use ubuntu 6.06 with gnome.

Thank you.

---

### Post by catlett on 2006-07-21
Go to Applications<System Tools<Configuration Editor once it opens select "apps", then select "nautilus". Select "desktop" and a page comes up with entries for what nautilus views on the desktop. Un-check "volumes_visible" and the icons will disappear.
If you cannot find the configuration editor in the menu, you may have to enable it with Alacarte menu editor which is located in Applications<Accessories

---

### Post by Jose Catre-Vandis on 2006-07-21
Thanks, good tip :-)

---

### Post by Drakkor on 2006-07-22
That sounds fine, catlett,only under Applications>System Tools, I have only
Automatix and GParted ??   :confused:
Oops,nevermind,read all of your post,lol Thanks ! :p

---

### Post by catlett on 2006-07-22
Open Alacarte menu editor which is under Applications<Accessories, When you select alacarte a window opens. On the left of the window is the choices that are in the panel menu.
Click on System Tools. Wait a second and a list will come up on the right side of the window. Check off the box for Configuration Editor. You may also want to go throught the rest of the alacarte menu and see if there are other things you want to put on the menu.

---

### Post by Drakkor on 2006-07-22
Read above,lol :D

---

### Post by annda on 2006-07-22
here it goes again :) 

> **catlett said:**
> Go to Applications<System Tools<Configuration Editor once it opens select "apps", then select "nautilus". Select "desktop" and a page comes up with entries for what nautilus views on the desktop. Un-check "volumes_visible" and the icons will disappear.
If you cannot find the configuration editor in the menu, you may have to enable it with Alacarte menu editor which is located in Applications<Accessories

---

### Post by edccmu22 on 2007-11-05
I currently have two windows partitions being mounted and displayed.  Is there a way to still mount both but only display one?  I'm using Gutsy.

Thanks.

---

### Post by rsambuca on 2007-11-05
If you change the mountpoint from /media/... it shouldn't be displayed on the desktop by default.

---

### Post by travis31 on 2007-11-05
> **edccmu22 said:**
> I currently have two windows partitions being mounted and displayed.  Is there a way to still mount both but only display one?  I'm using Gutsy.

Thanks.

This might help [http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/]("http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/")

---

### Post by rsambuca on 2007-11-05
> **travis31 said:**
> This might help [http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/]("http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/")

That won't work in this case because he only wants one of them to disappear from the desktop.

---

### Post by travis31 on 2007-11-05
> **rsambuca said:**
> That won't work in this case because he only wants one of them to disappear from the desktop.

The link has a section below that shows how to show only some partitions on the desktop.

---

### Post by rsambuca on 2007-11-05
> **travis31 said:**
> The link has a section below that shows how to show only some partitions on the desktop.

Sorry, I missed that.  You are correct.

---

### Post by Seikmann on 2008-02-18
Hmm. I have no such thing as Alacarte editor under "accessories" or anywhere else (7.10)

---

### Post by ububaba on 2008-02-18
> **Seikmann said:**
> Hmm. I have no such thing as Alacarte editor under "accessories" or anywhere else (7.10)
I too have run into the same problem. All my HDDs can be seen in[B] Partition Editor
[/B] but not on the desktop. The icons in media - Browser, don't contain any files at all!

---

