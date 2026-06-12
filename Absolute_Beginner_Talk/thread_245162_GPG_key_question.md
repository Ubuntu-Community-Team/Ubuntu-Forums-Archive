---
title: "GPG key question?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by spiral777 on 2006-08-27
I have a desktop currently, and that is where I run all my programs. I will be transferring over to a new laptop tomorrow, and my desktop will go away. I need to move all my stuff over to the laptop, including my gpg key, how do I do that?

---

### Post by jordanmthomas on 2006-08-27
If you're just wanting your trusted keys for apt-get, you need to copy /etc/apt/trusted.gpg into /etc/apt on your new computer.

As for moving all of your other stuff, my way wouldn't be too elegant so I'll just let someone else handle that part.   ;)

---

### Post by spiral777 on 2006-08-27
Any other hints? I really don't want to lose my key and have to resubmit everything.

---

### Post by kernelpanicked on 2006-08-27
If you are referring to your personal gpg key, copy $HOME/.gnupg to the other machine and you're golden.

---

