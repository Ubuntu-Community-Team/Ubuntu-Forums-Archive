---
title: "cannot log in"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by coolkid on 2008-04-01
I have ubuntu 7.04 installed on my PC. After I had installed JDK 1.6 from NetBean CD, I installed NetBean IDE and It promted that dosen't find any JDK on my ubuntu. After that, I restart my PC. Next, I loged in my account, It appeared the desktop screen just about 3 seconds then quit out to the log in screen. What'd happen with it? Thanks for any opinion.

---

### Post by dstew on 2008-04-01
> After I had installed JDK 1.6 from NetBean CDHow did you do this? Was the JDK in a Debian package, or did you compile from source? Did you run an installation script? Are you sure the JDK was set up for use in a Debian system, like Ubuntu?

---

### Post by coolkid on 2008-04-01
I set up JDK which attach to the NetBeadn CD 6.0 . I choose the file .bin . then I change the permission to execute it . Then I doulbe click and install it . After install JDK. I continue to install Netbean but It dosen't find out where I've installed JDK. After I restart my PC, the problem is like what I've posted.

---

### Post by frup on 2008-04-01
On the login screen (GDM) near the bottom left there should be an option to select sessions. You should try selecting something like fail safe gnome and checking for any irregularities with that as well.

---

### Post by dstew on 2008-04-02
I think the NetBeans JDK installer was not set up for a Debian system like Ubuntu. I think the best place to get advice would be from the people who distribute the NetBeans CD. Maybe they have a forum, or contact information.

You might need to re-install Ubuntu to fix it, but that depends on how bad the problem is. Can you boot in recovery mode (grub menu choice)?

---

