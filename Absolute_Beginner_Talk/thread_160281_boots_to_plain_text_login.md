---
title: "boots to plain text login"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-04-14
For no reason that I am aware of, my ubuntu now boots to a text login. It begins as normal, with the brown ubuntu logo, scrolling through the various services it is starting, then it jumps to 
mycomputer login:

I don't even know my password any more, however I know my superuser password.
Can I use this to log on? What name do I give? I have tried root and superuser, but they didn't work.

And when I reach the command line, how should I begin fixing the system?

---

### Post by az on 2006-04-14
If you can boot into recovery mode, type

dpkg-reconfigure xserver-xorg

if you cannot, boot to the command line and run
sudo dpkg-reconfigure xserver-xorg

---

### Post by aysiu on 2006-04-14
Try rebooting into recovery mode (second option, below the usual boot option and above "memtest"). This will have you logged in as root. After that try these options: ```
apt-get update
apt-get install ubuntu-desktop
/etc/init.d/gdm restart
```

---

### Post by Bloch on 2006-04-14
Actually, th only thing I remember doing was, I was trying out xkill on the command line. I typed xkill and with the skull & crossbones showing I tried to change desktop. This killed the bottom bar for a few moments, and when it came back the trash can was missing. So I clicked to log out and reboot.

---

### Post by Bloch on 2006-04-14
I think if I could get my username and password when I am logged in as root I could login again as myself. Somehow the automatic login to gdm has failed and I am sent to a text interface.

---

### Post by mrchrisblau on 2006-04-14
I assume you still are not in X, right?

If so (and also assuming you can log into root) you could type **adduser** and fill out all the new user info.

Then reboot and login with the new user (still out of X) and type startx. 

Then go to System > Administration > User and Groups and change/edit your main account's password. 

Then login to your main account (not root and not the new one, your regular user account) and then delete the account you created with root outside of x.

Then again, if you can get into your root account outside of x (which it seems you can) why not just type **startx** and go change your main user account's pass?

As for why your comp is booting to command line and not x, perhaps something happend to your init settings. init3 is booting to command line, init5 is booting to x. Maybe go check your init settings?

---

### Post by Bloch on 2006-04-14
Thanks folks. I reinstalled the desktop with apt-get update and then /etc/init.d/gdm.

I had previously gone through the dpkg-reconfigure xserver-xorg wizard.
That has left me with a slightly lower resolution screen. If anyone could tell me the configuration files that were changed I could restore them. As far as I know I should swap the contents of file and the .bak backup that was made.
Or should I reconfigure from the menu?

Thanks again for your help

---

### Post by steve.horsley on 2006-04-14
[QUOTE=Bloch]I think if I could get my username and password when I am logged in as root I could login again as myself. Somehow the automatic login to gdm has failed and I am sent to a text interface.[/QUOTE]
Ad root you can find your user name with **ls /home**. And set the password with **passwd username**.

But as root, you can do **startx** and then use the GUI configuration tools (assuming that X will start).

---

