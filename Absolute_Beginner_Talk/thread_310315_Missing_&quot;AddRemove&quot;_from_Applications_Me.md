---
title: "Missing &quot;Add/Remove&quot; from Applications Menu"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Literatka on 2006-12-01
I don't know what happened but some how I lost my add/remove programs from my  "applications" menu and can't seem to figure out how to restore it. 

Jessica

---

### Post by Sef on 2006-12-01
System > Preferences > Menu Layout   Just find Add/Remove and click on it.

---

### Post by aysiu on 2006-12-01
If, for some reason, you can't find it, you can add it and use the command ```
gksudo gnome-app-install
``` for the new menu item.

---

### Post by Literatka on 2006-12-01
That didn't work :( 

It's not in the menu section to add on and the terminal code didn't work either :(

---

### Post by aysiu on 2006-12-01
> **Literatka said:**
> That didn't work :( 

It's not in the menu section to add on and the terminal code didn't work either :(
Then paste this into the terminal: ```
sudo aptitude update && sudo aptitude install gnome-app-install gksu
```

---

### Post by Literatka on 2006-12-01
Thank you :)

---

### Post by Cannaregio on 2006-12-14
> **aysiu said:**
> Then paste this into the terminal: ```
sudo aptitude update && sudo aptitude install gnome-app-install gksu
```

I have since two days (new update?) the same problem, but in my case your solution did not work:

```

...Fetched 6B in 0s (12B/s) 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for gnome-app-install
The following packages have been kept back:
  gnome-applets gnome-applets-data gnome-netstatus-applet gnome-panel 
  gnome-panel-data gnome-system-tools libpanel-applet2-0 
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by Cannaregio on 2006-12-14
Ok, I found a solution. Now the Add/Remove reappeared

For what is worth you can try it as well. Anyway it worked for me.
Clearly I did add something non kosher to my list :-)

1) replace whatever you did put in your sources.list with the following (after having made a copy of it, of course), this sources.list comes from [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")...

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen
```

2)
Run 
```
sudo apt-get update
sudo apt-get upgrade
```

3)
Run
```
sudo apt-get install gnome-app-install
```


Voilà :-)

---

### Post by Orwell on 2006-12-15
As always, thanks for the tip. Here I was thinking I was the only schmuck who could make his Add/Remove disappear. Thanks guys.

---

