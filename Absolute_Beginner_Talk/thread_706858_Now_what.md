---
title: "Now what?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by larrypinsupplync@msn.com on 2008-02-24
I have successfully installed Ubuntu 7.10 (everything seems to work), now i'm not sure what to do next. Do I need to install drivers? If anyone could direct me to a thread that gives some good post-installation instructions i would very much appreciate it!:)

---

### Post by northern lights on 2008-02-24
You don't need to install drivers, Ubuntu autodetects your hardware - if it does support it, that is. There might be restricted drivers for your graphics card for instance, that might or might not work better. If so, that should pop up in the notification area (top right, next to the clock).

The first thing I'd do is go through the list of easy-to-install applications under "Applications > Add/Remove...". Then I'd run an update of the system: ```
sudo apt-get update
```

You probably want to customize your desktop management. In order to be able to select "Custom" under "System > Preference > Appearance" you need to run ```
sudo apt-get compizconfig-settings-manager
```

---

### Post by larrypinsupplync@msn.com on 2008-02-24
Ok nothing there so i assume drivers are not needed. Is there a how to for installing programs?

---

### Post by northern lights on 2008-02-24
There is several, check [this]("http://monkeyblog.org/ubuntu/installing/#script") for instance.

Further, see the edits of my first post...

---

### Post by seventhc on 2008-02-24
There are a lot of programs available, you might want to have a look in add/remove.
click on
[I]Applications>Add/Remove
[/I]if you see a program in that list just put a check mark next to the ones you want and click apply.also have a look at this site
[http://getdeb.net/](http://getdeb.net/)
The files from that site install easily, no commands needed. ;)

---

### Post by Tatty on 2008-02-24
There is a pretty good help file to get you started under the system menu, or you can read it online here:

[https://help.ubuntu.com/]("https://help.ubuntu.com/")

or there is the community documentation, which you should start browsing through once you have got past the official ubuntu help file...

[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

After that come on to these forums with any problems, there is a useful search function above which you should try first, but if you are still struggling then post on here and usually someone can come and help you, or at least point you in the right direction.

---

### Post by steveneddy on 2008-02-24
Try looking at [www.ubuntuguide.org/](www.ubuntuguide.org/)

Drivers are software that make your hardware work with the OS.

If your hardware is working, why do we need more drivers?

Maybe you are confused about terminology.

[COLOR="Blue"]You want some extra software, right?

What do you want to do?[/COLOR]

And why is your e-mail address used for your user name?

I would change that, make a new log in, if I were you. Pick something like larry, but do not use your e-mail address.

---

### Post by larrypinsupplync@msn.com on 2008-02-24
Thanks guys that should keep me busy for the evening!

---

