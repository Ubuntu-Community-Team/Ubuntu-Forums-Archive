---
title: "Where'd my notification go ??"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-04-27
Why did my yello-orange starburst ,to notify me of updates, disappear.  I don't get it when I have updates to download ??
Thanks ; )

---

### Post by LuisGMarine on 2007-04-27
The ' yello-orange starburst' only becomes available in your taskbar when there are updates to download.  If some some unknown reason it goes away and you don't get your updates, you can manually update by doing such:

Open up a terminal windows and type in the following:
```
sudo apt-get update
```

After that run:
```
sudo apt-get dist-upgrade
```

some people would say do this code instead, to me its almost the same but I could be wrong.
```
sudo apt-get upgrade
```

The first command updates your repo's and checks the versions of your packages against the ones on the server.  If they all match , then obviously you have no update, but if they don't match then most likely you will have to update, which is what the 2nd and 3rd command do.

Good Luck

-LuisGMarine

---

### Post by ajmorris on 2007-04-27
> **MrKlean said:**
> Why did my yello-orange starburst ,to notify me of updates, disappear.  I don't get it when I have updates to download ??
Thanks ; )

somehow your checkbox was from the icon in the system tray called "show notifications", to re-enable try pressing "Alt + F2" then typing in the dialog box, update-manager. This brings up the adept update manager, then the icon should be in the system tray. Right click on it (even if it is grey) and check the show notifications, and also go to preferences and then the update tab and select to check for updates. This should do the trick ;)

---

### Post by MrKlean on 2007-04-28
Thanks for the help, but none of those worked ; (  I'll keep looking ; )

---

### Post by Unconscious on 2007-04-28
Yeah, I have the same problem. When I run the update-manager from Alt-F2, sometimes it works, sometimes it doesn't. I usually have to run it two or three times, then I get truckloads of updates. Right click doesn't work, in the bottom panel, and there is no icon on the top panel.

...and what are people referring to when they talk about the system tray? Last I checked Ubuntu is not Windows.

---

