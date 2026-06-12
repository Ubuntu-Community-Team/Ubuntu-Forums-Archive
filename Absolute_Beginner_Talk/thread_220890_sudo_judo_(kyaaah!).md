---
title: "sudo judo (kyaaah!)"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by hookysun on 2006-07-22
dear sensei, how can it be that though i can log in as root and know the password still it is the case when logged in as a regular user i find that the sudo command knows not the password or behaves as if i don't know it?
to install something for instance i am perpetually logging entirely out of my account instead of the awfully handy sudo command.

---

### Post by slimdog360 on 2006-07-22
Youll have to say that again, but I like your enthusiasm.

---

### Post by adam.tropics on 2006-07-22
because sudo doesn't want your root password, it wants your user password.

---

### Post by Ctrl+Alt+Del on 2006-07-22
well the point behind sudo is its ability to give root like permission without having to hand over the password. In Ubuntu's case you can run any command, but that is not generally the case. Have a look at /etc/sudoers you can give permissions on a application basis if desireable

---

### Post by jimmygoon on 2006-07-22
> **hookysun said:**
> dear sensei, how can it be that though i can log in as root and know the password still it is the case when logged in as a regular user i find that the sudo command knows not the password or behaves as if i don't know it?
to install something for instance i am perpetually logging entirely out of my account instead of the awfully handy sudo command.

Er... Are you saying that you don't think that sudo is recognizing that you're typing?

Just type it in and Press Enter... there are no stars or letters/numbers, but it IS accepting your password (unless it says Incorrect Password)

---

### Post by skale on 2006-07-22
ever done this?

**sudo passwd root**

---

### Post by steve.horsley on 2006-07-22
Firstly, sudo wants your password, not root's password.
Second, it only allows those who belong the group admin.

---

