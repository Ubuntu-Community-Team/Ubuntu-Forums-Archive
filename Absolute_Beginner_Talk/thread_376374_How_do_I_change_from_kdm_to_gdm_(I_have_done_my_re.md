---
title: "How do I change from kdm to gdm? (I have done my research) [Resolved]"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Tahir on 2007-03-04
Hello all,

How do I change from kdm to gdm.  This is of course different from changing from kde to gnome which is easy.  I tried editing the file:

/etc/X11/default-display-manager

and changing it but this method does not work.  If I do this then what happens is that when I restart the computer the only way I can start the user interface again is by changing it back to kdm.   What do I do?  Please help me.

Thanks for all the responses.

-Tahir

---

### Post by qiemem on 2007-03-04
Should be a lot easier than what you're trying to do. At the login window, there should a session button at the bottom left. Click on this and select the DE you want.
Hope that helps!

---

### Post by aysiu on 2007-03-04
That method does work, but GDM is /usr/**s**bin/gdm and KDM is /usr/bin/kdm

---

### Post by Tahir on 2007-03-05
[QUOTE="aysiu"]That method does work, but GDM is /usr/**s**bin/gdm and KDM is /usr/bin/kdm[/QUOTE]

Thanks. got it sorted. All I did was change the line

```
/usr/bin/kdm
```

to

```
/usr/sbin/gdm
```

in the file /etc/X11/default-display-manager.

I was on the right track only I didnt know where it was. 

[QUOTE="qiemem"]Should be a lot easier than what you're trying to do. At the login window, there should a session button at the bottom left. Click on this and select the DE you want.
Hope that helps![/QUOTE]

There is a difference between the DESKTOP ENVIRONMENT and DISPLAY MANAGER.  Gnome and KDE are of the former and GDM and KDM are of the latter.  The Display Environment is the whole user interface that loads up after you login, whereas the display manager is just a graphical login screen.  That is all.

---

### Post by niki001 on 2007-03-05
Hi,

When I change the mentioned line in /etc/X11/default-display-manager to /usr/sbin/gdm and reboot I get a fault message 'X11 - server not configured correctly'. What else has to be done to make GDM (Gnome) boot as default in stead of KDM (KDE)?

thx

---

### Post by scxtt on 2007-03-05
hate to ask this, but ...

are you sure gdm is installed? (you also don't have to reboot for the change to take effect: if you're running kdm, just stop it, then start gdm) ...

---

### Post by Tahir on 2007-03-05
> **niki001 said:**
> Hi,

When I change the mentioned line in /etc/X11/default-display-manager to /usr/sbin/gdm and reboot I get a fault message 'X11 - server not configured correctly'. What else has to be done to make GDM (Gnome) boot as default in stead of KDM (KDE)?

thx

My whole post below sort of explains the difference between a desktop environment aka DE (such as gnome and KDE) and login managers (such as GDM and KDM).  To make it easier to understand I will provide a view images:

Here is GDM with a different theme: (part of the gnome project)

[http://www.gnome-look.org/CONTENT/content-pre1/48213-1.jpg](http://www.gnome-look.org/CONTENT/content-pre1/48213-1.jpg)

Here is KDM with a different theme: (part of the KDE project)

[http://www.kde-look.org/CONTENT/content-pre1/50996-1.png](http://www.kde-look.org/CONTENT/content-pre1/50996-1.png)

(Remember that, As I said above, KDM and GDM are login managers: all they manage is the login bit).  Also remember that when you change the theme of either login manager you could potentially make them look exactly the same but underneath the theme they are different).

Now here are some screenshots of KDE and and Gnome (both very bulky DEs):

KDE:

[http://www.kde.org/screenshots/](http://www.kde.org/screenshots/)

and Gnome:

[http://www.gnome.org/start/2.4/screenshots.html](http://www.gnome.org/start/2.4/screenshots.html)

Hope this clears up the confusion.

---

### Post by niki001 on 2007-03-06
thx Tahir,

that cleared up a lot...
Forgive me for being such a newbie...

greetz

---

### Post by Tahir on 2007-03-06
> **niki001 said:**
> thx Tahir,

that cleared up a lot...
Forgive me for being such a newbie...

greetz

I am a so called "noob" too. I have using ubuntu for about a month! I suppose I am a quick learner.

---

### Post by mac71 on 2007-04-05
Go here. Paste the command into a terminal and you can switch between the two in about 30 seconds.
[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

---

### Post by Tahir on 2007-04-05
> **mac71 said:**
> Go here. Paste the command into a terminal and you can switch between the two in about 30 seconds.
[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

Cheers mate :-)

I already solved the problem (I posted the solution on this thread), but thanks for an alternative (may I say easier) method.

-Taz

---

