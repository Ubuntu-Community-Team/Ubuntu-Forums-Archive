---
title: "A little problem while booting/shutting down"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-06-06
Hello :)
I have recently installed Xfce on my Ubuntu system (sudo aptitude install xubuntu-desktop).
After that I took care of my menus (removed Xubuntu's applications from Ubuntu's menu). Everything works great.
The problem is, that when I'm booting/shutting down my system, Xubuntu's logo (usplash? :-k ) is being displayed instead of the defaul Ubuntu.
Could I chnage that back, so that it would display the defaul Ubuntu? :)

Thanks, 
Klaidas

---

### Post by Poirot on 2006-06-06
I had a similar problem with Kubuntu.

[http://www.ubuntuforums.org/showthread.php?t=179738](http://www.ubuntuforums.org/showthread.php?t=179738)

Watch out for the mistaake in the earlier post, read the whole thing first.

In short:
Do this```
sudo update-alternatives --config usplash-artwork.so
```and this```
echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-manager
```

---

### Post by Russty of Oz on 2006-06-06
Well, mine is doing something altogether different.  When I boot/shut down I get a black screen with the message " Signal out of Range "

Anyone know why that is and if it can be fixed?  Breezy used to show the Ubuntu startup.

---

### Post by Klaidas on 2006-06-06
Well, it seems to work when I shutdown. But when booting up, it still displays Xubuntu's usplash ](*,) 
Any ideas? :)

Here's what I did:
[QUOTE=Terminal]
**klaidas@klaidas-desktop:~$ **sudo update-alternatives --config usplash-artwork.so 

There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/xubuntu-splash.so

Press enter to keep the default[*], or type selection number: **1**
Using `/usr/lib/usplash/usplash-default.so' to provide `usplash-artwork.so'.
**klaidas@klaidas-desktop:~$** echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-manager
/usr/sbin/gdm
**klaidas@klaidas-desktop:~$**[/QUOTE]

---

### Post by Klaidas on 2006-06-06
Ok, everything works now.
The problem was that I didn't do ```
sudo dpkg-reconfigure usplash
``` :)
Thanks for help ;)

---

