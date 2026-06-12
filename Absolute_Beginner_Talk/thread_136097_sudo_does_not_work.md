---
title: "sudo does not work"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Pbl on 2006-02-25
Hi everyone,
something strange is happening with sudo in my installation: it doesn't work! It asks for a password, I type it in and nothing happens!
Any ideas, anybody? Thanks in advance!

Pablo

---

### Post by cilynx on 2006-02-25
What are you trying to do with sudo?

If you
```

sudo -s

```
you'll be dropped to a root prompt (after you enter password)

If you 
```

sudo [some command]

```
it will run that command as root, then drop you back to your user prompt.

What are you trying to do?

---

### Post by tseliot on 2006-02-25
[QUOTE=Pbl]Hi everyone,
something strange is happening with sudo in my installation: it doesn't work! It asks for a password, I type it in and nothing happens!
Any ideas, anybody? Thanks in advance!

Pablo[/QUOTE]
It's absolutely normal. It won't show you any "*" (or something like that) for any of the letters you type.

Just type the password and press Enter

---

### Post by tseliot on 2006-02-25
[QUOTE=cilynx]What are you trying to do with sudo?

If you
```

sudo -s

```
you'll be dropped to a root prompt (after you enter password)

If you 
```

sudo [some command]

```
it will run that command as root, then drop you back to your user prompt.

What are you trying to do?[/QUOTE]
I guess he refers to the installation process in which you have to set your password but nothing shows up as you type the letters

---

### Post by Pbl on 2006-02-25
To cilynx:
> What are you trying to do with sudo?
Anything! Maybe I didn't make it quite clear: sudo does nothing! I mean, it doesn't launch the apps or processes I try to start.
For example, this
```
sudo apt-get update
```
asks for the password, and then does nothing. The console prompt just returns.

To tseliot:
> It's absolutely normal. It won't show you any "*" (or something like that) for any of the letters you type.
Thanks, I know!

I'm stuck here. Thank you for replying.

Pablo

---

### Post by tseliot on 2006-02-25
[QUOTE=Pbl]To cilynx:

Anything! Maybe I didn't make it quite clear: sudo does nothing! I mean, it doesn't launch the apps or processes I try to start.
For example, this
```
sudo apt-get update
```
asks for the password, and then does nothing. The console prompt just returns.

To tseliot:

Thanks, I know!

I'm stuck here. Thank you for replying.

Pablo[/QUOTE]
Oh, you meant that.
Ok, it might be that you're not in the sudoers file

Boot in Recovery mode
then type:

nano /etc/sudoers

get to this part:
# User privilege specification
root    ALL=(ALL) ALL

and add your username just below it

your_username ALL=(ALL) ALL

then save (CTRL+O)
and exit (CTRL+X)

then type:
reboot

---

### Post by cilynx on 2006-02-25
TS:

Not being in the sudoers file should throw an error though.

And isn't the official way to get sudo access in Ubuntu to use the 'Users and Groups' admin panel and give yourself "access to run system programs" or such?  

To the best of my knowledge, you also can't edit the sudoers file with just a text editor.  Don't you have to use 'visudo'?  Maybe I'm just in the dark ages, dunno...

Pbl:

This is kinda stupid, but does gksu work?  It shouldn't as it relies on sudo, but you never know...

---

### Post by tseliot on 2006-02-25
[QUOTE=cilynx]TS:

Not being in the sudoers file should throw an error though.[/QUOTE]
I know that but I think he should try it if he wants to use sudo

[QUOTE=cilynx]And isn't the official way to get sudo access in Ubuntu to use the 'Users and Groups' admin panel and give yourself "access to run system programs" or such?[/QUOTE]
Don't you need root's authorisation to do that?

[QUOTE=cilynx]To the best of my knowledge, you also can't edit the sudoers file with just a text editor.  Don't you have to use 'visudo'?  Maybe I'm just in the dark ages, dunno...[/QUOTE]
It's not that you "can't" do that but you "shouldn't" do that because it's not 100% secure. Nonetheless I've solved many problems also without visudo and I haven't had any problems.

Oh, and I'm sure you're more experienced than me since I have used Linux for almost a year ;) .

---

### Post by cilynx on 2006-02-25
The sudoers hack is a good thing to try, yes.

Also, just checking to see if 'su' works would be a good thing.  That'll at least get you root access.

You do need root access to run the Admin Panel, yes.  That's why I was curious if gksu worked.

I'm pretty sure I've had sudo get writhing mad at me for editing the sudoers file without using visudo, but I don't have any idea what distro that was on.

TS:

Don't knock your "almost a year" of experience.  You seem to have picked up a lot and it's great that you're sharing said knowledge.  I've been playing w/ Linux since Slackware 3.0, but most of what I know is obscure command line and automation crap that doesn't make a lick of sense to someone on a desktop driven distro.

Cheers --

---

### Post by cilynx on 2006-02-25
Also, a technical aside for the googlers out there:

Ubuntu doesn't believe in adding individual users to the sudoers file.

Here is my sudoers:

```

rcw@pyth:~$ sudo cat /etc/sudoers
Password:
# /etc/sudoers
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

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
rcw@pyth:~$

```

As you can see, there's only "root" and the "admin" group.  When you go into the "Users and Groups" admin panel, that list of "things you can do" is technically a list of groups to put your user into.  Checking "Executing system administration tasks" is really just adding you to the "admin" group, which then because of the sudoers file setup lets you run sudo.

Continuing on my digression, adding a user to the sudoers file will still work fine as TS said above.  Although this isn't the "prefered method for Ubuntu", Ubuntu is still Linux so normal Linux tricks and theories still work.

Hopefully that didn't make things too much more confusing...

---

### Post by tseliot on 2006-02-25
[QUOTE=cilynx]As you can see, there's only "root" and the "admin" group.  When you go into the "Users and Groups" admin panel, that list of "things you can do" is technically a list of groups to put your user into.  Checking "Executing system administration tasks" is really just adding you to the "admin" group, which then because of the sudoers file setup lets you run sudo.[/QUOTE]

Very interesting. Thanks for sharing :)

---

