---
title: "username password"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by flippeddisc on 2007-02-18
I just installed Ubuntu 6.10.I didn't install the oem version.When I try yo log in it says log in failed or something.I know I'm using the right username and password that I entered during setup.Help?

---

### Post by taurus on 2007-02-18
Boot into the recovery mode from GRUB menu and paste the output of this command here.

```
ls -la /home
```

---

### Post by flippeddisc on 2007-02-18
when I type that in and press enter it says [invalid option]

---

### Post by taurus on 2007-02-18
What did you type in from the prompt?  It should be

```
**l**s -**l**a  /home
```
Those are lower case letters l as in larry.

---

### Post by flippeddisc on 2007-02-18
Maybe I don't understand what you mean by prompt.What I did was:


Boot in recovery mode.
typed in ls -la/home beside root@localhost:~#
Then pressed enter

---

### Post by Maestro23 on 2007-02-18
> **flippeddisc said:**
> Maybe I don't understand what you mean by prompt.What I did was:


Boot in recovery mode.
typed in ls -la/home beside root@localhost:~#
Then pressed enter

ls (space) -la (space) /home

---

### Post by taurus on 2007-02-18
Type that command after you see this prompt, root@localhost:~#.  And by the way, there is a space between -la and /home.

```
root@localhost:~# ls       -la          /home
```

---

### Post by flippeddisc on 2007-02-18
Ok, I was missing the spaces.Now its showing my username in blue letters.This is the username I have been typing in the log in screen. What about password?Sorry to be so much trouble.

---

### Post by taurus on 2007-02-18
Are you sure you use the right password?  Perhaps you need to change it.  While still in the recovery mode, run

```
passwd **username**
```
Replace the **username** with the same one that you use to log in, from the output of /home.

---

### Post by flippeddisc on 2007-02-18
got er done ,thank you so much for the help

---

