---
title: "No shutdown or reboot button"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by patik on 2007-03-13
I am running a clean install of Edgy with Nvidia drivers (no Beryl or anything fancy/beta) and I do not have shutdown or reboot buttons on the shutdown screen (when you click on the Quit icon in the far corner). I have installed kde-desktop but I use gnome. My only option is to logout, then click shutdown from the session options which works fine.

I previously had Feisty on another disk/partition and it had those buttons. Any idea how to get them back, or are they just not included in Edgy? 

Alternatively, is there a command that cleanly shuts down? I tried "sudo shutdown" with some flag (-s?) and it immediately went black and shutdown, almost as if I had just pressed the power button.

---

### Post by jdfreshwater on 2007-03-13
I think your problem may be with your display manager of gdm or kdm.  It matters which of these is active to get all of the logout and shutdown stuff on your default desktop.  This means you may get these options in KDE, but not Gnome or the other way around.  You can always use

sudo shutdown (-r for reboot) (-h for shutdown) now

this will shutdown the system.

---

### Post by Sunflower1970 on 2007-03-13
This happened to me once. Freaked me out till I figured out what I did 

Go to System-->Administration-->Login Window. Look for something called the "Menu Bar" Make sure "Show Actions menu" is checked. If all goes well your shutdown and reboot button reappear.

---

### Post by patik on 2007-03-13
> **Sunflower1970 said:**
> Go to System-->Administration-->Login Window. Look for something called the "Menu Bar" Make sure "Show Actions menu" is checked. If all goes well your shutdown and reboot button reappear.

I tried this and it shows the "Starting Administrative Application" on the menu bar that lists open windows, but then it disappears. 

For clarification I have the button on the menu bar (see attachment) but the only options are Log Out, Lock Screen, Switch User, Suspend, and Hibernate. There's a bit of space between the last two which is where Shutdown and Reboot appeared on Feisty (can't take a screenshot of it unfortunately).

---

### Post by Sunflower1970 on 2007-03-13
Yeah. That's what happened to me. Missing the two buttons on the quit menu

Are you logged in as root instead of just a user? That might cause the Login Window not to appear....

---

### Post by x1a4 on 2007-03-13
Hi,

System -> Preferences -> Session 

check [Ask on Logout]

---

### Post by patik on 2007-03-13
> **x1a4 said:**
> Hi,

System -> Preferences -> Session 

check [Ask on Logout]

It was already checked.  :( 

And I am not logged in as root, I'm the user that I was asked to create during installation.

---

### Post by Mohammad_Khalid_Hussain on 2007-03-13
Hey i have this so called 'problem'. I am running Beryl (therefore a different window manager?). I had this on the first day but then they seemed to have disappeared(Its my third day now). What I do now is to Log Out then choose to Shutdown from the login screen.

I will try the option suggested above and see if it helps.
Thanx.

Hope it gets Solved .

---

### Post by Najand on 2007-03-13
Seems like an XGL Startup problem, try to startup xgl  using:
```

/usr/bin/Xgl :0 -fp /usr/share/fonts/X11/misc -fullscreen -ac -accel glx:pbuffer -accel xv:fbo:0

```

---

### Post by Mohammad_Khalid_Hussain on 2007-03-13
What exactly do i do with it?

I am sorry, But I dont know what to do with it.

Help me pls.

---

