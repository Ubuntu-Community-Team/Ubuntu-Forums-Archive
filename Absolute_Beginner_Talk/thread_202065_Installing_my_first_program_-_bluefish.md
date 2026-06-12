---
title: "Installing my first program - bluefish"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by msteinblock on 2006-06-22
I do a lot of PHP coding, and decided to give bluefish a try.  This is my first time installing a program and need a little help.

When I go the the bluefish website, it says all I need to do is type apt-get install bluefish.  I tried that, but figured out I needed super user privledges.  So I tried the line sudo apt-get install bluefish.  Same results, says could find package bluefish.  So...I changed the root password, switched over to root and tried running it again, still nothing.  Any ideas what I am doing wrong?  I want to learn...hopefully I wont get frustrated and be tempted to run back to windows.  hehe

~Matthew
[http://Locophotos.com](http://Locophotos.com)

---

### Post by Zikes on 2006-06-22
Sounds like you need to activate the Universe repository.  I know it can be activated from Synaptic, but I'm afraid I can't recall exactly where and I'm not at a Linux machine at the moment.

---

### Post by Jagot on 2006-06-22
Bluefish is in the universe reository which is not enabled by default.

See about enabling the repository here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Then you will be able to install.

---

### Post by johnc4510 on 2006-06-22
You need to enable the universe and multiverse repositories:
System>Administration>Synaptic Package Mgr.
Click on Settings and then Click on Repositories
Put a check mark in all empty boxes and close that window
Click on Reload
Click on Mark all Upgrades
Click on Apply
Now all the extra repositories are there, and you should be able to install bluefish

---

### Post by mlind on 2006-06-22
Yes, you need to enable universe repository
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Arisna on 2006-06-22
Bluefish is not officially supported by Ubuntu.  Therefore, you will need to enable the Community Maintained ("Universe") software repository to install it via apt-get.

The following instructions assume you're using GNOME, the default Ubuntu desktop.  Simply click "System" at the menu in the top-left corner of your screen, navigate to "Administration" and click "Software Properties."  Under the "Installation Media" tab that appears, click the "Ubuntu 6.06 LTS" entry to highlight it.  Now click "Edit."  Check the box next to "Community maintained (Universe)."  If you will want support for certain non-free software applications, you can also enable the "Multiverse" repository at this dialogue.  Click "OK," close the Software Preferences tool, and you should now be able to install Bluefish.

EDIT:  Beaten.  Badly. :P

---

### Post by msteinblock on 2006-06-22
First of all....that was amazing quick help!  Thanks everyone!!

Now I got a little further....


 Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I tried both root and my username again.

---

### Post by msteinblock on 2006-06-22
Got it now....I had to read the last post too.

Thanks again everyone!!!

~Matthew

---

