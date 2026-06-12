---
title: "Forgot Password"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-07-26
I forgot my password, what can I do to reset it?

---

### Post by wolfen69 on 2007-07-26
[http://www.linuxforums.org/security/howto:_recover_root_password.html](http://www.linuxforums.org/security/howto:_recover_root_password.html)

---

### Post by aysiu on 2007-07-26
> **wolfen69 said:**
> [http://www.linuxforums.org/security/howto:_recover_root_password.html](http://www.linuxforums.org/security/howto:_recover_root_password.html)
That's for recovering the *root* password. Ubuntu doesn't have a root password by default. This is the user password.

**Step 1**
Boot into recovery mode. It's usually the boot option right below the one you usually pick. This will make you root at the terminal.

**Step 2**
Type ```
passwd *username*
``` where *username* is your username. You'll be prompted for a new password.

**Step 3**
Type ```
reboot
```

---

### Post by rscott5 on 2007-07-26
Another method would be to append "single" to the end of the line beginning with kernel in the GRUB boot menu. This will automatically log you in as root without prompting for password and you can then change the password of your user by typing passwd *username*. It's scary how easy it is to get into a Linux machine and change the password by doing this, but I just keep reminding myself, physical access = root access. The only way to protect against this is to password protect the GRUB.

---

### Post by Cypher on 2007-07-26
> **rscott5 said:**
> Another method would be to append "single" to the end of the line beginning with kernel in the GRUB boot menu. This will automatically log you in as root without prompting for password and you can then change the password of your user by typing passwd *username*. It's scary how easy it is to get into a Linux machine and change the password by doing this, but I just keep reminding myself, physical access = root access. The only way to protect against this is to password protect the GRUB.

This is what the "Recovery Mode" option in the GRUB menu does in Ubuntu. It is safer to use the menu option as opposed to messing up the default boot option during editing..

---

