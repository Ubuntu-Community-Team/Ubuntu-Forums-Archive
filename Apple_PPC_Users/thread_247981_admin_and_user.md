---
title: "admin and user"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by rainbow_will on 2006-08-31
hi folks
I'm new to ubunto and I seem to have deleted my only admin account. What do I have to do to get one back? How do I login as root / sudo or whatever?

:)
will.

---

### Post by Paul41 on 2006-08-31
Did you delete the first account you created?  If not that account has root privileges.

---

### Post by rainbow_will on 2006-08-31
yes, I deleted the account I created during install.
I can still login to it, mind, but it doesn't give me admin privileges, apparently.

w.

---

### Post by Paul41 on 2006-08-31
Logging in with it does not automatically give you root permissions.  Have you tried to run any sudo commands with that account in the terminal?

If you really deleted the account then I don't have any ideas, but from what you said ("I can still login to it") it sounds to me like you should still have root access.

---

### Post by rainbow_will on 2006-08-31
Yes, well I deleted it in the "manage users and groups" program, but it hasn't completely gone.

---

### Post by rainbow_will on 2006-08-31
ok so I presume I can try to run the users and groups program from a command prompt as sudo. Where would I find the .exe for this please?

w.

---

### Post by Paul41 on 2006-08-31
I saw this post somewhere else that might help you.  The second post form nelz looks like it might help you.  In his example change "master" to your user.

[http://www.linuxformat.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=4039](http://www.linuxformat.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=4039)

---

### Post by Paul41 on 2006-08-31
Here is another way to do the same thing as my last post that might be easier.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by spinz8 on 2006-08-31
Hi rainbow_will
I had the same problem with you. Please read this thread to restore your admin privilege.
[http://ubuntuforums.org/showthread.php?t=238277](http://ubuntuforums.org/showthread.php?t=238277)
Kind regards

---

### Post by rainbow_will on 2006-09-01
Right, well I see that someone with root access can alter group structure. To do this, he needs to go into full power mode with sudo. However, when I login to the account-I-created-at-installation, it does not seem to want to run sudo, and it does not seem to have the ability to look at a file like sudoers, which is owned by root.

This strikes me as being v. illogical. Surely the system should recognize that this account has root privileges (ie is effectively root) and allow it to run sudo, whether it is in the admin group or not.:?: 

I guess I can try recovery mode, nevertheless i think I should not need to do this.

---

