---
title: "Just a few questions"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Blizzt on 2008-03-12
Another Ubuntu newbie here.  Everything has been working great I just have a few questions.  After a few hours of searching the forums I finally got my wireless network working but each time I start Ubuntu I have to go to the terminal and enter "sudo modprobe ndiswrapper" to even get the option to connect wirelessly.  Is that normal?  Also it doesn't connect automatically, I have to use the "Connect to other wireless network" option in the network manager and enter my SSID.  Is that normal?  If these things are normal that's fine because I'm loving Ubuntu.  Just curious.  Any help will be greatly appreciated.  Thank you.

---

### Post by bren on 2008-03-12
no its not normal......

if you type lswh -C network and lspci and post the results here you will get more help 

or if you want search for wpa supplicant .... i believe this is the next step (but not sure)

bren

---

### Post by ryanhaigh on 2008-03-12
To load ndiswrapper at startup you will need to add it to this /etc/modules file. Press alt-f2 then enter ```
gksudo gedit /etc/modules
``` which will open a text editor, add ndiswrapper to the end of the file, save and exit. Next time you boot the module should be loaded automatically.

Do this and then see if your other issue persists, if it does and you always connect to the same wireless network, you may consider setting up the network configuration in system>admin>network, don't use roaming mode and set the name of the essid in there. Alternatively you could use wicd I have not used it myself but people have praised it for working where network manager fails so it may be of use.

Is your wireless ESSID hidden on the router?

---

### Post by Blizzt on 2008-03-12
OK, ndiswrapper now loads on startup but it still won't connect automatically.  I tried disabling roaming and entering my SSID but still nothing and my SSID isn't hidden.

Here's another weird thing, when I force it to connect I actually pick up two other networks.
So it's like it doesn't even look till I tell it to.

I don't mind the extra step to connect because it works great after I do.  I was just curious why it did that.  

One more thing, I am amazed at the improvement in my computer.  I was watching youtube videos and I couldn't believe the improvement in my video.  I can watch at full screen and it's not blurry.....lol.  Ubuntu rocks!!!!

Thanks to everyone that posted.  Keep up the good work.

---

### Post by ryanhaigh on 2008-03-14
Maybe the interface isn't being brought up automatically, when you restart your computer before you 'connect to other network' try opening the terminal and doing an ifconfig. If you don't supply an interface or -a it only shows the active interface (according to the man page anyway). If this is in fact whats going on there may be a workaround, for example you may be able to put ```
ifconfig up wlan0
``` into /etc/rc.local which is the last startup script executed.

EDIT: change wlan0 to whatever the wireless interface is.

---

