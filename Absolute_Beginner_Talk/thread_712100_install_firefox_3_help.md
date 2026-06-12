---
title: "install firefox 3 help"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by slickh20 on 2008-03-01
ok i downloaded and went to put in the command in the terminal to install and this is what i get (the download is on the desktop.

i dont know what any of this means.  thanks

casey@desktop2:~$ sudo tar -C /opt -jxvf /home/username/Desktop/firefox-3.0b3.tar.bz2
tar: /home/username/Desktop/firefox-3.0b3.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
casey@desktop2:~$

---

### Post by Nepherte on 2008-03-01
Just read the error: **No such file or directory**.
You stated the file is in /home/username/... but you should replace username with **your** username.

---

### Post by taurus on 2008-03-01
What is your login name, casey or username?

What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by spiderbatdad on 2008-03-01
looks like you are in the wrong PWD. Try cd into Desktop before untarring. I see your host is called Desktop2 (very tricky), but you are in fact in ~$.

---

### Post by slickh20 on 2008-03-01
you guys are so smart maybe next time i will just try to look at what i put in.

thanks

---

