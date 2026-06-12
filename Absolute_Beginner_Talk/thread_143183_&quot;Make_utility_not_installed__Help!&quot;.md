---
title: "&quot;Make utility not installed?  Help!&quot;"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by heislord5 on 2006-03-12
OK,

I try to run make and it says:

"bash: make: command not found"

Crap!  Why the heck isn't make installed with the distribution?  How do I get it?  I'm a newbie, how do I install it?

---

### Post by 5-HT on 2006-03-12
Hi, what you're looking for should be covered under the 'build-essential' package (includes 'make' plus some other needed utils for compiling).

It's on the install CD already, just not installed by default.
You can also grab it from the repositories.

*EDIT: didn't notice the question on how to install software...

Here is a nice link from the wiki that explains how to install software in Ubuntu:
[https://wiki.ubuntu.com/InstallingSoftware]("https://wiki.ubuntu.com/InstallingSoftware")

Here's another one that describes how to install build-essential:
[https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")

HTH

---

### Post by heislord5 on 2006-03-12
also, 

When I installed I gave a user name and password, but the "root" user.....it didn't ask me for a password for that I don't think.  Is there a default?

---

### Post by 5-HT on 2006-03-12
[quote=heislord5]also,

When I installed I gave a user name and password, but the "root" user.....it didn't ask me for a password for that I don't think. Is there a default?[/quote] 
For security purposes, Ubuntu has the root account locked by default and uses 'sudo' instead.

In order to do anything that would normally require root privileges, simply preface the command with 'sudo'.

When it asks for a password, it is asking for your user password.

If you really want to, you can set up a root password. 
But there is really no need as 'sudo' can do most things you require, and you can always get a root terminal if you like (doing so from within x: 'gksudo <favorite_terminal>).

If you want to launch a graphical application with root privileges, preface the command with 'gksudo' (like in the previous example).

Here's a link that explains this in detail:
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

*EDIT: Assumed you were using GNOME, but if you are using KDE (Kubuntu)...instead of 'gksudo' I believe the command is 'kdesu'


Hope this helps.

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=heislord5]also, 

When I installed I gave a user name and password, but the "root" user.....it didn't ask me for a password for that I don't think.  Is there a default?[/QUOTE]

That's normal, root is disabled by default. You can use the command "sudo" to access things that root can. Like "sudo apt-get update" then enter YOUR user password. This link can help you... [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

EDIT: Too slow.

---

### Post by heislord5 on 2006-03-12
Thanks.  That page explains a lot.  I'm just learning about how to install packages and about Synaptic Package Manager.  I'm going to do some more reading before asking more questions.

I tried Linux some years back and it was hard.  It still is, lol.  I just want to install my wireless network card, and to do that I'm downloading source, installing a compiler, compiling and then loading... lol.  Not like good old Microsoft that just gives me a one button click.

Anyway, I'm through griping.  I appreciate the community and helpfulness of people though.  Thanks guys/gals.

Brad

---

### Post by 5-HT on 2006-03-12
No prob.

Linux has come far in the past little while; Ubuntu particularly in terms of ease of use, default security/settings, and community support.
  
You may be surprised at how much better an experience you'll have this time around.

Some of the links in my sig may be of help to get yourself familiarized with GNU/Linux in general, and Ubuntu particularly.

Wireless can be a breeze if your card gets detected and configured properly in the install, but some of the time there just aren't any Linux friendly drivers put out by the manufacturer. Hopefully, you'll get it going once you get the driver installed, but if any issues remain there may be some ways to get around them.I don't have wireless myself and consequently wouldn't be of much help, but there are lots of friendly, knowledgeable people around these forums.

---

