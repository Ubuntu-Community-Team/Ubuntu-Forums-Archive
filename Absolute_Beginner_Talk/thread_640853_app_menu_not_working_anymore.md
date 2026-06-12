---
title: "app menu not working anymore"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by dusko24 on 2007-12-14
hi guys

 my application menu stopped working....places, system menu is fine, only application wont respond at all...I tried to edit it with right click, no response. I also tried to start main menu through system-settings-main menu.nothing. doesnt even show up. I was advised to remove gnome settings with   rm -rf  .gconf .gconfd .gnome .gnome2  no change at all...any help please? I know that I can start applications with alt+f2 but it would be nice to have that menu back and working.
thx

---

### Post by Bruce M. on 2007-12-14
> **dusko24 said:**
> hi guys

 my application menu stopped working....places, system menu is fine, only application wont respond at all...I tried to edit it with right click, no response. I also tried to start main menu through system-settings-main menu.nothing. doesnt even show up. I was advised to remove gnome settings with   rm -rf  .gconf .gconfd .gnome .gnome2  no change at all...any help please? I know that I can start applications with alt+f2 but it would be nice to have that menu back and working.
thx


Who advised you to use that command?

Too late, he went offline (23:40 GMT)

---

### Post by Sef on 2007-12-14
Try this to reinstall Ubuntu's desktop:

Alt +  F2 > gnome-terminal

```
sudo apt-get install ubuntu-desktop
```

---

### Post by coolen on 2007-12-14
The command you were advised to run erased some rather important configuration files, including those which are used to populate your Applications menu.
It should be possible to get your default menu and settings back. Sef's suggestion seems a good place to start, but further help is available if required.
Please let us know who told you to run that command immediately. They will be banned.
That is assuming it was on the forums, of course.

---

### Post by dusko24 on 2007-12-14
ok i'll try it and will let you know, thanks

---

### Post by dusko24 on 2007-12-14
well, I was looking on the net to find solution and found this guy who had almost same problem and so I tried to do the same thing what he was advised....[http://www.uluga.ubuntuforums.org/showthread.php?t=635108](http://www.uluga.ubuntuforums.org/showthread.php?t=635108)

so I think it was MY stupidity to try things without asking first but I really do not like people to bother....don't ban him:-)

---

### Post by dusko24 on 2007-12-14
i tried to reinstall as advised but unfortunately no change....maybe any other suggestions?

---

### Post by dusko24 on 2007-12-15
anybody??

---

### Post by Sef on 2007-12-17
From the Terminal have you tried

```
sudo apt-get install .gconf .gconfd .gnome .gnome2 
```?

---

### Post by macogw on 2007-12-17
> **Sef said:**
> From the Terminal have you tried

```
sudo apt-get install .gconf .gconfd .gnome .gnome2 
```?

I'm pretty sure that's not possible.

Try creating another user and then log in as that user.  Open a terminal as that user and do "sudo nautilus" then in there go to View -> Hidden Files and copy those 4 things from that user's home drive to yours.  then back to the terminal and do "cd /home/yourusername" then "sudo chown yourusername:yourusername .gconf" and repeat for each of those files so then you have the default config files in your home directory.  Yes, your username goes twice with a : in between.  That sets the owner (chown= CHange OWNer) and group to your user.

---

