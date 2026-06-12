---
title: "Network Control On Panel"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by richard978 on 2008-03-11
Without knowing it I've managed to accidentally remove the icon for on my panel which allows me to quickly choose which connection to use.

Does anyone know how to restore this to my panel.....

---

### Post by glennric on 2008-03-11
Have you rebooted?  It may come back if you do.

---

### Post by richard978 on 2008-03-11
yes and no it didn't....

---

### Post by glennric on 2008-03-11
Try running "nm-applet &" from a terminal.

---

### Post by richard978 on 2008-03-11
just returned a number

---

### Post by glennric on 2008-03-11
Hmm.  Well to make the applet load on startup go to System->Preferences->Sessions and click Add.
Type in 
Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager Applet
Then click OK.
Reboot and you should have it back.  However, just to make sure nothing else is wrong type
```
nm-applet --sm-disable &
```
in a terminal.

---

### Post by tangibleorange on 2008-03-11
How about:
```
nm-applet
```

---

### Post by forrestcupp on 2008-03-11
You should be able to right-click the panel and choose Add to panel.  That will give you a window full of applets that you can add to the panel.  You can just choose the network applet from that and it will be back.  It should still be there after you reboot.

---

### Post by Bölvaður on 2008-03-11
> **forrestcupp said:**
> You can just choose the network applet from that and it will be back.

It should not be there with the default install. So that would not work.
typing nm-applet in terminal works for me, and it lasts till the X-server is restarted. So adding "nm-applet" to sessions  (System - Preferences - Sessions - Add) it should be there next time you restart.

Name: Manual Network configuration
Command: nm-applet
Comment:

---

### Post by forrestcupp on 2008-03-11
When I right-click on my panel and choose 'Add to Panel' the window that comes up has a section called 'System & Hardware.'  Right there in that section is an applet called 'Network Monitor' that I can add to my panel and it stays there.

---

### Post by tangibleorange on 2008-03-11
> **forrestcupp said:**
> When I right-click on my panel and choose 'Add to Panel' the window that comes up has a section called 'System & Hardware.'  Right there in that section is an applet called 'Network Monitor' that I can add to my panel and it stays there.

I think the OP is referring to the network-manager icon that appears in the system tray, rather than a seperate network monitor icon on the GNOME panel. Confusing, I know...

---

### Post by richard978 on 2008-03-11
I can add the network monitor but not the network control. I've tried typing nm-applet
 in the terminal but does nothing????????????/

---

### Post by tangibleorange on 2008-03-11
does it return nothing? no error message?

try:
```
nm-applet --sm-disable
```

---

### Post by glennric on 2008-03-11
Do you have the system tray on your panel?  Right click on the panel and select "Add to panel".  Then find the "Notification Area" applet and add that.  See if the network manager shows up then.

---

### Post by Bölvaður on 2008-03-11
When you say it does nothing, do you also mean that you are unable to make other commands in terminal? (as in if it is running a program)

or does it return "bash: nm-applet: command not found"

if the second one is true you have to install it again

---

### Post by wormser on 2008-03-11
I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. Right click on the menu Panel and click Add to Panel. If it still is not appearing then go to System> Preferences> Sessions. Look for Network Manager. Make sure it checked. If it not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

---

### Post by richard978 on 2008-03-11
> **glennric said:**
> Do you have the system tray on your panel?  Right click on the panel and select "Add to panel".  Then find the "Notification Area" applet and add that.  See if the network manager shows up then.

Thankyou that sorted it.....cheers. God knows how I removed that....couldn't work it out

---

### Post by wormser on 2008-03-11
> **richard978 said:**
> Thankyou that sorted it.....cheers. God knows how I removed that....couldn't work it out

Mark your thread as resolved and give thanks to the post that helped.  The thanks is a little star medal on each post in the lower right corner.  This makes it easier for people searching to find the post that solves it.

---

