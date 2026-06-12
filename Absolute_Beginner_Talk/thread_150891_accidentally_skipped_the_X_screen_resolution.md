---
title: "accidentally skipped the X screen resolution"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by ScottyI on 2006-03-26
screen. How can I add a few more resolutions (besides the defaults)?

---

### Post by Sutekh on 2006-03-26
Use this command
```
sudo dpkg-reconfigure xserver-xorg
```
You will get asked heaps of questions about keyboard/mouse and monitor.  Use the default/suggested values if you are unsure.  You will get the opportunity to choose which resolutions you want.

---

### Post by ScottyI on 2006-03-26
thanks, im at the part where i need to chose the resolutions... How the heck do i select them? thanks, alot

never mind, <space>...doh!

---

### Post by Sutekh on 2006-03-26
With the arrow keys (to move) and the space bar (to select)

---

### Post by ScottyI on 2006-03-26
I chose all of the default options and selected the resolutions, and rebooted, but the same resolutions appear. any suggestions?

---

### Post by Sutekh on 2006-03-26
What resolutions did you try to select?  What is the maximum resolution of your monitor?

---

### Post by ScottyI on 2006-03-26
in XP i was running 1680x1050 which seems to be the only resolution that doesnt look a bit 'off' on this dell lcd. the greatest res i can select is 1024x768

---

### Post by Sutekh on 2006-03-26
Ok that's pretty wierd.  I have never had that problem with reconfiguring the X server.

You may have to do some manual hacking of the xorg configuration file.

Have a read of this HOWTO (at the custom modeline part)

[Ubuntu Forums - HOWTO change resolution/refresh rate in Xorg - by](http://ubuntuforums.org/showthread.php?p=454217)[heimo](http://ubuntuforums.org/member.php?u=13183)

---

### Post by henriquemaia on 2006-03-26
Try setting the exact refresh rate for your monitor. 

If your monitor's best resolution is 1680x1050@85hz, read this [thread]("http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate") how to get that. I had success on my TFT monitor with that.

---

### Post by Sutekh on 2006-03-26
[QUOTE=henriquemaia]Try setting the exact refresh rate for your monitor. 

If your monitor's best resolution is 1680x1050@85hz, read this [thread]("http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate") how to get that. I had success on my TFT monitor with that.[/QUOTE]
Hey we posted the same link, but they have different thread numbers.  Wierd!

---

### Post by henriquemaia on 2006-03-26
I did a search for it, opened the link and copy/pasted here. I believe that's why it has "highlight=refresh+rate" at the end of it (those were my search terms).

Not sure, though.

---

### Post by ScottyI on 2006-03-26
what the heck? I just rebooted once again, and Im off and running at 1680x1050! albeit at 60Hz. Atyll work though. :D 

thanks for the help guys. Ill have to experiment a bit more and figure out why it wasnt working.

---

### Post by Sutekh on 2006-03-26
[QUOTE=ScottyI]what the heck? I just rebooted once again, and Im off and running at 1680x1050! albeit at 60Hz. Atyll work though. :D 

thanks for the help guys. Ill have to experiment a bit more and figure out why it wasnt working.[/QUOTE]

Actually I can tell you why.  It was because you changed it while X was running.

The proper way (as I should have said to you) is to stop X first.  

You change to a virtual console, by pressing Alt+Ctrl+F1 and log in.  Then stop X by stopping the GNOME display manager (GDM) using
```
sudo /etc/init.d/gdm stop
```
Then reconfigure the X server
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart the GDM and X using
```
sudo /etc/init.d/gdm start
```


You could also achieve this by pressing Ctrl+Alt+Backspace (after reconfiguring the X server) to restart the GDM or reboot, as you did.

---

### Post by BoneKracker on 2006-03-27
man xorg.conf

then you can tweak the monitor and screen settings to your heart's content

---

### Post by ScottyI on 2006-03-27
[QUOTE=Sutekh]Actually I can tell you why.  It was because you changed it while X was running.

The proper way (as I should have said to you) is to stop X first.  

You change to a virtual console, by pressing Alt+Ctrl+F1 and log in.  Then stop X by stopping the GNOME display manager (GDM) using
```
sudo /etc/init.d/gdm stop
```
Then reconfigure the X server
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart the GDM and X using
```
sudo /etc/init.d/gdm start
```


You could also achieve this by pressing Ctrl+Alt+Backspace (after reconfiguring the X server) to restart the GDM or reboot, as you did.[/QUOTE]

Thanks for the explanation. Good info.

---

