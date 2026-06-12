---
title: "CD label maker program"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by peatrap on 2007-11-17
Can anyone point me in the right direction for a CD label maker program for Ubuntu.
   
                                           Thanks

---

### Post by skyjacker on 2007-11-17
> **peatrap said:**
> Can anyone point me in the right direction for a CD label maker program for Ubuntu.
   
                                           Thanks
See if this will work for you.:)  [http://glabels.sourceforge.net/](http://glabels.sourceforge.net/)

---

### Post by tyggna1 on 2007-11-17
[This thread ]("http://ubuntuforums.org/showthread.php?t=382137") has been immensely helpful to me when I'm looking for Linux software.   Kinda long, though.

---

### Post by ayenack on 2007-11-18
Open Synaptic and type cd label. There are a few that might be worth a go.

---

### Post by Dripbagulhos on 2007-11-18
Hello,

I used to use Kover ([http://42.fht-esslingen.de/kover/screenshots.php3](http://42.fht-esslingen.de/kover/screenshots.php3)) and Kover Artist ([http://www.kde-apps.org/content/show.php?content=38195](http://www.kde-apps.org/content/show.php?content=38195)). Both are made for KDE, but I still use Digikam and K3B, so I think there is no big deal on using another programa not built for Gnome.

---

### Post by peatrap on 2007-11-18
I have down loaded the  synaptic software, the download does not show up in applications even after a reboot.

---

### Post by ubuntu27 on 2007-11-18
> **peatrap said:**
> I have down loaded the  synaptic software, the download does not show up in applications even after a reboot.


install ** Debian Menu** which is a special menu that list EVERY installed application.

Install Debian menu:
```
sudo apt-get install menu
```

Restart Gnome Panel:
```
killall gnome-panel
```

Update application list in Debian Menu:
```
sudo update-menus
```


if that didn't work. Try Logging out and then log in again (Or just kill X by hitting  CTRL+ALT+BACKSPACE on your keyboard)

That didn't work either? Try the following

```
sudo dpkg-reconfigure menu
```

```
sudo dpkg-reconfigure menu-xdg
```

---

### Post by peatrap on 2007-11-18
The problem seems to be growing, tried down loading other programs from the channel and nothing will load. Time to wipe and reinstall, thanks for the help.
:(

---

### Post by ubuntu27 on 2007-11-19
> **peatrap said:**
> I have down loaded the  synaptic software, the download does not show up in applications even after a reboot.

> **peatrap said:**
> The problem seems to be growing, tried down loading other programs from the channel and nothing will load. Time to wipe and reinstall, thanks for the help.
:(


Wait. I am not sure what's going on here. You said that you "downloaded the synaptic software", What do you mean by that? 
Synaptic Package Manager is installed by default in Ubuntu. You do not need to download it and install it manually.

If you mean you used Synaptic to install some programs, what programs did you try to install?  Did you get some error?  There is always a solution to any problem. Re-installing the Operating System should be the last resort.  So tell us the problem and we will try to help you out :)

---

### Post by ayenack on 2007-11-19
I've just come back to this thread and I'm confused. If you downloaded software via Synaptic Package Manager (Top Menu Bar System>Administration>Synaptic_Package_Manager) then if the apps do not appear in Applications menu you will need to start them from terminal by typing the name of the app or do what ubuntu27 advised and install Debian Menu. To start apps from terminal.

Applications>Accessories>Terminal

Then

cd-circleprint (From command prompt)

This would start cd-circleprint if you installed it.

If you are getting error messages try this, open a terminal and type this at the command prompt.

sudo apt-get -f install

Until the errors stop.

You might be better of using Add/Remove in future as it automatically installs a startup icon to the correct menu bar or tells you how to start the app from terminal. This is probably what I should have advised from the off.

To use Add/Remove. Top menu. Applications>Add/Remove. This will open Add/Remove then top right corner of Add/Remove click on drop down menu next to Show and select All available applications. Then you can search for applications from the Search box and install them. Applications can also be un-installed using Add/Remove in the same way. In Add/Remove the only labeler I can find is gLabels using label as the search parameter.

---

### Post by peatrap on 2007-11-19
synaptic package manager was used to install

no errors

cd-circleprint from the terminal pulls up circle print

no errors

Applications does not show circle print as a download, does not show at all as a choice.
That is why I used the synaptic package manager.

---

### Post by ayenack on 2007-11-20
So you'll need to start the apps from Terminal if I'm understanding you correctly. Is this solved for you or do you still have issues?

---

### Post by jimrz on 2007-11-20
try launching circle print from the Deskbar app then, in future, each time you need it you can go to Deskbar > History and launch it from there

---

### Post by peatrap on 2007-11-21
I do not know what happened, it seemed that the more I used the system the slower it became
11-20-07 downloaded updates
turned computer off
when I turned it back on it will not proceed past the sign on and password page
freezes on  a nice tan page
Wiped the hard drive and reinstalled, works fine now.

---

