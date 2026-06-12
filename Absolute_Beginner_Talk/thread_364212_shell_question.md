---
title: "shell question"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by cmbigd4life on 2007-02-18
Hello,

I am trying to change my default shell from bash to csh via chsh.  When I run a "less /etc/shells" /bin/csh is included.  However, when I try and chsh to /bin/csh, I receive "/bin/csh is an invlaid shell."  Any ideas?

Thanks,

Corey

---

### Post by taurus on 2007-02-18
What's the output of this command at a prompt?

```
whereis csh
```

---

### Post by cmbigd4life on 2007-02-18
whereis csh returns

 csh:

Does this suggest that it is not installed?

---

### Post by Maestro23 on 2007-02-18
> **cmbigd4life said:**
> whereis csh returns

 csh:

Does this suggest that it is not installed?

Yes. Open Terminal

> sudo apt-get install csh

or 

sudo aptitude install csh

---

### Post by cmbigd4life on 2007-02-18
I just solved the problem by installing csh.

thanks,

---

