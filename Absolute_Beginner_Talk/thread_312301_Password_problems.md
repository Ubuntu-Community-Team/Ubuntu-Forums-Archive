---
title: "Password problems"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by kenogrene on 2006-12-04
Hi 

We have just tryed to install Ubuntu LTS 6,06. When we started up after the installation we are asked for username and password. We have no problem with the username but we are not able to enter the password. Have any of you tryed this and what have you done to salve it. 

KenogRene

---

### Post by 23meg on 2006-12-04
Where exactly does this happen? Do you get a graphical login screen (brown) when Ubuntu starts, or just a text prompt?

---

### Post by kenogrene on 2006-12-04
Hi 

The page is black and it says:

Ubuntu 6.06.1 LTS Ulrich tty1

Ulrich Login:
Password:

When im trying to type anything in the password its not possible. The cursur dont move.

---

### Post by CupofDice on 2006-12-04
The password wont show. Dont worry about that, just type it in. 

I also think you are supposed to use-
```
startx
```
when you get the console to show the gui. This is advice from a noob who just screwed up his /home permissions (now fixed:D ), so take it at your own risk, but I have read the startx command over and over and over as the fix, and I just used the console, so the password not showing up is normal. You should probably wait for better help though

Edit- [http://www.linuxforums.org/forum/debian-linux-help/37888-how-start-gnome.html](http://www.linuxforums.org/forum/debian-linux-help/37888-how-start-gnome.html) found some better help here. Chances are you are not using Kubuntu right?

```

startgnome
or
startx gnome

```
It is for debian though, so it may not work.

---

### Post by tdwester on 2006-12-04
If you are using a number make sure to hit num lock it is off by default.

---

