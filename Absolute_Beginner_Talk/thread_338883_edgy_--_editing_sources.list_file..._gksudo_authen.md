---
title: "edgy -- editing sources.list file... gksudo authentication fails [Resolved]"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Charlie Wilkes on 2007-01-15
I want to add a source to my sources.list file, but when I type:

gksudo gedit etc/apt/sources.list

a dialog pops up asking for my password, and then the console displays the following message:

(gedit:6090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then I can't save the changes to the file.

I tried setting up a root acct., but Ubuntu won't let me log in as root.

How do I get around this to get the permissions I need to edit my system files?

Thanks for your time & attn.

Charlie

---

### Post by macogw on 2007-01-15
I think it's gksu, not gksudo.  Try that.

---

### Post by jvc26 on 2007-01-15
When it asks for a password, put in your own password. Ignore that error message it pops up all the time, has been reported and marked as low priority and so will be fixed one day or another. Try it again, with the gksudo command, then put in your user password (thats also the sudo password) I wouldnt advise enabling a root account as that makes your computer more vulnerable.
Hope that helps,
Il

---

### Post by jvc26 on 2007-01-15
> **macogw said:**
> I think it's gksu, not gksudo.  Try that.
gksudo and gksu both work on my computer, and the standard command put up on things like ubuntu guide is gksudo. :)
Il

---

### Post by Jussi01 on 2007-01-15
If your using gnome, you can also add sources by clicking system -> Software sources -> third party (tab)

HTH

---

### Post by aysiu on 2007-01-15
> **Charlie Wilkes said:**
> I want to add a source to my sources.list file, but when I type:

gksudo gedit etc/apt/sources.list

a dialog pops up asking for my password, and then the console displays the following message:

(gedit:6090): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then I can't save the changes to the file. Have you tried ```
gksudo gedit /etc/apt/sources.list
``` instead of ```
gksudo gedit etc/apt/sources.list
```?

---

### Post by Charlie Wilkes on 2007-01-15
> **Illuvator said:**
> When it asks for a password, put in your own password. Ignore that error message it pops up all the time, has been reported and marked as low priority and so will be fixed one day or another. Try it again, with the gksudo command, then put in your user password (thats also the sudo password) I wouldnt advise enabling a root account as that makes your computer more vulnerable.
Hope that helps,
Il

Thanks, but it doesn't work.  It's not just a matter of getting the error message -- gedit will not let me save the file.  Here is what happens:

1.  I type the command:
gksudo gedit /etc/apt/sources.list

2.  A box pops up requesting my password, which I type in.

3.  I get the error message in the console.

4.  Gedit launches and I edit the sources.list file

5.  When I attempt to save the sources.list file, gedit displays the following message:

Could not save the file /etc/apt/sources.list
You do not have the permissions necessary to save the file.
Please, check that you typed the location correctly and try again.

So, how do I get the permissions necessary to edit and save this file???

Charlie

---

### Post by aysiu on 2007-01-15
Is it possible that you're not in the admin group? Or that something's wrong with your /etc/sudoers file?

More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Are you able to successfully save it if you use *nano* instead of *gedit*? ```
sudo nano -B /etc/apt/sources.list
```

---

### Post by Charlie Wilkes on 2007-01-15
> **aysiu said:**
> Have you tried ```
gksudo gedit /etc/apt/sources.list
``` instead of ```
gksudo gedit etc/apt/sources.list
```?

](*,) I guess that was it... a syntax error.  I managed to edit and save the file and update apt. 

Thanks so much for pointing that out.  I've got a nice system going here with "edgy."

Charlie

---

