---
title: "Basic Installation"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Gnigma on 2007-12-20
This is the procedure I use. Any other way seems to involve lots of time and frustration. Hopefully, it will help somebody: 

1) Get Ubuntu on CD. Get the latest stable version available. Have a working internet connection; broadband is a necessity. Make sure your wireless card and ethernet adapter is compatible with Ubuntu-- check the lists. Also, set your gateway/router to open security, and DHCP, then connect via ethernet (hardwire) to the machine you're installing on. 

2) Boot from the CD and run the install--- only set up one user until it is up and running. Sometime in the last third of the install, you should be able to see the modem traffic leds flashing. If this does not happen, your internet connection isn't working. Stop here and change the settings on the gateway or modem for less security until this connection works. Either this connection has to work or you are in for lots of typing and lots of time on this forum. Eventually the install program will complete. Reboot without the CD.

3) Log on. DO NOT TOUCH THE NETWORKING SETTINGS! Do not try to use the browser, don't look at the rest of the network--- the install is NOT complete! Instead, mouse the icons at the top right of the screen-- one of them will say "updates," and there will probably be one that says "restricted drivers." Click on the "updates." Run the install program. This is where you need broadband-- mine had 148 updates that took 6 hours to download, and another hour plus to install. When it's done, rerun the "updates" installer for anything that failed. They won't take effect until you reboot, but don't reboot yet.

4) Do the same thing for the "restricted " items. I had to run this twice: once for the video card driver and once for the wireless card firmware. NOW reboot.

5) After you log on, check the web browser it'll probably connect right up via the ethernet hardline.  If it works, exit the browser. Now go to System/administration/network. (Drop down @ top left of screen.) It'll ask you for your password. Enter the same as your login password. Highlight the wireless connection, then click properties. Disable roaming mode, unless it's a laptop, select DHCP on the little drop down menu, and enter your ESSID if it's not broadcast. Go back and checkmark the wireless connection.

6) Exit the program and restart. Unplug the ethernet cable while it's shutting down. When you log back on, the wireless should work for your browser. You're done. Use it like it was yours.

This is just my own experience with the install procedure. This has worked on four different machines, all with different motherboards, and different (Ubuntu compatible) wireless cards. I've only tried it for single OS.

---

### Post by Xiong Chiamiov on 2007-12-21
You can choose to install without connecting to the internet and apply updates later.  I sure did.  And surprisingly, my noname wireless card worked out-of-the-box.

---

