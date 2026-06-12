---
title: "Howto load firestarter from boot?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-01-19
Hello,
i used automatix2 installation for firestarter.

If i press ALT F2 during boot i can read:" Loading Firestarter Firewalll", or something like this.

But after boot-login i always have to manualy start the firewall from Admin menu/firestarter with password.

How can i let it start automatic?

Thanks

---

### Post by davebgimp on 2007-01-19
Firestarter is a program to give you a gui for setting up a firewall rule(s) with IPTables. Since the firewall rules and policies are loaded at boot into IPTables, you actually do not need to run Firestarter at all during normal usage unless you are changing or entering a new rule, which in that case, you can just quickly fire up the app, add/edit the rule and close it back down.

---

### Post by shareMenaPeace on 2007-01-19
Thanks i thought this.
But i just like to keep track so i want the GUI to boot.
I also triggered the GUI cfg to boot during bootup, but it want i guess its because of the required password.

Though is there a save easy way todo this or i just need to manualy start the GUI every boot+password?

Thx

---

### Post by davebgimp on 2007-01-19
Follow the instructions on this page to have Firestarter start automatically without having to enter a password.

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

---

### Post by shareMenaPeace on 2007-01-19
> **davebgimp said:**
> Follow the instructions on this page to have Firestarter start automatically without having to enter a password.

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)
Thank you for the link davebgimp.

---

### Post by shareMenaPeace on 2007-01-19
When i try to save the sudoers file i get
> You are trying to save the file on a read-only disk. Please, check that you typed the location correctly and try again.

Do i need to change the partition rights todo this?

---

### Post by davebgimp on 2007-01-19
Are you editing this file as root? 

Try from a terminal:

**sudo gedit /etc/sudoers**

---

### Post by shareMenaPeace on 2007-01-19
Yes i even tried ALT F2 gksudo nautilus

---

### Post by davebgimp on 2007-01-19
try gksudo gedit /etc/sudoers from a terminal. It should work. Lastly try sudo su to switch to root and then gedit /etc/sudoers. If you do that, make sure to exit the session after you're done so as not to stay in root.

---

### Post by shareMenaPeace on 2007-01-19
Not working i get 
> GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


And closeing the terminal quiets the session , right?

---

### Post by shareMenaPeace on 2007-01-19
Ah found a way
[http://ubuntuforums.org/showthread.php?t=338883&highlight=host-based+authentication+failed](http://ubuntuforums.org/showthread.php?t=338883&highlight=host-based+authentication+failed).
sudo nano -B /etc/sudoers

---

### Post by davebgimp on 2007-01-19
> **shareMenaPeace said:**
> Ah found a way
[http://ubuntuforums.org/showthread.php?t=338883&highlight=host-based+authentication+failed](http://ubuntuforums.org/showthread.php?t=338883&highlight=host-based+authentication+failed).
sudo nano -B /etc/sudoers

Awesome. Glad that worked for you.

---

### Post by shareMenaPeace on 2007-01-19
Well i still dont get it working.

Also i read this
> A note on the security aspects: This method makes a trade off in local security for convenience. If your user account becomes compromised the attacker will be able to control the firewall. However this method is preferable to having a shared root user password in a multiuser setting. It is also preferable if the alternative is not to run Firestarter at all.


I can life with it to start the GUI if i want it to appear, thx anyway.

Cheers

---

### Post by Xappe on 2007-01-19
you should always use visudo for editing /etc/sudoers !
like this:
```
$ sudo visudo
```

---

### Post by davebgimp on 2007-01-19
> **Xappe said:**
> you should always use visudo for editing /etc/sudoers !
like this:
```
$ sudo visudo
```

D'oh! He's got a point there. Been a couple years since I had to modify sudoers.

---

### Post by shareMenaPeace on 2007-01-19
ok cool thx

---

### Post by phonicboom on 2008-04-17
duh! ok i replied to a post on page one and didn't see this was a 2 page thread

ok so what i wrote is already here

deleted :)

---

### Post by ramjet_1953 on 2008-04-17
Something to keep in mind.

It is not good to have applications running in root mode on your desktop.
In fact it is a security risk.

Also, unless you require port forwarding, there is no need to touch iptables at all.

What do they say about trying to fix things that aren't broken?

Regards,
Roger :cool:

---

