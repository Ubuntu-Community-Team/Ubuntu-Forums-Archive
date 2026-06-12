---
title: "Am I root?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jeisenst on 2007-05-15
Ok, I'm trying to run [$ apt-get install clamav] from the terminal and I keep getting a permission denied message followed by the simple question, am I root?  I don't know. Am I? I thought I was but, now I'm not so sure.  Can someone help me get my root back?

---

### Post by srt4play on 2007-05-15
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LaRoza on 2007-05-15
Append "sudo" before the command, as in "sudo apt-get install whatever", sudo will prompt you for your password, type it in, you won't see letters, so don't panic.

---

### Post by taurus on 2007-05-15
No, you are not root BUT you do have root privilege though.  So, if you want to install something, you need to use sudo with the same password that you log in with.

```
sudo apt-get update
sudo apt-get install clamav
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jeisenst on 2007-05-15
As always, thanks to everyone for their help.

---

### Post by rich.bradshaw on 2007-05-15
if you type 

whoami

it will tell you who you are....

---

### Post by Bachstelze on 2007-05-15
And if you need to *really* be root, type

```
sudo -i
```

---

