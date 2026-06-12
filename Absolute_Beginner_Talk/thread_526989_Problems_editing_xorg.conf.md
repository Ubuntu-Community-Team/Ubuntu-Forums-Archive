---
title: "Problems editing xorg.conf"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by mashedtaz1 on 2007-08-16
I am having an issue when trying to edit this file.

I have used the command:

gksudo gedit /etc/xll/xorg.conf

it then prompts for my password, then the editor opens up and it is blank!

In the terminal window I get:

None of the authentication protocols specified are supported and host-based authentication failed.

I need to edit this so that i can add a line to it.

Can anyone help??

---

### Post by Waappu on 2007-08-16
Hi

Type in terminal```
gksudo gedit /etc/X11/xorg.conf
```terminal is case sensitive

---

### Post by aitorcalero on 2007-08-16
> **mashedtaz1 said:**
> I am having an issue when trying to edit this file.

I have used the command:

gksudo gedit /etc/xll/xorg.conf



Are your sure that you are using the right path to xorg file?

I think the correct path is /etc/X11/xorg.conf, try this one:
```

gksudo gedit /etc/X11/xorg.conf

```

And remember in GNU/Linux caps matters!!! ;)

---

### Post by petit.padavoine on 2007-08-16
Don't forget to create a backup of that file BEFORE you edit it, because it could break your GUI.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by RomeReactor on 2007-08-16
> **aitorcalero said:**
> And remember in GNU/Linux caps matters!!! ;)
That, and **mashedtaz1** was writing xll (ex-el-el) instead of X11 (Upper case x-one-one).

Also:
> **mashedtaz1 said:**
> In the terminal window I get:

None of the authentication protocols specified are supported and host-based authentication failed.
**mashedtaz1**, that's a [bug while using gksudo]("https://launchpad.net/ubuntu/+source/gksu/+bug/23917"). Nothing to worry about, though.

---

### Post by mashedtaz1 on 2007-08-18
Thanks for all your help guys, sorry for being such a noob and not using attention to detail lol! :)

---

