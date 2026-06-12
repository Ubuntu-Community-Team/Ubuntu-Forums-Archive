---
title: "Change my ssh and nxserver remote access password ..."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-08-20
I tried to change my user password for ssh and nxserver remote access but it would not work.  I had to switch back to my old password in order for nxserver to function.  Anyone know what I need to do?

Thanks

Carl

---

### Post by dwhitney67 on 2007-08-22
> **cwmoser said:**
> I tried to change my user password for ssh and nxserver remote access but it would not work.  I had to switch back to my old password in order for nxserver to function.  Anyone know what I need to do?

Thanks

Carl

I'm not familiar with nxserver, so someone else will have to help you there.  As for SSH, I was unaware that there way a different password other than the one that is normally used to access (i.e. login to) an account.

When I attempt to connect via SSH, I use a command similar to the following:

[FONT="Courier New"]$ ssh -l remoteUser remoteServer[/FONT]

or

[FONT="Courier New"]$ ssh remoteServer[/FONT]

if the username on the remote system is the same as the local system.

In either case, the password requested is the login password on the remote system.

---

