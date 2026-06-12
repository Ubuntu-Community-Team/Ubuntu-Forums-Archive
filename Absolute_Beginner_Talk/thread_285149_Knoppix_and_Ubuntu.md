---
title: "Knoppix and Ubuntu"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by HowardB on 2006-10-26
Ubuntu is installed on my son's computer. He can't remember his USERID or Password. I'd like to copy his data files on the hard drive. I booted the computer with Knoppix, but it didn't detect anything on the hard drive. How can I copy data files on an Ubuntu computer without entering the correct USERID and PW?
    HowardB

---

### Post by doobit on 2006-10-26
In Ubuntu, you can reboot and Esc to grub to log on as root using the recovery mode. His data folder should be in the /home directory and should be named the same name as his user ID so that's part one. As root, in a terminal, you can change his password to something new, without knowing the old password.
```
passwd <username>
```
you will then be prompted to enter a new password and confirm it.

---

### Post by HowardB on 2006-10-27
It worked beautifully! Thanks.

---

