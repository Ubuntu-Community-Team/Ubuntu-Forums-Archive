---
title: "How to access Nvidia GUI quickly??"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-21
The Nvidia settings can be accessed through:
**sudo nvidia-settings**

Is there a quicker way, say through system/device manager graphical menu?

How to access it creating a link and clicking on an icon?

Thanx

---

### Post by phr0ze on 2007-06-21
Right click on the desktop and select Create Launcher
Type a title for this.
In command, put this command: gksudo nvidia-settings
Thats it. you can click this to quickly launch the settings.

You can also drag this up to the menu bar to add an icon up there.

BTW: You should use GKSudo for any graphical program instead of sudo.

---

### Post by deadlikeoscar on 2007-06-21
Go to google images and find yourself a good nvidia png icon. Download it and then open a terminal. Type **sudo mv /home/deadlikeoscar/Download/nvidia.png /usr/share/pixmaps** Change the /home/deadlikeoscar etc to whatever your download directory is. Now you have an icon you can use. Next right click on the top on say System. It doesn't really matter where and select Edit menu. Scroll down to System and I put it under Administration. Click on Administration or wherever you want to put it. On the right choose New Item. A Create Launcher box will open. Name the Launcher whatever you want, type nvidia-settings under command (unless you know for a fact you have to use sudo--I don't) And click on the no icon thing on the left and add the nvidia icon you downloaded. That should be it.

---

