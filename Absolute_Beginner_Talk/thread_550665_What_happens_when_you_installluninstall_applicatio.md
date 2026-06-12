---
title: "What happens when you installl/uninstall applications?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-09-14
I am curious to know what goes on "behind the scenes" when you install/uninstall applications in Linux.

I am a previous Windows user, and I know that basically Windows create a folder in the C:/Programs Files. There also is usually a short cut in the start menu.

Is there a "Program Files" in Linux? Where does Linux create files that I should know about?

How about uninstall? When you uninstall a program in Windows, it very often still has a folder in the Program Files, and sometimes even in the Start Menu (that really annoys me).

Does uninstalling a program and removing the residual config in the Package Manager complete removes all traces of the program?

Thanks for your input!

---

### Post by overdrank on 2007-09-14
> **Odd-rationale said:**
> I am curious to know what goes on "behind the scenes" when you install/uninstall applications in Linux.

I am a previous Windows user, and I know that basically Windows create a folder in the C:/Programs Files. There also is usually a short cut in the start menu.

Is there a "Program Files" in Linux? Where does Linux create files that I should know about?

How about uninstall? When you uninstall a program in Windows, it very often still has a folder in the Program Files, and sometimes even in the Start Menu (that really annoys me).

Does uninstalling a program and removing the residual config in the Package Manager complete removes all traces of the program?

Thanks for your input!

Hi maybe this link will help it has some good info on files
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by hyper_ch on 2007-09-14
to completely remove you need to uninstall AND purge the package... otherwise the config files will be left behind.

---

### Post by Odd-rationale on 2007-09-14
So does doing that leave no traces of the program to bog down my system? (unlike Windows, which you have to reinstall every six months :) )

Great! How do I purge the program?

---

### Post by hyper_ch on 2007-09-14
it will not bog down the system as there is no central registry like in windoze... the config data is each in a different file normally to be found either in /etc/PROGRAMM or /home/USER/.PROGRAMM

```

sudo apt-get remove --purge PACKAGE

```

---

### Post by kombipom on 2007-09-14
Personally I use Synaptic to install & uninstall my software and that has a "Mark for Complete Removal" option which removes the software and the configuration files.

Right-click on installed package, select "Mark for Complete Removal" then click Apply, Hey Presto!

No doubt there is a command line way of doing this with apt-get if you prefer (try man apt-get in a terminal for all the options).

The only reason to reinstall Ubuntu every 6 months is to get the latest version ;-)

---

### Post by Odd-rationale on 2007-09-14
Thanks all!

---

