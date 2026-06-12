---
title: "how can I boot ubuntu to command line only?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by paark.s on 2007-04-10
sometime I leave my laptop on for days using rtorrent. I just want to run it with the least heat possible.

sugguestions to do other things are also welcomed.

thanks

---

### Post by carlosfocker on 2007-04-10
Only suggestion is to prop the back of the laptop up to insure proper airflow. Having the gui loaded really I dont feel makes much of a difference.

---

### Post by bulldog on 2007-04-10
Ctrl-Alt-F1 will give you a console.if that's what you're looking for.

---

### Post by garlik42 on 2007-04-10
In /etc/init.d there is a file "gdm" for ubuntu or "kdm" for kubuntu.
you must remove the executable bit from the file.

IE from a terminal
cd /etc/init.d
sudo chmod a-x gdm

Reboot.

To put the gui back,
cd /etc/init.d
sudo chmod a+x gdm

Reboot

There might be a better way to do this, but this method does work (I just tried it)

---

### Post by paark.s on 2007-04-11
> **bulldog said:**
> Ctrl-Alt-F1 will give you a console.if that's what you're looking for.

That 's kind of thing I was thinking of, thanks.

But one more question arise, would it be the same as running gnome-terminal in gnome?or what is the difference?

---

### Post by click4851 on 2007-04-11
why do I seem to remember that you can change the run level at boot up so your machine will boot to the command line? I had to do this for some reason under Mandrake, for a period of time.

---

### Post by chili555 on 2007-04-11
> But one more question arise, would it be the same as running gnome-terminal in gnome?or what is the difference?Yes.

Gnome terminal puts a nice window around it, uses themes and lets you change profiles to get dark blue type on a pink background. Ctl-Alt-F1 gives you a prompt and no more. Once you get there, I think I would make sure GDM is stopped with *sudo /etc/init.d/gdm stop* When you are done, start GDM and press Ctl-Alt-F7.

---

### Post by AlanRogers on 2007-04-11
> **chili555 said:**
> Ctl-Alt-F1 gives you a prompt and no more. ~~~ When you are done, start GDM and press Ctl-Alt-F7.
Sorry for the quick hijack but is there somewhere a concise list of these very useful keystrokes?

---

### Post by paark.s on 2007-04-13
thanks.

---

### Post by garlik42 on 2007-04-25
> **click4851 said:**
> why do I seem to remember that you can change the run level at boot up so your machine will boot to the command line? I had to do this for some reason under Mandrake, for a period of time.

The default runlevel in gentoo is in a file /etc/inittab 3 is for text mode and I think 6 is for gdm.

I'm not sure where this lives in ubuntu, but if you execute "runlevel" from a prompt, it says "N 2"

---

