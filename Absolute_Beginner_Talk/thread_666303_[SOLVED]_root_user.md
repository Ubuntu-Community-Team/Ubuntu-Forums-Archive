---
title: "[SOLVED] root user"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Terry N on 2008-01-13
Hello all,

I am very green on using linux although I have had it loaded on my system for a long time.I don't know any of the commands to compile a piece of software or even if I am in the right terminal so I just gave up. Then I found Ubuntu and it got me interested again. Problem is I do not know how to log in as root. Can anyone tell me how to do this? Thanks for the help. By the way does anyone know of any good video editing software. I tried to install cinelerra and that is how I found Ununtu after I lost my source file. Its a long story but anyway I was running Debian and Ubuntu seems much easier so I am glad I did it.

Thanks, TerryN

---

### Post by ThrobbingBrain66 on 2008-01-13
Logging in as a root is bad practice.  Can I ask why you want to do this?

As for video editing, Ubuntu repos are available on Cinelerra's website:
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by overdrank on 2008-01-13
> **Terry N said:**
> Hello all,

I am very green on using linux although I have had it loaded on my system for a long time.I don't know any of the commands to compile a piece of software or even if I am in the right terminal so I just gave up. Then I found Ubuntu and it got me interested again. Problem is I do not know how to log in as root. Can anyone tell me how to do this? Thanks for the help. By the way does anyone know of any good video editing software. I tried to install cinelerra and that is how I found Ununtu after I lost my source file. Its a long story but anyway I was running Debian and Ubuntu seems much easier so I am glad I did it.

Thanks, TerryN

Hi this is a good link on root
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Tag you it  ThrobbingBrain66  :)

---

### Post by Linuxratty on 2008-01-13
Peter van der Linden wrote:
The "don't run as root" mantra dates from the days of
timesharing servers. When you run on a single user PC, your
most valuable resource is your data, not the integrity of
the system.

If your system is compromised, the attacker can do all the
things he wants to do in your user account, equally well as
a root account (store files, send spam, run zombie
software). Being or not being root doesn't hinder him at
all.

On a server it is bad to be root all the time because a
mistake by you could affect many other people. On a single
user PC behind a firewall there is no compelling reason not
to run as root.

---

### Post by Terry N on 2008-01-13
I just need administative rights so I can add 1344 fire device for kino?

Thanks again Terry N

---

### Post by Terry N on 2008-01-13
I guess I need to use Rootsudo but it look like it needs command lines and I was trying to avoid that.

Thanks, Terry

---

