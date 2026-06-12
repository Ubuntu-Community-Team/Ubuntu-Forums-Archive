---
title: "Is SUDO risky?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-10-23
Suppose I use "sudo whatever" to run a command as root, and then 10 seconds later I start up Firefox and browse to some malicious site by mistake.  Am I perhaps still running with full root privs at that point?  That would of course be a bad thing if exploit code could be run under my account, and have full root privs without even being prompted for another password.

If I'm right in being worried about this or similar issues, is there an easy way to simply configure 'buntu to use the more standard Unix-type commands and to simply not use the SUDO command at all?

Tks,
Bob

---

### Post by Dr Small on 2007-10-23
> **RTrev said:**
> Suppose I use "sudo whatever" to run a command as root, and then 10 seconds later I start up Firefox and browse to some malicious site by mistake.  Am I perhaps still running with full root privs at that point?  That would of course be a bad thing if exploit code could be run under my account, and have full root privs without even being prompted for another password.

If I'm right in being worried about this or similar issues, is there an easy way to simply configure 'buntu to use the more standard Unix-type commands and to simply not use the SUDO command at all?

Tks,
Bob
Hello. Please take a look at this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Dr Small

---

