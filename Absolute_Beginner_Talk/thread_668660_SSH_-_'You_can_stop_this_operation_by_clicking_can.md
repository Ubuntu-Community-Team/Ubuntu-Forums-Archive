---
title: "SSH - 'You can stop this operation by clicking cancel'"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-01-15
SSH was working fine...

Places => Connect to server etc.

Now, once I've created the SSH icon, and click it, I get the message:

[B]Opening "mydomain.com (for example)"

You can stop this operation by clicking cancel.[/B]

The only button to press is cancel, so to proceed I have to press cancel, which ends the operation.

On an early post it was suggested that one deletes a file called .ssh, but that doesn't do any good.

So, any suggestions?

Thanks.

---

### Post by barney385 on 2008-01-15
Have you done a kernel upgrade recently?

---

### Post by getmeoutofhere on 2008-01-15
No, I've done nothing.  It was working an hour ago.  I tried logging into a different account, and now nothing works.  Can't get past this cancel box, regardless of who I log into.

---

### Post by PinkFloyd102489 on 2008-01-15
Try ssh'ing from the command line.

```
ssh hostname/ip
```

---

### Post by getmeoutofhere on 2008-01-15
No, it doesn't work.  I tried to two different servers, and both didn't prompt me for a username, they instead wanted the password.  So I couldn't get in.  I can get in, though, using Filezilla.

---

### Post by hellion0 on 2008-01-15
> **getmeoutofhere said:**
> No, it doesn't work.  I tried to two different servers, and both didn't prompt me for a username, they instead wanted the password.  So I couldn't get in.  I can get in, though, using Filezilla.That's because it's assuming your machine's username is the SSH username.

Try either this:

```
ssh -l <username> <hostname.or.ip>
```

...or the easier:

```
ssh <username>@<hostname.or.ip>
```

...on the command-line.  It will then prompt you for a password and connect normally.

---

### Post by getmeoutofhere on 2008-01-15
hellion0,

Yes, that works, thanks.

Of course there is sitll the question of how to get SSH working from Places => connect to server.

---

### Post by getmeoutofhere on 2008-01-15
Presumably my SSH 'Connect to Server...' must be corrupted in some way.  Can it be removed and reinstalled?  Or is there some cache that needs clearing out?

---

