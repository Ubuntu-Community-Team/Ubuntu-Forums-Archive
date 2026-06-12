---
title: "dpkg interrupted"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-22
I just upgraded to Dapper from Breezy and when I open my Synaptic Package Manager I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I opened my terminal and typed that in, this is what I got and I'm not at all sure what to do
```
enzo@reboot:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
enzo@reboot:~$ sudo dpkg --configure -a
Setting up libunicode-string-perl (2.09-1) ...
Setting up gdm (2.14.6-0ubuntu1) ...

Configuration file `/etc/gdm/gdm.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** gdm.conf (Y/I/N/O/D/Z) [default=N] ?

```

I was trying to install Xubuntu through the terminal... I think I typed something like ```
sudo apt-get install xubuntu-destkop
``` (which did not work.) Could that have caused this?

[This person]("http://ubuntuforums.org/showthread.php?t=179960&highlight=dpkg+interrupted") had the same error message, but it seems as though they knew what buttons to push at the "dpkg --configure -a" prompt (and I do not). Also, I think they were using automatix, and I am not.

[This person]("http://ubuntuforums.org/showthread.php?t=178309&highlight=dpkg+interrupted") had a similar problem, but their terminal paste isn't the same as mine.

Edit: I accidentally pushed enter and now lots of things are installing. o.O  ...

---

### Post by kingmonkey on 2006-05-22
If you havent added anything to gdm.conf then just update. you can press D to see the differences if you are unsure. 

Or backup your original gdm.conf and install new one then you have the option of using the old if you want.

---

### Post by S{yndrom}e on 2006-05-22
you are basically installing a whole new desktop manager. So alot of things are going to come along with. It is basically like installing umm Windows 98 ontop of Windows XP sorta. Not realy but u get what i mean :P ?

to get rid of it you can do this (i tihnk)

sudo apt-get remove xubuntu-desktop --purge

oh and next time dont use apt-ger when wanting to try something out

use aptitude

i.e sudo aptitude install xubuntu-desktop

---

### Post by tonyr on 2006-05-22
There is nothing wrong with what you are seeing, as far as I can tell, if that's what
you are asking about.  The **gdm** package contains a new copy of
the file **gdm.conf**, but you already have an existing one (I assume
you have been using Gnome) from your Breezy installation.  You should let the
default action occur (keep your old gdm.conf).  I think the new version will
show up as **/etc/X11/gdm/gdm.conf.new**, but I could be wrong about that.
In any case, I don't think allowing the default action should do any harm.

This kind of thing is not unusual.  Updating packages will occasionally produce such
a query.

---

### Post by Sef on 2006-05-22
> Configuration file `/etc/gdm/gdm.conf'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** gdm.conf (Y/I/N/O/D/Z) [default=N] ?

You are being asked what to do.  Do you want to install  the new desktop or not (Y, I or (N, O) , or would you rather see the differences between the desktops (D), or to think about it some more (Z.)

---

### Post by Clay85 on 2006-05-22
ah okay. Thank you for clearing it up, I was really scared! :D

---

### Post by tonyr on 2006-05-22
[QUOTE=Clay85]
Edit: I accidentally pushed enter and now lots of things are installing. o.O  ...[/QUOTE]

Yeah, you let the default action happen, which is not a bad thing.

And about that Xubuntu install/remove, [this]("http://www.ubuntuforums.org/showthread.php?t=129517") thread might interest you.

---

### Post by Clay85 on 2006-05-22
Yeah I found that thread, but that's how to uninstall it, and I want to install it. I'm sure it's some easy command in the CLI.

What is aptitude? I could look it up I suppose...

---

### Post by Sef on 2006-05-23
Aptitude is an advanced apt-get.  If you install xubuntu, use aptitude, it will make it easier to uninstall it, if you so desire.

Commands to install xubuntu

sudo apt-get update

sudo aptitude install xubuntu-desktop

---

