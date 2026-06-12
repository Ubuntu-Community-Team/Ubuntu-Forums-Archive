---
title: "file /etc/hosts (Xubuntu)"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-12-02
Hi,

When I start Xubuntu, I get a warning box that xfce can't connect to the internet. In that box, it says something to the effect that "xxxxx-desktop" should be added to the "file /etc/hosts".

Can someone tell me how to do just that? I have no idea where to find that file, and what to enter.

Thanks!

---

### Post by DapperMe17 on 2006-12-02
Anyone?

---

### Post by Bachstelze on 2006-12-02
Please paste the contents of the file :)

---

### Post by Shatrat on 2006-12-02
> I have no idea where to find that file
/etc/hosts is in /etc, and is named hosts. ;)

If you want to see what's in it in a terminal you can just type 
```
less /etc/hosts
```

---

### Post by DapperMe17 on 2006-12-02
Here's the warning data as it appears in the box on the screen, prior to the desktop loading...


"Could not look up internet address for xxxxx-desktop.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
xxxxx-desktop to the file /etc/hosts on your system."


xxxxx-desktop is the name of the computer, or user.

---

### Post by Shatrat on 2006-12-02
If xxxxx-desktop is the host name of your computer then it should have the following in your /etc/hosts at the top.  You can edit the hosts file by using ```
sudo gedit /etc/hosts
```
127.0.0.1          localhost
127.0.1.1          xxxxx-desktop

---

### Post by taurus on 2006-12-02
> **DapperMe17 said:**
> Here's the warning data as it appears in the box on the screen, prior to the desktop loading...


"Could not look up internet address for xxxxx-desktop.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
xxxxx-desktop to the file /etc/hosts on your system."


xxxxx-desktop is the name of the computer, or user.
It's the name of the computer!  Both /etc/hosts & /etc/hostname need to have the same name so if you have "xxxxx-desktop" in /etc/hostname, then you better have "xxxxx-desktop" in your /etc/hosts as well.

---

### Post by Shatrat on 2006-12-02
Im curious why it wouldn't be in your /etc/hosts.  
Did you change the hostname after installing?  
What is in your /etc/hosts now?

---

### Post by DapperMe17 on 2006-12-02
I tried the command...sudo gedit /etc/hosts...in terminal, but it said command not found. Should this work in Xubuntu?

---

### Post by Shatrat on 2006-12-02
h0h0, try sudo nano /etc/hosts

---

### Post by DapperMe17 on 2006-12-02
Right on friend! It's there, but i remember modifying the compnetwork settings, by adding to the end of the computer name. I've deleted that on network settings now. Will let you know of any problems.

Just use to Winblows O gues, with the GUI's...commands are not my strong suit, yet...maybe...:p

---

### Post by CADutch on 2008-05-11
sudo won't work until you have resolved your issue with hostname and hosts (catch 22). Instead of sudo use **SU** and logon as root. Now you will be able to nano/gedit the file hosts. I had the same issue on Ubuntu and XUbuntu when upgrading to Hardy Heron. 

p.s. if you don't know your root passwork then go to Applications - system - user groups and unlock the screen screen. You can now enter a password for root.

Good luck, Thomas

---

