---
title: "[SOLVED] Default root password?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by VorlonShadow on 2007-10-02
I just finished installing Ubuntu (how do you pronounce that, BTW?).  I'm trying to install updates for Firefox and Avast, and I need root access to do so.   During the installation of the o/s, it did not ask me for a root password.  I was assuminng that it was the same as the account that I set up, but evidentially not.  So, is  there a default root password, and if so, what is it?

Thanks,
Jesse

---

### Post by shad0w_walker on 2007-10-02
The root user is disabled by default (Security reasons) so any prompts for passwords will be for your users password. How are you trying to do these updates? Synaptic and add/remove programs should prompt you automatically to enter your password.

---

### Post by jordanmthomas on 2007-10-02
I pronounce it ooh-boohn-too

Check this for more explanation on root:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

short answer:  there is no root password.  You need to use your own and sudo or gksudo.
You can get a temporary root shell with
```
sudo su
```
and using your own password.

Also, to update firefox and Avast and anything else, look up apt and synaptic.

---

### Post by eph1973 on 2007-10-02
In Ubuntu, it is standard to use the command sudo to do things you normally need to do as root.  If you want to set a password for root, you would type:
```
 sudo passwd
```
It will prompt you for a password, then enter YOUR password, then it will ask for a new UNIX password, and ask for a confirmation.  If you want to log in as root, from the terminal, you can type
```
su
```
and give it the password you generated earlier.  However, pretty much anything you need to do as root, you can do as sudo (which prompts you for YOUR password, not the root password), and it's much safer (less likely to screw something up on your system on accident).

---

### Post by alienexplorers on 2007-10-02
Remember to use > sudo for non-graphical commands and > gksudo for graphical commands

---

### Post by bodhi.zazen on 2007-10-02
LOL

By default the root account is locked and sudo is patched to account for this.

You can access root with ```
sudo -i
```

You can set a root password , as above ...

You can then re-lock the root account with :

```
sudo passwd root -l
```

If you are unfamiliar with sudo, it takes a while for it to grow on you ... but eventually it does

_Note_: That command should be :

```
su -
```

Or 

```
sudo su -
```

:twisted:

---

### Post by bodhi.zazen on 2007-10-02
> **alienexplorers said:**
> Remember to use > sudo for non-graphical commands and [QUOTE]gksudo for graphical commands[/quote]

+1

---

