---
title: "System-&gt;Quit -- Missing Shutdown Option"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-07-03
When I select System->Quit I am presented with a popup box with the following options:

Log Out
Lock Screen Switch User
Suspend
Hibernate

Isnt there suppose to be a Shut Down Option???

To shutdown Ive been using 
sudo shutdown -h now
at command line (which isnt bad)

however I believe there should be a shutdown option.  Or is this the only options associated with Feisty?

---

### Post by lisati on 2007-07-03
Yes - there normally is a "Shutdown" option. The only time I haven't had it is when I've logged in as a user on my Desktop from my laptop and then logged out.

Suggestions anyone?

---

### Post by kevdog on 2007-07-03
Any other ideas??

---

### Post by UJoe4 on 2007-07-03
I'd also be interested in the answer to this. I have a Kubuntu (KDE) installation and installed GNOME and Xfce as additional desktop choices. When I'm using KDE or Xfce the "Quit" options include Shutdown and Restart, but when I'm using GNOME they don't.

I had thought that might be because I'm still using the KDE display manager to log in and choose my session instead of the GNOME one, so GNOME only wants to log me back out to the KDM login screen rather than shutting down entirely... does that make any sense?

But if you only have GNOME installed and are still missing these options, I have no idea.

---

### Post by kevdog on 2007-07-03
Maybe thats the answer.  I have all three desktop installed - K, U, X and use the Kubuntu login screen.  (Can this be changed to the Gnome login screen -- I guess it really doesn't matter).

I originally installed them in this order
Ubuntu
Kubuntu
Xfce

---

### Post by UJoe4 on 2007-07-03
> Can this be changed to the Gnome login screen
According to some other threads, this might work:

sudo dpkg-reconfigure gdm

If this works and you get the Shutdown and Restart options back in GNOME, let us know whether the reverse is also true: Are those options now gone from KDE? And are they still there in Xfce?

---

### Post by K_Soze on 2007-07-15
> **UJoe4 said:**
> According to some other threads, this might work:

sudo dpkg-reconfigure gdm

If this works and you get the Shutdown and Restart options back in GNOME, let us know whether the reverse is also true: Are those options now gone from KDE? And are they still there in Xfce?

This worked great for me. I can switch back and forth from gdm to kde. In gdm the buttons are back but it doesn't get them back in kde.

Oh well, I'd rather have the shutdown and restart buttons.

thanks a million......:guitar:

---

