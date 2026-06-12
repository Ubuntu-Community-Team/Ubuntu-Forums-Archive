---
title: "networking icon missing"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by JoaoCarlosCorreia on 2007-11-08
Hi, I accidentally removed the networking icon from my toolbar. I tried to add it back with:
                - right click on the toolbar > Add to panel > network monitor
the icon is the same, but doesn't have the same features than before (can turn on/turn of network, can change DNS, etc)

How Can I restore my old network tool?

Thanks in Advance,


João

---

### Post by Schalken on 2007-11-08
I can't exactly remember what you have to run to get it back or how it is started when you login, but the network tool is called network-manager. Try doing Alt+F2 and running "nm-applet"...yeah, I think that's the one. :?

Hope this helps! :)

---

### Post by philinux on 2007-11-08
Have a look in prefs sessions and look through the start up list. Make sure network manager is ticked. How did you manage to remove it from the panel?

---

### Post by JoaoCarlosCorreia on 2007-11-08
That's it, the network manager!!!
in my sessions is ticked and run the command "nm-applet --sm-disable" as you guys said.
But i still don't have it...

---

### Post by philinux on 2007-11-08
you probably have but try rebooting.

---

### Post by philinux on 2007-11-08
If all else fails do this

reinstall the network-manager packages:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```

or do it from synaptic.

---

### Post by JoaoCarlosCorreia on 2007-11-08
I tried the reinstall but didn't solved my problem. 
I see the network-manager installed in the window add/remove programs. But I don't know how to launch it and I can't put it in my panel.

The most wierd is that I have another linux in other machine and the alt+F2 + nm-applet works perfectly and I have 2 icons working in my panel. In my ubuntu nothing happens...

---

### Post by philinux on 2007-11-08
In your original post you said accidentally removed it. 

Exactly how did you do this.

---

### Post by TadH on 2007-11-08
sudo apt-get remove network manager

then reinstall it and make sure its ticked under sessions from system>preference>session

---

### Post by Onesimus on 2007-11-08
I have had the same problem as yourselves.  Do not uninstall network-manager this just causes you to lose the network !

What is missing from the top panel is the notification area.  Right click in the top panel choose Add to Panel, then select the notification area.

The network icon, as well as battery icon (if you are on a laptop), and the OOo quickstarter icon reappears.

---

### Post by JoaoCarlosCorreia on 2007-11-09
Thanks a lot Onesimus!!!
That really solved my problem.
thanks everyone else that tried to help me

---

### Post by philinux on 2007-11-09
Can you explain how you managed to delete it from the panel in the first place because if you right click the network icon there is no remove from panel option :confused:

---

### Post by Onesimus on 2007-11-09
You can delete the notification area by right clicking on the two vertical dotted lines, that are to the left of the network icon.  This will delete area, and hence you are unable to see the network icon.

Simple really, but not particularly straight forward.  Why the network icon is in the notification area is rather strange ? Particularly as it is used for configuration rather than just notifying of activity.

---

### Post by JoaoCarlosCorreia on 2007-11-09
It's true, I guess I right click the notification area instead of the network manager icon.
Then I clicked in the "remove from panel", that I remember.

Anyway, thanks for your help guys

---

### Post by yellowbread on 2007-11-09
How fortuitous. Last light my kids managed to (apparently) remove the notification area from the panel. To disconnect my modem I had to kill pppd. Now I have it all back. Thanks. In the process, I found a way to remove the network manager icon from the notification area. Simply add a new notification area (which on my computer came up without the NM icon), then remove the notification area that has the NM icon in it.

---

