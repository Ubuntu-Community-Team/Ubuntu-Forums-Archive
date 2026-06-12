---
title: "Login help"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by mayben on 2006-10-02
This is my first time installing a linux distro. After installing ubuntu it asks for a username and password. I try the one I created during installation but it doesn't work. What do I do?

---

### Post by taurus on 2006-10-02
Make sure the cap is not on since Linux is case sensitive!!!  Otherwise, you need to boot into single user mode, recovery mode, from GRUB and look in /etc/passwd to get the exact login name for your account.  Then, create a new password for it...

```

more /etc/passwd  <-- to view it
passwd john  <-- to create a new password for account john...

```

---

### Post by mayben on 2006-10-02
Thanks alot I got my correct username from that! :) :)

---

