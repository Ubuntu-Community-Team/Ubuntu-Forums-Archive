---
title: "I need a WIFI app (urgent)"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-15
I have xubuntu installed. I used to have ubuntu and loved the wifi app in ubuntu.. That is exactly what I need, with signal strength, the diff wireless networks, and an easy way to put in the wep key. I don't believe xubuntu has one pre-installed (or does it?). Also I was hoping it would display in the top right corner, just like in the one in ubuntu? (I have gone to Applications>system>network, but that is too complicated for me and it doesn't scan the networks)

Anyone have something similar for XUBUNTU? I am in a hurry - so please reply ASAP!

(I tried wifi-radar - it didn't cut it :))




(also - I used to have ubuntu installed, and just did a sudo code to download xubuntu, will it slow down my pc if I never uninstall ubuntu and just keep them both? - not a high priority question, but the above one is!)

---

### Post by ugm6hr on 2007-06-15
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

If you installed Xubuntu from Ubuntu, Network Manager (the one you talk about) is already on your computer.  The link above tells how to install it.  But for you, you should just have to add the following to your autostarted applications:

nm-applet --sm-disable

Then reboot.

---

### Post by jimbob on 2007-06-15
Try Wicd - I personally think it is much better than Wifi-radar.

   [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by ajskhan on 2007-06-15
AHHHH! I put that in the terminal, and I rebooted and now I cannot see the two bars (one that shows which programs are open, and the other that is on the top that holds the system button) HELP!!!

BUT TERMINAL DOES SHOW! please help ASAPASAPASAP

---

### Post by ajskhan on 2007-06-15
> **ajskhan said:**
> AHHHH! I put that in the terminal, and I rebooted and now I cannot see the two bars (one that shows which programs are open, and the other that is on the top that holds the system button) HELP!!!

BUT TERMINAL DOES SHOW! please help ASAPASAPASAP
bump, very urgent~

is there any command to undo what I did last?!?!?! hurry

---

### Post by ugm6hr on 2007-06-16
> **ajskhan said:**
> bump, very urgent~

is there any command to undo what I did last?!?!?! hurry

Sorry - wasn't expecting that.  Have you tried restarting?  Bizarre that it's removed sys-tray.  If that doesn't work - to add a System Tray

Right click on the top panel -> Add New Item -> System Tray

That should give you a new tray.

To run the Network Manager applet - from Terminal:
```
nm-applet
```

The other entry is really for the startup options to ensure you only get 1 applet in the tray.

Sorry again.

---

### Post by ajskhan on 2007-06-16
I don't have a top panel, or bottom panel!

---

### Post by ugm6hr on 2007-06-16
> **ajskhan said:**
> I don't have a top panel, or bottom panel!

Sorry - misunderstood you again.  Just to check - you currently have the standard Xubuntu desktop background (pale blue) with a few desktop icons (your hard drive etc) on it, but no panels top and bottom. 

To bring back the panels:
```
xfce4-panel
```
This should bring up the panels.  But they may disappear when you close the Terminal again.  But it should at least allow you to edit the panel preferences.  If that doesn't work, try:
```
xfce4-panel &
```
Everything should be back where they should be then.  When I restart, I always tick the "Save session for future logins" box - altho not sure if that's necessary.
You can also just use Thunar File Manager and go to /usr/bin/xfce4-panel and double-click.

Hopefully, this should solve the panels problem, and then to check if NM is running:
```
xfce4-taskmanager
```
Look for *nm-applet* - if it's running, then the following command will give you more than 1 icon.
```
nm-applet
```
Should run NM (but may give you multiple NM applet icons in systray from previous experience).  And the other command given previously should remove multiple icons if you put it in the startup programs (although I managed to do it by uninstalling / reinstalling NM - as per my previously linked post).

Hope that helps sort your problems.

---

### Post by ajskhan on 2007-06-16
> **ugm6hr said:**
> Sorry - misunderstood you again.  Just to check - you currently have the standard Xubuntu desktop background (pale blue) with a few desktop icons (your hard drive etc) on it, but no panels top and bottom.  [COLOR="Red"]yes same background and everything, haven't messed with anything
[/COLOR]
To bring back the panels:
```
xfce4-panel
```[COLOR="Red"] - did that and it did disappear when I closed the terminal but it did come up[/COLOR]
This should bring up the panels.  But they may disappear when you close the Terminal again.  But it should at least allow you to edit the panel preferences. [COLOR="Red"](what do I do with the prefs?)[/COLOR] If that doesn't work, try:
```
xfce4-panel &
``` [COLOR="Red"]- did that, closed terminal, and they disappeared again?![/COLOR]
Everything should be back where they should be then.  When I restart, I always tick the "Save session for future logins" box - altho not sure if that's necessary.
You can also just use Thunar File Manager and go to /usr/bin/xfce4-panel and double-click.

Hopefully, this should solve the panels problem, and then to check if NM is running:
```
xfce4-taskmanager
``` [COLOR="Red"]first need panels back - permanently, then I will try this stuff!  thanks[/COLOR]
Look for *nm-applet* - if it's running, then the following command will give you more than 1 icon.
```
nm-applet
```
Should run NM (but may give you multiple NM applet icons in systray from previous experience).  And the other command given previously should remove multiple icons if you put it in the startup programs (although I managed to do it by uninstalling / reinstalling NM - as per my previously linked post).

Hope that helps sort your problems.



see above in red

---

### Post by ajskhan on 2007-06-16
just wanted to bump

---

### Post by ugm6hr on 2007-06-16
Couple of options:
Try double-click from Thunar (/usr/bin/xfce4-panel)
Then Shut-down, and ensure the "Save session for future logins" is ticked.
Hopefully, the panels should appear when you boot back up again.

If that doesn't work, you can add xfce4-panel to start-up apps:
Applications->Settings->Autostarted Applications
Add
Name: Panel / Command: xfce4-panel &

This has been tried by someone else:
[http://ubuntuforums.org/showthread.php?t=467995&highlight=xfce4-panel](http://ubuntuforums.org/showthread.php?t=467995&highlight=xfce4-panel)

---

### Post by ajskhan on 2007-06-16
ok, and where exactly do I click save session for future logins?

---

### Post by ugm6hr on 2007-06-16
> **ajskhan said:**
> ok, and where exactly do I click save session for future logins?

With the panels present. click on the top right "Quit" - this should bring up an option box - with Switch User, Logout, Restart, Shutdown etc...

In that box, there is a small tick-box option that says "Save session..."

---

### Post by ajskhan on 2007-06-16
cool, fixed - now still need that wifi app :)
btw i am missing the little bottom right icons that let u have like 4 desktops

---

### Post by ugm6hr on 2007-06-16
> **ajskhan said:**
> btw i am missing the little bottom right icons that let u have like 4 desktops

Right-click the bottom panel:
Add New Item
Pager

Should appear.

If you can still trust me - try the advice given re: nm-applet

PS: If you're looking for an Xubuntu wifi app - Wicd is probably a better fit (NM is GNOME dependent).  But if NM is already installed (from Ubuntu) - give it a try.

---

### Post by ajskhan on 2007-06-16
ok, so there is no nm-applet in taskmanager

---

### Post by ugm6hr on 2007-06-16
> **ajskhan said:**
> ok, so there is no nm-applet in taskmanager

```
nm-applet
```

---

### Post by ajskhan on 2007-06-16
Cool! But will it start every time I boot up?

---

### Post by ugm6hr on 2007-06-17
> **ajskhan said:**
> Cool! But will it start every time I boot up?

It should.  Just give it a try!  If it doesn't - post again.

This link is helpful:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

---

### Post by ajskhan on 2007-06-17
Awesome thanks!

---

