---
title: "Browsing Nautilus as Root with all root file permissions !"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by TitanKing on 2006-06-18
Well you might find it tedious to run all the unix terminal commands time consuming when something needs to be done quickly. I just found this out and again lovely Ubuntu with its awsome "sudo" surprises me a whole lot !

Here it comes... wait for it... its worth it...

~>sudo nautilus

It works for creating folders, changing permissions, deleting files the whole lot ! ;)

Its risky but so is the terminal :)

!

---

### Post by richbarna on 2006-06-23
> **TitanKing]Well you might find it tedious to run all the unix terminal commands time consuming when something needs to be done quickly. I just found this out and again lovely Ubuntu with its awsome "sudo" surprises me a whole lot !

Here it comes... wait for it... its worth it...

~>sudo nautilus

It works for creating folders, changing permissions, deleting files the whole lot !  said:**
> 

Actually it's :-
[QUOTE]gksudo nautilus

sudo for standard commands, gksudo for launching gui's :)
Don't want to break anything now, do we? ;)

---

### Post by aysiu on 2006-06-23
I echo richbarna's recommendation--for graphical applications, use *gksudo*, not *sudo*.

---

### Post by Brunellus on 2006-06-23
will someone explain to me once again why gksudo is so much more preferable to regular sudo?

---

### Post by aysiu on 2006-06-23
It prompts you for a password graphically, so you can create a launcher for it instead of always running it from the terminal.

It doesn't screw with your permissions or accidentally give root ownership of some of your home configuration files.

And it works for every graphical application, not just some. If you don't believe me--try doing ```
sudo kate
```

---

### Post by Jagot on 2006-06-23
[QUOTE=Brunellus]will someone explain to me once again why gksudo is so much more preferable to regular sudo?[/QUOTE]

I could be completely wrong but I think I've heard that using by using gksudo it launches a program as root, but as sudo just launches as the user with administrative privileges.

---

### Post by aysiu on 2006-06-23
[QUOTE=Jagot]I could be completely wrong but I think I've heard that using by using gksudo it launches a program as root, but as sudo just launches as the user with administrative privileges.[/QUOTE]
You're partly correct. For example, if you launch an application with *sudo*, you may notice that it uses your user's configuration file in ~/.nameofapp, but if you launch it with *gksudo*, it'll use root's configuration file in /root/.nameofapp instead.

In both cases, though, you're really user with root privileges, as you aren't using the root password.

---

### Post by Jagot on 2006-06-23
Groovy, thanks for clarifying aysiu.

---

### Post by panurge77 on 2006-06-23
> You're partly correct. For example, if you launch an application with sudo, you may notice that it uses your user's configuration file in ~/.nameofapp, but if you launch it with gksudo, it'll use root's configuration file in /root/.nameofapp instead.

Hmm. sudo nautilus will use /root for sure, with root configuration, root icons, etc

Which remembers me another question I had about sudo, so I'll open another thread

---

### Post by aysiu on 2006-06-23
[QUOTE=panurge77]Hmm. sudo nautilus will use /root for sure, with root configuration, root icons, etc

Which remembers me another question I had about sudo, so I'll open another thread[/QUOTE]
That may be the case for Nautilus, but I haven't seen that to be the case for every application--Firefox, for example.

Notice how when I use ```
gksudo firefox
``` Firefox (well, Swiftfox, in this case, but it's the same for Firefox, believe me) gets launched with the default (empty) root profile that simply says it's up-to-date and uses the default Firefox.

When, however, I launch Firefox with ```
sudo firefox
``` Firefox gets launched with my user profile and my user theme (iFox).

This may not happen for all applications, but it's best practice to consistently use *gksudo* for graphical applications instead of *sudo*. If you've ever seen an "only root can install extensions" thread, you'll know why... or a "my .ICEauthority file is screwed up" thread.

Please encourage good practice. Just because sometimes (or even most times) you can get away with doing *sudo graphicalapp*, you should still encourage new users to use *gksudo graphicalapp* or *kdesu graphicalapp*.

---

### Post by TitanKing on 2006-06-27
Like totally did not know it :D Thanks for the tip !

---

### Post by Gustav on 2006-06-27
If you want to use your $HOME and so on with gksudo, you can use the -k (or --preserve-env) option. (e.g. gksudo -k "yourcommand")

---

### Post by NutrOn on 2006-06-30
The error I got with gksudo was

***@ubuntu:~$ gksudo nautilus
(nautilus:6683): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I guess Bastille firewall may be working to well.

Nutr0n :roll:

---

### Post by richbarna on 2006-06-30
[QUOTE=NutrOn]The error I got with gksudo was

***@ubuntu:~$ gksudo nautilus
(nautilus:6683): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I guess Bastille firewall may be working to well.

Nutr0n :roll:[/QUOTE]

You and everbody else too. Not to worry :-
[http://www.ubuntuforums.org/showthread.php?t=206247]("http://www.ubuntuforums.org/showthread.php?t=206247")

---

### Post by aysiu on 2006-07-01
[QUOTE=NutrOn]The error I got with gksudo was

***@ubuntu:~$ gksudo nautilus
(nautilus:6683): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I guess Bastille firewall may be working to well.

Nutr0n :roll:[/QUOTE] That "error" is a bug. *gksudo nautilus* works fine. Full explanation here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

