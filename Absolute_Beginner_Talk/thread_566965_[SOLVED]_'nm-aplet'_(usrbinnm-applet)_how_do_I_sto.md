---
title: "[SOLVED] 'nm-aplet' (usr/bin/nm-applet) how do I stop it from asking me for password?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-10-04
sorry if I'm being stupid, as my last post has remained unanswered 4 days now,can someone please tell me why 

'nm-applet' (usr/bin/nm-applet) 

asks me for a password each time I log on to my PC and want a wireless connection, worse even it does that almost every hour, I have told it once the WPA key, so can't the bloody thing just remember it?

**my last post here with screenshots:**
[http://ubuntuforums.org/showthread.php?t=563106](http://ubuntuforums.org/showthread.php?t=563106)

and another similar issue here unanswered since November 5th, 2006 from user "SendDerek":
[http://ubuntuforums.org/showthread.php?t=293987](http://ubuntuforums.org/showthread.php?t=293987)

I just want to turn on my PC it should simply just connect without giving me any headaches, is this possible, please.

---

### Post by cvaty on 2007-10-04
theres a lot of so called solutions listed here in the forums, just do a search with keywords nm_applet, keyring. 

 i found  however that none of them worked for me... so i got rid of the default gnome network manager and installed wicd.  no more keyring b.s.

---

### Post by cvaty on 2007-10-04
if you want to go through with my idea heres the site:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

download the .deb
try to install, remove the network-manager as it will instruct you
try to install again.

  the defualt icons are a bit ugly in my opinion.  i've attached a replacement set i found somewhere along the way

icons go in opt/wicd/images/

---

### Post by MozartlovesUbun2 on 2007-10-04
> **cvaty said:**
> theres a lot of so called solutions listed here in the forums, just do a search with keywords nm_applet, keyring. 

 i found  however that none of them worked for me... so i got rid of the default gnome network manager and installed wicd.  no more keyring b.s.

Ok, prior to posting I did do a search for "nm_applet, keyring"
The only result that shows up is this one here and it still doesn't give any solutions.

[http://ubuntuforums.org/showthread.php?t=474126&highlight=nm_applet+keyring](http://ubuntuforums.org/showthread.php?t=474126&highlight=nm_applet+keyring)

==============

ok i did try a search with just the word"Keyring" which brings up 250 results, not all related to this problem though
this one here might be worth reading, its a post from last year

[http://ubuntuforums.org/showthread.php?t=187874&highlight=keyring](http://ubuntuforums.org/showthread.php?t=187874&highlight=keyring)

if this irritating keyring doesn't work, whats the need of it and why is it still here, or not fixed? been over a year now.

anyway as far as I could make of it seems to be a bug and I guess it's not fixed in Gutsy either

[http://bugzilla.gnome.org/show_bug.cgi?id=444607](http://bugzilla.gnome.org/show_bug.cgi?id=444607)

---

### Post by ronmarley1 on 2007-10-04
Pam keyring manager will allow you not have to keep typing in your keyring password.  I have not used it, so I cannot attest to the usability.
Additionally, I just installed Gutsy beta, and the new keyring manager (new version of gnome) has a check box to remember the password, and that works for me.

---

### Post by notwen on 2007-10-04
Unfortunately, the current NM in Feisty will never remember your keyring pass, unless you install PAM keyring manager(how-to [here]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/")).  You could also wait until Gutsy's release where they have fixed this in the NM keyring.  Hope this helps. =]

---

### Post by MozartlovesUbun2 on 2007-10-04
> **notwen said:**
> Unfortunately, the current NM in Feisty will never remember your keyring pass, unless you install PAM keyring manager(how-to [here]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/")).  You could also wait until Gutsy's release where they have fixed this in the NM keyring.  Hope this helps. =]

OK, I hope so too, but I just read some where in one of the 100 tabs I have open looking into this issue, that the bug hasn't been resolved in Gutsy, :-(

---

### Post by ronmarley1 on 2007-10-04
> **MozartlovesUbun2 said:**
> OK, I hope so too, but I just read some where in one of the 100 tabs I have open looking into this issue, that the bug hasn't been resolved in Gutsy, :-(

The only thing that I can share is that it works for me in Gutsy.  
In a side not, it's not really an Ubuntu issue, but a Gnome issue.  The keyring manager is a part of Gnome.  The reason that it'll save the password in Gutsy is that Gutsy uses a newer version of Gnome that Feisty does.
Good luck with Pam, if you try it.  This issue bugged me also, but after reading the numerous threads on it, and all the issues people had, I decided to just put up with it until Gutsy came out with the new Gnome.

---

### Post by notwen on 2007-10-04
Yes the issue should be resolved in GNOME 2.20 which will be included w/ Gutsy later this month. =]

---

### Post by MozartlovesUbun2 on 2007-10-05
> **ronmarley1 said:**
> The only thing that I can share is that it works for me in Gutsy.  
In a side not, it's not really an Ubuntu issue, but a Gnome issue.  The keyring manager is a part of Gnome.  The reason that it'll save the password in Gutsy is that Gutsy uses a newer version of Gnome that Feisty does.
Good luck with Pam, if you try it.  This issue bugged me also, but after reading the numerous threads on it, and all the issues people had, I decided to just put up with it until Gutsy came out with the new Gnome.

ok thats cool then, well I won't go rushing into Beta Gutsy now for the laptop, for testing the home PC has been running smoothly on Gutsy Beta since three days, so I'll wait for the final version.
thanks

---

### Post by BrendanM on 2007-10-05
I second the suggestion for WICD. WICD is amazing. By far the best network-mangement utility I've seen for Ubuntu. I don't know why they don't make it the default.

---

### Post by MozartlovesUbun2 on 2007-10-07
> **BrendanM said:**
> I second the suggestion for WICD. WICD is amazing. By far the best network-mangement utility I've seen for Ubuntu. I don't know why they don't make it the default.

WICD what, where is it? can't find it in synaptics!

---

### Post by ronmarley1 on 2007-10-08
> **MozartlovesUbun2 said:**
> WICD what, where is it? can't find it in synaptics!

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
They even have instructions on installing it in Ubuntu.

---

### Post by MozartlovesUbun2 on 2007-10-10
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
==============================

**Installing Wicd in Ubuntu**

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras 

where feisty is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For a command, enter "/opt/Wicd/tray.py". In KDE, run the following command from a terminal:

    sudo ln -s /opt/wicd/tray.py ~/.kde/Autostart/tray.py

You can open the main window by left clicking on the tray.

---

