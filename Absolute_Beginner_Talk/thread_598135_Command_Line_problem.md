---
title: "Command Line problem"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by oscarthefish on 2007-10-31
Have been trying to learn the basics of the Command Line and so i typed out: "su" i was asked for the password which i duly typed in but was rewarded with: Authentication failure Sorry. Could someone tell me what's going on here please. Thanks!

---

### Post by swisscow on 2007-10-31
Me too - ??????????????

---

### Post by swisscow on 2007-10-31
This is the reason (should have looked myself first)
[HTML]
Are you sure that you are not confusing su with sudo?
su asks for the root password, sudo asks for the users password.
When for instance synaptic asks for a passwords it's done with sudo and not su.
By default Ubuntu doesn't create a password for root, since everything is expected to be done through sudo. "sudo su" will actually do what you want to with su[/HTML].

---

### Post by Sensenseppl on 2007-10-31
Ubuntu uses sudo, to gain root access for a short time. If you really want to login as root, which is not recommended, use "sudo su".

---

### Post by CSMatt on 2007-10-31
"Su" asks for the root password, which is locked by default.  You'll need to use "sudo" instead.  The "sudo" command asks for your password.

---

