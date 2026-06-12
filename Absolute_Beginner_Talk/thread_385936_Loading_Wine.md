---
title: "Loading Wine"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Mike Daniels on 2007-03-16
Trying to load Wine in 6.06 and get the following message:

mike@mike-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:14244): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Any ideas? I have no knowledge of computers and am following the instructions in the Dapper guide.

Thanks

Mike

---

### Post by ironfistchamp on 2007-03-16
Just a question, but does gedit actually load up? I'm not sure if that is the same message, but there is one message that I get (and other people aswell) when using gksudo that can be ignored. I think it is the one you are getting there.


HTH

Ironfistchamp

---

### Post by jhenager on 2007-03-16
Here's what I would try:
sudo gedit /etc/apt/sources.list

I have seen the gksudo command, and am using Gnome, but always use sudo.

The other thing I would try if you are still getting errors is simply gedit, to see if that works.

---

### Post by eljalill on 2007-03-16
As far as I can see, this does not connect to wine, but to gksudo gedit .
So, you could try editing your sources.list with nano
(code: sudo nano sources.list) . which would let you get wine anyway.
And you could see, whether this gksudo gedit error also occurs, when you try to open another file with it.
 Nano is a little harder to use, but basically the instructions are at the bottom of the page that opens in the terminal when you type that command.

---

### Post by jhenager on 2007-03-16
> **eljalill said:**
> As far as I can see, this does not connect to wine, but to gksudo gedit .


Right. I think he is getting stuck at step one.

BTW, wine can be installed through Add/Remove. Much easier.
That's one thing that I still complain about with Linux. You go to install something, and you get all caught up in tar -vsfx, or missing dependencies, or no gcc compiler, and after a couple of hours wrangling with it, you forget what you started out to do in the first place.

---

### Post by eljalill on 2007-03-16
But to get the newest wine version, the wine respository has to be addes to sources.list.... and that would also go for add/remove, would it not?

I agree with you on the issue of lengthy and complicated installations... but mostly that only goes for more exotic stuff. I still find 98% of what I want in synaptics.

But to not change the topic.. 
Mike Daniels: Did you succeed in editing sources.list ? Need more help or all set?

---

