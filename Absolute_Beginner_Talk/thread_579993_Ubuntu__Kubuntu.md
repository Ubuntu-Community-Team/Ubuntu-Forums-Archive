---
title: "Ubuntu / Kubuntu"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by benjr06 on 2007-10-18
Hello all.

I'm a Gutsy user.  I read in the help page(ubuntutokubuntu) that I can install Kubuntu through Synaptic.   I'd like to try out Kubuntu to try and get my wife hooked, but if its not to my particular tastes, I'd like to still have Ubuntu for myself.

Did I read correctly when it says that I can switch between my normal Ubuntu session and a Kubuntu session when I reboot?


Thanks,

BenJr06

---

### Post by p_quarles on 2007-10-18
You read correctly. At the login screen, select the "session" option, and it will give you a list of available environments.

---

### Post by rsambuca on 2007-10-18
You don't even need to reboot.  You can just logout and make the change.

---

### Post by benjr06 on 2007-10-18
Wow!  I really like communities where you can get answers within two minutes of posting.  Were you all just perusing the forums or is there some other way to see new posts as they are posted?

Anyway, thanks again for the information.

On another note.  Is there a viable way to listen to Yahoo Music using Ubuntu/Kubuntu?  My wife really want to listen but sadly discovered that she couldn't when trying to get it to work in Ubuntu-Feisty.

---

### Post by benjr06 on 2007-10-19
> **p_quarles said:**
> You read correctly. At the login screen, select the "session" option, and it will give you a list of available environments.

Hi.  I was able to get Kubuntu installed without issue.  During setup, it asked me which environment I wanted as default.  I chose GDM for Gnome since I didn't know how KDE would work out.  Now, I do not know how to get the KDM to load.  When I reboot or logoff or change user, I'm always sent to Ubuntu's login screen, I don't get an option as mentioned.  I'm still new to Linux world, so I'm sure its something simple I'm not doing.  

Anyone have simple steps I can take to get this working?

Thanks in advance.

---

### Post by p_quarles on 2007-10-19
Switching desktop managers isn't necessary if you just want to switch between the window managers. The "sessions" menu in the login screen will allow you to select either KDE or Gnome, but it doesn't actually change the DM, just the environment. Are you not getting that option? What comes up when you click on the sessions button?

Anyway, switching DMs is straightforward, but probably isn't something you'll want to do every day. Two ways to do it:
```
sudo dpkg-reconfigure gdm *(or kdm*)
```
This will bring up the dialogue asking which one you want to make default. 

Or you can edit the /etc/X11/default-display-manager file, and change the end either to gdm or kdm. 

Whichever method you use, getting it to take effect requires an extra step. First, log out of the current desktop. In the login screen, select "system options" (exact title varies), and choose "Restart X." Then you're set.

---

### Post by benjr06 on 2007-10-19
> **p_quarles said:**
> Switching desktop managers isn't necessary if you just want to switch between the window managers. The "sessions" menu in the login screen will allow you to select either KDE or Gnome, but it doesn't actually change the DM, just the environment. Are you not getting that option? What comes up when you click on the sessions button?


I don't see any options when the login screen appears.  It simply says UserName.  Maybe I'm overlooking something.  I'll try the rest later when I'm in front of that computer.

---

### Post by bodhi.zazen on 2007-10-19
Even better (my wife and I have the same issue), you can each have your own desktop *without logging each other out*

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

This is what we do in our hourse, it does not eat up all that much in terms of overall performance. If you are worried 'bout security lock the desktop.

---

### Post by rsambuca on 2007-10-19
> **benjr06 said:**
> I don't see any options when the login screen appears.  It simply says UserName.  Maybe I'm overlooking something.  I'll try the rest later when I'm in front of that computer.

In the bottom left hand corner of the login screen there is an "Options" selection.  Click on it and select "Sessions".  You will have a choice between gnome or kde.

---

### Post by benjr06 on 2007-10-19
I was able to change my environment with the help from you guys.


Thanks for the information.

---

