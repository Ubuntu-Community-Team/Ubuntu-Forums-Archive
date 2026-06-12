---
title: "no admin privileges?"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by myownrequiem on 2005-09-09
[FONT=Arial]I'm having a few problems with Ubuntu(Hoary Hedgehog).  I just installed it and I'm dual-booting with Windows XP Pro.
When I log on I get the following message:

Could not look up internet address for (my computer name).
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding (my computer name) to the file /etc/hosts.

Also I can't do any administrative tasks.  Several features like "Users and Groups" just don't open when I click them and if I try to use sudo for anything it says I'm not on the sudoers list, which of course is read-only and belongs to root.....

I don't know if these problems are related, but help with either or both would be appreciated.

(I'm pretty much a Linux n00b so I may be doing something dumb)

Thanks in advance[/FONT]

---

### Post by mlomker on 2005-09-09
By default the root password is the same as the user that you created during login.  You might want to read through the [wiki--lots of good stuff in there.](https://wiki.ubuntu.com/UserDocumentation)

---

### Post by Juergen on 2005-09-09
> By default the root password is the same as the user that you created during login.That's not quite right, I think.
By default the root password is disabled - the hash stored for it is '*' which is a value that the hash-function never gives as result, so no password will match.

> if I try to use sudo for anything it says I'm not on the sudoers listThis problem seems to hit some people after an 'expert' install.

The reasons could be either the group 'admin' is not in /etc/sudoers or your user is not a member of this group - or maybe the group 'admin' is missing at all.

The only way I know to correct this would be to boot into 'recovery mode' with grub or boot a live-CD and edit the files from there...

Since you can't look at /etc/sudoers, open a terminal and do a
```
less /etc/group | grep admin
```and post the results here.
(I still have the old 'warty' setup for sudoers with all users listed seperately, so maybe someone with a hoary-config could post the needed entry for the group 'admin')

---

### Post by myownrequiem on 2005-09-10
OK, I typed in that command and got back:

lpadmin:x:107:(my username)

After a bit of fiddling I found that there is no group actually called admin, but I belong to a group called adm (short for admin?).  There is also a group called sudo which I am not in.  I guess I can edit this file from recovery mode, but ...err....how?

---

### Post by Juergen on 2005-09-10
Probably the easiest would be to create the 'old' warty setup, where you user is explicitly in /etc/sudoers.
For this, boot to 'recovery mode' and do
```
export EDITOR=nano && visudo
```
Then add a line at the end like
```
your_username	ALL=(ALL) ALL
```
save, reboot, and you should be able to do admin tasks with sudo.

Then, if you want the newer setup, create a group admin, make your user a member of it, and change your_username to %admin in /etc/sudoers (with 'sudo visudo' this time).
(and do a 'man sudoers' before changing anything, I'm no expert here ;-))

---

### Post by Muhammad on 2005-09-10
Do what Juergen said,

Or simply:

[list]Ctrl+Alt+F1[/list]

[list]Username: root Password: The shadow password you choosed during installation.[/list]

[list]```
visudo
```[/list]

[list]At the end of the text, type ```
(your username) ALL=(ALL) ALL
```[/list]

[list]Ctrl+O[/list]

[list]Ctrl+X[/list]

[list]Ctrl+Alt+F7[/list]

You should have admin previlges now, and you don't need to reboot. ;)

---

### Post by Juergen on 2005-09-10
> Username: root Password: The shadow password you choosed during installation.**Did** the Setup ask for a root-pw?
Then of course this is a simpler way.

If not, you have to go to 'single user'/'recovery mode'.

---

### Post by Muhammad on 2005-09-10
Yes it did for me. :)

But if he forgot the root password he typed during installation, then he has no choice but to use recovery mode.

---

### Post by myownrequiem on 2005-09-10
Right.  I'm now on the sudoers list and i can use commands like chown.  These commands work but every time I do it it says "cannot look up host (my hostname) by gethostbyname()".

And I still can't open features like Users and Groups.

---

### Post by Muhammad on 2005-09-10
Here's my sudoers list

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
muhammad ALL=(ALL) ALL

try pressing "F2" instead of "Ctrl+O" when you're done editing your sudoers list.

---

### Post by Juergen on 2005-09-10
> cannot look up host (my hostname) by gethostbyname()That's unrelated to the 'sudo' problem IMHO.

Look at /etc/hostname - it should contain your hostname (go figure ;-))
and /etc/hosts - it should contain a line like
> 127.0.0.1 localhost.localdomain localhost <yourhostname>for '<yourhostname>' you can have several entries/aliases that all should be resolved to your box' internal ip-address

---

### Post by myownrequiem on 2005-09-11
Yup.  That's fixed everything I mentioned.  Works fine now.  Thank you all.

---

### Post by mlomker on 2005-09-11
[QUOTE=Juergen]That's not quite right, I think.
By default the root password is disabled - the hash stored for it is '*' which is a value that the hash-function never gives as result, so no password will match.
[/QUOTE]

By default the user that you create during install is a member of the **admin** group and that group is listed in the /etc/sudoers file.  There isn't a need to get that technical with most posters on here--they just need things to work...and you guys took care of that.   :-D

---

### Post by Muhammad on 2005-09-22
NOTE: you can set a root password during installation if you choose expert mode. ;)

---

### Post by Juergen on 2005-09-22
The problem seems to be that your first user isn't made a sudoer if you do an 'expert' install.
So all newbies chosing expert (because of the partitioning, or whatever) are lost if they try to follow the usual guides.

But maybe 'recovery mode' wasn't needed then.

I upgraded to Hoary and AFAIR my Warty expert install disabled root and created a sudoer (but I might remember wrong, these things I work around without much thinking - but for real noobs this is a problem, of course)
Maybe I'll do a fresh install with breezy, just to see how it works (but I love the ability to just upgrade with apt, so just maybe...).

---

