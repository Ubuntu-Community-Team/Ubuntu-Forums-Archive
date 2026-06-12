---
title: "[SOLVED] Super user privileges"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-08-07
I'm sick and tired of using "sudo" on every command in the terminal (for it appears that my user has minimal privileges). How can I make my user have sudo privileges by default so I don't have to keep typing sudo every line?

Thanks :)

---

### Post by overdrank on 2007-08-07
> **kbsuperstar said:**
> I'm sick and tired of using "sudo" on every command in the terminal (for it appears that my user has minimal privileges). How can I make my user have sudo privileges by default so I don't have to keep typing sudo every line?

Thanks :)

HI 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-08-07
> **kbsuperstar said:**
> I'm sick and tired of using "sudo" on every command in the terminal (for it appears that my user has minimal privileges). How can I make my user have sudo privileges by default so I don't have to keep typing sudo every line?

Thanks :)
Type ```
sudo -i
``` Then you will have a root shell and won't have to keep retyping *sudo* over and over.

---

### Post by kbsuperstar on 2007-08-07
Thanks! This is just what I needed :)

---

