---
title: "Firewall"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by progrockusa on 2007-03-16
Hi i'm looking for a firewall (preferably GUI based) for ubuntu mostly to monitor outbound traffic.

---

### Post by 23meg on 2007-03-16
Check out Firestarter.

---

### Post by bapoumba on 2007-03-16
There is one installed by default on every ubuntu (iptables). You can install firestarter, a GUI to iptables.

---

### Post by oliviacond on 2007-03-16
Firestarter?

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by u.b.u.n.t.u on 2007-03-16
Maybe this is of use?

Firestarter (Firewall GUI for iptables.)

* Check to see if Firestarter is running.
sudo /etc/init.d/firestarter status


* Add Firestarter to start-up programs.
System > Preferences > Sessions
Click.
Add
Enter the text.
sudo firestarter --start-hidden

---

### Post by progrockusa on 2007-03-16
not sure how to install it.
```
Installing in Debian and Ubuntu

Firestarter is maintained in Debian and can be downloaded and installed using the apt-get tool by simply typing "apt-get install firestarter".

Ubuntu users can install Firestarter by enabling the "universe" repository in the /etc/apt/sources.list file or in synaptic under Settings->Repositories. Having enabled the repository, the procedure is the same as in Debian.

```
when i do apt-get install firestarter i get this. 
```
prog@prog-desktop:~$ apt-get install firestarter
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```
i don't know what it means by enabling universe.

---

### Post by 23meg on 2007-03-16
Here's [how to enable Universe]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html"). After enabling it, you can install Firestarter with ```
sudo apt-get install firestarter
```

More information on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

More on the basics of installing software:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by progrockusa on 2007-03-16
nvm i figured it out. ty guys

---

