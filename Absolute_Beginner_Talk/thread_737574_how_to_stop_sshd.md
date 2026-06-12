---
title: "how to stop sshd ?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by dvds on 2008-03-27
Hello Forum,

I'm quite new in the ubuntu-world, and have one small question: when executing "/etc/init.d/ssh stop" I expected to see every ssh connection closed and no new allowed, but depite the "OK" everything continues to work... can somebody help me?

Thank you.

---

### Post by keelerm on 2008-03-27
Are you getting any errors when you issue that command?  And are you issuing this command as root?

---

### Post by dvds on 2008-03-27
> **keelerm said:**
> Are you getting any errors when you issue that command?  And are you issuing this command as root?

 * Stopping OpenBSD Secure Shell server sshd                  [ OK ]

No errors, I'm trying as root and via a php script, so with the standard Apache user, same result... :-k :|

---

### Post by keelerm on 2008-03-27
And you can still spawn new connections, or are currently connected sessions maintained?

---

### Post by dvds on 2008-03-27
> **keelerm said:**
> And you can still spawn new connections, or are currently connected sessions maintained?

Both, that's the problem...

---

