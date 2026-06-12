---
title: "sudo not working"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by unbuntu on 2006-04-08
I found this problem when I was trying to lauch "Applications->Add Applications" from the menu when logged in as user.  But after I entered root(admin) password, gnome-app-install doesn't start up, and I get no error messages.  This happens everytime when I, logged in as user, try to access admin functions like update, add app and others.  Then I tried in the terminal by typing "sudo gnome-app-install", but the same thing happens again:  it asks me for password, and after I enter the correct password, nothing happens...but my root account is definitely working, since I can launch these admin apps by switch to root (su), and then type "gnome-app-install" (or others).  So what's the possible cause of this?

This is my /etc/sudoers file, and I haven't touched it since installation.
```

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

```

Many thanks in advance!

---

### Post by trent dillman on 2006-04-08
Boot into recovery mode and add this:
```

%admin  ALL=(ALL) ALL

```

You probably did an expert install. If you can su, you set up a root account.

---

### Post by unbuntu on 2006-04-08
[QUOTE=trent dillman]Boot into recovery mode and add this:
```

%admin  ALL=(ALL) ALL

```

You probably did an expert install. If you can su, you set up a root account.[/QUOTE]

Must I do this in the recovery mode?  Can I use visudo instead and reboot afterwards?

Yes, I did an expert install, and I did activate the root account.  I thought expert install would give me an option to choose which packages I would like to install, but it didn't, and installed the same base system anyway...

---

### Post by trent dillman on 2006-04-08
No, you can use root.

---

### Post by unbuntu on 2006-04-08
Well...I added the line and reboot, but it doesn't work...still nothing happens after I sudo stuff...

---

### Post by ubuntuuser on 2006-04-08
Have you tried adding ```
 unbuntu    ALL=(ALL) ALL
```to the sudoers file?

---

