---
title: "Adding New Users in Ubuntu 7.10 Is Not Working As Expected"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2008-01-10
I'm having a problem adding new users to Ubuntu 7.10 and am not sure how to troubleshoot this problem.

Here's what happens:

Boot to computer, login as my user account which is configured with all of the User Privileges available.

I click on System > Administration > Users and Groups

The Users settings menu shows up and I see 2 accounts listed:

root
My Account

I click on "Add User"

In the New User account box, I provide a new username, real name, I select profile Desktop user, then I set the password by hand and click OK. 

New User Account box goes away and the screen returns to the User Settings - but the new user isn't listed.

Where do I begin troubleshooting this?

---

### Post by billgoldberg on 2008-01-10
Stupid question but did restarting x (ctrl+alt+backspace) or resetting the pc fix the problem?

---

### Post by PeterJS on 2008-01-10
I was having the same problem yesterday, it's probably a bug, and will hopefully be fixed in hardy if not sooner, but that's not a real good answer to the problem.

You could use the command line tools to create the user and then use the users manager to add them to groups, and set their password.
```

sudo adduser *username*

```

---

### Post by vortex0007 on 2008-01-10
no restarting X has no effect, but thanks for the suggestion

---

### Post by vortex0007 on 2008-01-10
If it is a bug where would I go to find out if someone is doing something about it? 

I can use the CLI but I'd rather have the GUI working.

---

### Post by PeterJS on 2008-01-10
Launchpad is the goto place to look for bug reports and things.

The user-admin tool is in the gnome-system-tools package, here's the current bug list:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/)

---

### Post by Hospadar on 2008-01-10
does it ask you for your password before it starts? if not, or even if it does, you could just give it a shot, try opening it from a terminal```
sudo users-admin
```This might also give you some insight if it's giving errors in the terminal that you wouldn't otherwise see

---

