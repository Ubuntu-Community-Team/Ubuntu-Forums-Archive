---
title: "root account &amp; password"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by sun wu-kong on 2007-08-15
Just installed Kubuntu Feisty from the live cd. I was not 'asked' for root password during installation.

Howto setup root account now ?

When I bootup system, howto configure system to directly goto KDE login screen.

Thank you.

---

### Post by shad0w_walker on 2007-08-15
When you boot up the system the KDE login manager should be started automatically. If its not then you either have a server install or there is some kind of problem with your X configuration.

As for changing setting the root password you can use this command

```
sudo passwd
```

This will enable the root account with the provided password, however i recommend using sudo or su instead of logging in as root.

---

### Post by anaconda on 2007-08-15
You can give root a password if you want to. (not recommended)
```
sudo passwd
```

The sudo will ask your normal users password first.
Then if you want to enable graphical login for root it is also possible. (dont know where in KDE, I use Gnome)

Autologin would be one setting (in Gnome) System>Administration>Login window
In kde it will be similar.

---

