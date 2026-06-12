---
title: "Admin Login"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by 4-PackDad on 2008-04-15
Hey;

I just installed Ubuntu 7.10 about a whole 1 1/2 weeks ago.

So far so good, just a few bumps.

I have '3' diff user accounts set up.
'1' admin + '2' other users.

Problem:
I can not look/read my other drives under a 'non-admin' login.

Cannot mount volume.
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy.
hal_storage_fixed_mount refused uid 1002

I can switch to my admin login, access the drive, log-out and back into the 
non-admin user account,
and
then I can access the drive.

My admin password will Not work under a non-admin user account.

Same problem when trying to install Plugins.

What am I doing wrong.

Thnx,
Bill

---

### Post by Xiong Chiamiov on 2008-04-15
As far as being able to access your drives from the other accounts, you'll need to change the permissions on them.  You can either do it with the GUI (right-click -> properties -> permissions? sorry not familiar with gnome) or with the command-line (chmod).  I (or many other people here) can help you out with the specifics of chmod if you need to do it that way.

---

### Post by GCoffee on 2008-04-15
Your administrator account password and your administrative password are two different things.. you set your administrative at the ubuntu setup...

---

### Post by 4-PackDad on 2008-04-16
> **GCoffee said:**
> Your administrator account password and your administrative password are two different things.. you set your administrative at the ubuntu setup...

Ok, I understand but then I don't see the it.

What I consider my Administrator Account has Administer System 'checked' under Privileges.

While, my other user accounts do not have this checked.

So, how are the '2' passwords different.

How do I fix this...?

I never messed with this under XP,
Cause it never worked like I thought it should.
To me the User Accounts work like they ought under Ununtu.

Thnx,
Bill

---

