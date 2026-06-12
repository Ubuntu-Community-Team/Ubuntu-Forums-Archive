---
title: "Laptop load cylce count fix in Arch?"
date: 2008-09-28
forum: Arch and derivatives
---

### Post by Sealbhach on 2008-09-28
Right, just installed Arch and using Firefox in Fluxbox. Wasn't as bad as I thought it would be, except that damn twm running when I did startx caused me a few headaches.


I have a couple of questions - hope this is the right place.

1. Is there a fix for the laptop load cycle count issue - like the "ugly fix" they have in Ubuntu?

2. Can anyone recommend a nice file manager that works well in Fluxbox.

3. Do I have to type "startx" everytime or is there another way, or a graphical login screen?


.

---

### Post by fwojciec on 2008-09-28
> **Sealbhach said:**
> Right, just installed Arch and using Firefox in Fluxbox. Wasn't as bad as I thought it would be, except that damn twm running when I did startx caused me a few headaches.


I have a couple of questions - hope this is the right place.

1. Is there a fix for the laptop load cycle count issue - like the "ugly fix" they have in Ubuntu?

You can have a look at this thread: [http://bbs.archlinux.org/viewtopic.php?id=39258]("http://bbs.archlinux.org/viewtopic.php?id=39258")

> **Sealbhach said:**
> 2. Can anyone recommend a nice file manager that works well in Fluxbox.

Thunar, pcmanfm, rox -- basically any file manager will work fine in Fluxbox.  My favorite is thunar, but it's purely a matter of personal preference.

> **Sealbhach said:**
> 3. Do I have to type "startx" everytime or is there another way, or a graphical login screen?

No, you can install one of the graphical login managers -- [http://wiki.archlinux.org/index.php/Login_manager]("http://wiki.archlinux.org/index.php/Login_manager")

---

### Post by MisfitI38 on 2008-09-28
> **Sealbhach said:**
>  Wasn't as bad as I thought it would be, except that damn twm running when I did startx caused me a few headaches.
[You either skipped over this part]("http://http://wiki.archlinux.org/index.php/Beginners_Guide#.7E.2F.xinitrc") of the guide, or you weren't following the right guide. ;)
2. Personally, I like thunar. PCmanfm is ok also.
3. All the DM's I can think of are available and installable via pacman. Note that you may wish to reset your default runlevel through /etc/inittab or, launch your DM as a daemon, specified in the DAEMONS= array in /etc/rc.conf.

Welcome to Arch. I hope you enjoy your stay.

---

### Post by RiceMonster on 2008-09-29
> **Sealbhach said:**
> 2. Can anyone recommend a nice file manager that works well in Fluxbox.

I personally like Thunar, however there's tons of other available.

> **Sealbhach said:**
> 
3. Do I have to type "startx" everytime or is there another way, or a graphical login screen?

You'll want to use GDM, KDM, SLIM, or XDM

You can also modify your ~/.bash_profile so x will start when you log in (I had that for a bit, and it annoyed me, so now I just type startx).

check these out:
[http://wiki.archlinux.org/index.php/Start_X_at_boot](http://wiki.archlinux.org/index.php/Start_X_at_boot)
[http://wiki.archlinux.org/index.php/Adding_a_login_manager_(KDM%2C_GDM%2C_or_XDM)_to_automatically_boot_on_startup](http://wiki.archlinux.org/index.php/Adding_a_login_manager_(KDM%2C_GDM%2C_or_XDM)_to_automatically_boot_on_startup)

---

### Post by mips on 2008-09-29
1. I did exactly the same as for ubuntu if I recall correctly.
2. PCManFM, emelFM
3. Use SLiM. Just add SliM to your daemons list in /etc/rc.conf and it will start next time you boot. 
[http://wiki.archlinux.org/index.php/Login_manager#Append_the_daemon_name_for_the_Display_Manager_of_your_choice_.28entrance.2C_gdm.2C_kdm_or_slim.29](http://wiki.archlinux.org/index.php/Login_manager#Append_the_daemon_name_for_the_Display_Manager_of_your_choice_.28entrance.2C_gdm.2C_kdm_or_slim.29)

---

### Post by Sealbhach on 2008-09-29
Cool, thnks everyone. :D


.

---

