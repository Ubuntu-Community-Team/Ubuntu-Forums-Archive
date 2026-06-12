---
title: "Help installing splashy theme"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-06-09
I've been try like hell but I can not get a single splashy theme to install.
```

bob@tuxbox:~$ sudo splashy_config -i /etc/splashy/themes/kubuntusplashy.tar
>Install theme          [ FAIL ]
This format is invalid
Error opening directory '/tmp/splashy-theme-[COLOR=Red]wzZugg[/COLOR]/README': Not a directory
```I get this every time except the red part is different every time I run it and it makes a corresponding file in my /tmp folder that does contain the README file but it's owned by root. Any ideas?

---

### Post by kyphi on 2007-06-10
There is a Gnome Splash Screen Manager in the repositories for Ubuntu that does all that with ease.

Perhaps there is a similar programme for Kubuntu.

             ____________________________________

Sorry, I just realised that this is not what you wanted to know.

---

### Post by thelocust on 2007-06-10
I found the problem everything works fine I got the theme to load but on boot-up it says it cant find /etc/inittab which further research found that ubuntu doesn't use inittab it uses upstart. Does anyone know a work around for this.

---

### Post by thelocust on 2007-06-10
Well I give up I found a work around but I can't get it to work. If anybody else is interested it's at the bottom of[ this page.]("http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions")

---

