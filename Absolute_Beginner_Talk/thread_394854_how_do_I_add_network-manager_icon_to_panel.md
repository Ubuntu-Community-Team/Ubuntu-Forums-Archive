---
title: "how do I add network-manager icon to panel???"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by billygates on 2007-03-27
I removed the nm-applet icon from my panel and can't figure out how to get it back.  This of course limits the ability to connect to different wireless networks.

I have uninstalled and reinstalled it using synaptic to no avail.

I know it is running as I have verified in system monitor.

I apologize for being such a n00b.  I am much more familiar with windows but I'm trying to make the switch.

thanks.

---

### Post by overdrank on 2007-03-27
> **billygates said:**
> I removed the nm-applet icon from my panel and can't figure out how to get it back.  This of course limits the ability to connect to different wireless networks.

I have uninstalled and reinstalled it using synaptic to no avail.

I know it is running as I have verified in system monitor.

I apologize for being such a n00b.  I am much more familiar with windows but I'm trying to make the switch.

thanks.

Hi if you will right click on the top panel and say add to panel this will let you add the monitor. Good luck and hope this helps!:)

---

### Post by billygates on 2007-03-27
> **overdrank said:**
> Hi if you will right click on the top panel and say add to panel this will let you add the monitor. Good luck and hope this helps!:)

Thank you for your prompt response.   I have tried that method but have been unable to locate network-manager in the list of items available to add.

I have used the "add panel" several times and was exactly where I went when I first deleted the icon.

---

### Post by charles.g.moore on 2007-03-27
> **billygates said:**
> Thank you for your prompt response.   I have tried that method but have been unable to locate network-manager in the list of items available to add.

I have used the "add panel" several times and was exactly where I went when I first deleted the icon.

[http://www.ubuntuforums.org/showthread.php?t=389986](http://www.ubuntuforums.org/showthread.php?t=389986)

---

### Post by jsartti on 2007-03-27
Go to Control Center, click on "Sessions". In the first tab, click on "new". On the box set "Network Manager" for name and "nm-applet --sm-disable" for command. Close everything, log out and log in. 

Good luck!

P.D.: Sorry for my english, i am a spanish speaker

---

### Post by billygates on 2007-03-27
thank you all for your responses.

I was able to get it back after sorting through some other posts.

Apparently, the icon is included in a group of icons in "Notification Area" of Utilities.

To add it back to my panel, I had to right-click on the panel, select 'Add to Panel', and then select 'Notification Area' under Utilities.

The Network Manager icon as well as Update icon and crash report detection icon reappeared on the panel.

Thanks for helping me learn.

---

### Post by morphodone on 2007-04-14
solved my problem too, thanks.

didn't have any idea that was the notification area!

---

### Post by thischarmingman on 2008-03-04
Hi

I have had the same problem. My wireless network works fine, the network manager is installed, the notification area has been enabled and it shows up has being enabled in my sessions window. I've looked through all the threads and still my nm icon isn't showing up. Further suggestions would be much appreciated!

---

### Post by sayakb on 2008-03-04
> **thischarmingman said:**
> Hi

I have had the same problem. My wireless network works fine, the network manager is installed, the notification area has been enabled and it shows up has being enabled in my sessions window. I've looked through all the threads and still my nm icon isn't showing up. Further suggestions would be much appreciated!

Did you try adding the Network Monitor applet to the panel? Also, do you see other icons like pidgin or amarok or rhythmbox etc in your notification area?

---

### Post by thischarmingman on 2008-03-04
Yes, whenever I add the network monitor it just shows the connection that is currently configured. I am looking for the application that shows the bars and other available connections. Other icons do show up in my notification area including skype, pidgin, updates etc but no network manager

---

### Post by philinux on 2008-03-04
I would remove the notification area. Then add it back then reboot.

---

### Post by sunbird on 2008-03-30
I had the same problem and fixed it - i.e. the network and battery info appears on the panel. But now, I have THREE identical network manager icons, all showing me connected to the same network. I can't seem to remove the other two. Any idea how to proceed?

**Edit:** I removed the icon and then re-added it and re-started Gnome. That fixed it.

---

### Post by rajaram_s on 2008-03-30
Dont you find the network manager in the preferences menu?

---

### Post by Aeo76 on 2008-04-18
Or you could use gconf-editor and add most of the icons discussed to the menu from there, unless I missed what was being asked for.

---

