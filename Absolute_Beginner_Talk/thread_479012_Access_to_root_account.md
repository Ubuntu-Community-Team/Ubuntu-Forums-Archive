---
title: "Access to root account"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by florida490 on 2007-06-19
Just installed 7.1.  I wanted to use apt-get to install Firestarter, but got some kind of message about not being root.  I went to system, prefrences, administration, users and groups, and got entered my password.  Will this give me access to the root account?  If so, how do I get out of the root account?

I'm also concerned about being logged in as root on the Interent.  I've heard that can leave my computer open to attacks.  Is there any way I can download Firestarter on another computer and burn it on CD?

---

### Post by Spike-X on 2007-06-19
> **florida490 said:**
> 
I'm also concerned about being logged in as root on the Interent.  I've heard that can leave my computer open to attacks.  

Which is why Linux doesn't let you log in as root.

You need to put "sudo" before the apt-get command. This will give that particular command temporary root access for that time only.

---

### Post by bone43 on 2007-06-19
Check out this page scroll down a little ways there is a section on installing software :)

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

Have Fun!

---

### Post by ramjet_1953 on 2007-06-20
Unless you need to change the firewall, i[COLOR="Blue"]ptables[/COLOR], to allow port forwarding, I would leave it alone, as all ports are closed by default.

What many people don't understand is that Firestarter is NOT a firewall. It is a graphical front-end for iptables.

Also, it is a bad move to run the Firestarter GUI on your desktop continually, as it requires root privileges to do so, which, in itself, is a fairly grave security risk.

If it's not broken, don't try to fix it, is the rule here.

Regards,
Roger :cool:

---

### Post by drivel on 2007-06-20
Of course,you can login root account,but not advised.
Use sudo instead!

---

### Post by atria on 2007-06-20
Yep sudo is a better choice. If you really need a root shell just for convenience sake, use

```
sudo -i
```

---

