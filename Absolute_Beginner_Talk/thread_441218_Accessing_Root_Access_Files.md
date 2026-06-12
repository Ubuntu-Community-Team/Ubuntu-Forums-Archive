---
title: "Accessing Root Access Files"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-05-12
Hi, I want to put an apple picture as my distributor logo. One thing, I need to do it as root (I think). 

How do I get into my files as root? I want to do it with being able to see it in the normal view though. The same as clicking "Places - Home Folder". How do i do that?

Thanks in advance, Liam.

---

### Post by taurus on 2007-05-12
<Alt>F2 -> gksudo nautilus

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tenicus on 2007-05-12
Run nautilus as root.  Open a terminal and type "sudo nautilus"

---

### Post by liamwithers on 2007-05-12
Thanks, but that isn't what I need is it? I need to move my Apple picture into the same folder as the ubuntu logo. Then I need to delete the Ubuntu logo and rename the Apple logo. STILL CONFUSED!

---

### Post by psusi on 2007-05-12
Yes.. and you can do that if you run nautilus as root.

---

### Post by jfinkels on 2007-05-12
> **liamwithers said:**
> Thanks, but that isn't what I need is it? I need to move my Apple picture into the same folder as the ubuntu logo. Then I need to delete the Ubuntu logo and rename the Apple logo. STILL CONFUSED!

Once you open Nautilus as root, you can move files around just as you would normally: click and drag, copy and paste, rename, etc. What specifically are you having a problem doing?

---

### Post by liamwithers on 2007-05-12
> **jfinkels said:**
> Once you open Nautilus as root, you can move files around just as you would normally: click and drag, copy and paste, rename, etc. What specifically are you having a problem doing?

Right, I've got in with Nautilus.. Resized my Apple picture into the different sizes I need (I think).

I have made them into 24x24/32x32/48x48/128x128

Those sizes are the ones in NuoveXT. I am using NuoveXT for my icons (according to System > Preferences > Theme > Custome theme > Customize). Then I renamed them to ubuntu-logo.png which was the name for my original icon. Do I require a restart? Can somebody download NuoveXT and try something similar to see if I'm doing this right?

Thanks in advance, Liam.

---

### Post by aysiu on 2007-05-12
> **Tenicus said:**
> Run nautilus as root.  Open a terminal and type "sudo nautilus"
Or, better yet: ```
gksudo nautilus
``` Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jfinkels on 2007-05-12
> **liamwithers said:**
> Right, I've got in with Nautilus.. Resized my Apple picture into the different sizes I need (I think).

I have made them into 24x24/32x32/48x48/128x128

Those sizes are the ones in NuoveXT. I am using NuoveXT for my icons (according to System > Preferences > Theme > Custome theme > Customize). Then I renamed them to ubuntu-logo.png which was the name for my original icon. Do I require a restart? Can somebody download NuoveXT and try something similar to see if I'm doing this right?

Thanks in advance, Liam.

What is the location in the filesystem for the files you wish to replace? I don't know what you mean by 'distributor logo'...where would I find this logo on my own Ubuntu system?

---

### Post by aysiu on 2007-05-12
*distributor-logo* is the name of the logo for Gnome that is either Ubuntu's logo or the Gnome foot (or, in this case, the Apple logo): ```
locate distributor-logo
/usr/share/icons/Human/scalable/places/distributor-logo.svg
/usr/share/icons/Human/22x22/places/distributor-logo.png
/usr/share/icons/Human/24x24/places/distributor-logo.png
/usr/share/icons/Human/48x48/places/distributor-logo.png
/usr/share/icons/gnome/scalable/places/distributor-logo.svg
/usr/share/icons/gnome/16x16/places/distributor-logo.png
/usr/share/icons/gnome/24x24/places/distributor-logo.png
/usr/share/icons/gnome/32x32/places/distributor-logo.png
/usr/share/icons/gnome/22x22/places/distributor-logo.png
/usr/share/icons/Tangerine/scalable/places/distributor-logo.svg
/usr/share/icons/Tangerine/16x16/places/distributor-logo.png
/usr/share/icons/Tangerine/24x24/places/distributor-logo.png
/usr/share/icons/Tangerine/22x22/places/distributor-logo.png
/usr/share/icons/Tangerine/32x32/places/distributor-logo.png
/usr/share/icons/Tango/scalable/places/distributor-logo.svg
``` Keep in mind, though, that sometimes *distributor-logo* is just a symlink (or shortcut or alias) to the real image file, which might be called something else like *start-here*.

---

### Post by liamwithers on 2007-05-12
The place where the NuoveXT ones are is: /home/liam/nuoveXT-1.6 then the file sizes.

The other ones are in /usr/share/icons then the icon theme, then places, then the file size.

I tried a restart and nothing happened! Help please!

---

