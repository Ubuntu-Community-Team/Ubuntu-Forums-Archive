---
title: "Need help with WICD installation"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Helven Ink on 2008-01-22
I can't get WICD to install, it gives me an error message of conflicts with network manager. If I uninstall network manager, it still gives me the same error, only then I can't reinstall network manager... ...which I guess isn't incredibly important because I can't get online in the first place. WICD was suggested as a fix for my intel3945 wifi card, so I d/led the .deb, and copied to my laptop. I'm running ubuntu 7.10

I've seen 2 threads about this, but it's like all the help was deleted, and all that's left is the question, and the admission of "Thanks, that worked"... =p

which leaves me kind of stumped.

  Please help!

---

### Post by zabien1970 on 2008-01-22
Not sure how you're doing all this but try the commands in this link if they're different than yours 
[http://www.ossgeeks.co.uk/?p=166](http://www.ossgeeks.co.uk/?p=166)

---

### Post by sheki1 on 2008-02-02
that link doesn't work...

am having the same problem...  and I don't know how to uninstall the network manager...

please HELP!

---

### Post by RomeReactor on 2008-02-02
Hi. If you want to uninstall network manager to install WICD, then search for **network-manager** and **network-manager-gnome** in Synaptic (System->Administration->Synaptic) and mark them for removal; or to do it from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude remove network-manager network-manager-gnome
```
Then try installing WICD.

---

### Post by AdemoS on 2008-02-02
*EDIT: Ah, RomeReactor beat me! Well, you can still use my instructions if you get stuck somewhere.*


Since I'm using WICD, so you can try what I did.



**Removing Network Manager and Installing Wicd**

System / Administration / Software Sources

Choose the "Third Party Software" tab

Click "Add" and copy paste this:
> deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras

Next you want to install it.

System / Administration / Synaptic Package Manager

Click "Search"

Type in:
> wicd

Click the check on the only package that comes up

Click "apply"

It should ask to remove NetworkManager and Install Wicd.



Now, thanks to great thinking by the Apt-Get people, it will download Wicd BEFORE you lose your internet connection. (by removing NetworkManager)

Then, after Wicd is downloaded, and NetworkManager removed, it will install the files for Wicd.




[COLOR="Green"]**Optional Step:**[/COLOR]

In order to get the Wicd tray each time you start up, you have add the following:

System / Preferences / Sessions

In the Startup Programs Tab:

Click "Add"

Name: Wicd (or whatever makes sense to you)
Command: /opt/wicd/tray.py

Now you'll always have a tray!


Enjoy Wicd, I found it much smarter and more stable then NetworkManager.

---

### Post by Paris Heng on 2008-02-02
Yes thanx, I also wonder why it having problem with Madwifi, so I uninstall the network manager and try a network manager name WICD. It look ok for me right now.

For somebody there facing the problem like me, please visit the following:

Installation on WICD:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by sheki1 on 2008-02-02
hi, I've tried following all these steps ansd still cannot get WICD to work...

I was able to uninstall network manager and install wicd.

Now I've got no idea how o run it, how to access it, or how to do anything with it. When I go to network, it stll doesn't show wireless.

I can't do those wget command or add repos since I cannot access the wireless network.

---

### Post by Steven_B on 2008-02-02
You can start WICD with:
```
python /opt/wicd/gui.py
```

You can start the tray applet each time you login by going to
Sytem>Preferences>Sessions, and adding
```
python /opt/wicd/tray.py
```

---

