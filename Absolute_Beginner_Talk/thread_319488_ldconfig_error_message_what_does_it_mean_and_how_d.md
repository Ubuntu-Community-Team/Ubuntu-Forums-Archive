---
title: "ldconfig error message: what does it mean and how do I fix it?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by whein on 2006-12-15
I installed wine on my edgy box last night (that sounds so dirty taken out of context) and while the install itself seemed to go through there were error messages that I'd like to know what they mean and if I should do something about them.
I used [_https://help.ubuntu.com/community/WineForAMD64_]("https://help.ubuntu.com/community/WineForAMD64") as a guide and tweaked it for wine 0.9.27.  But during installation and afterwards I keep getting
```
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link
```
Wine seems to run fine with the one program I tried it with (UltraEdit32) but I'd like to at least understand the error message, and what I should do to fix it.  Anyone know?
-Will

---

### Post by Hershey on 2007-02-02
Not sure if you're still looking for a solution or not, but I was running into the same issue.  Doing the following seems to have fixed it:

```

sudo rm /usr/lib32/libXxf86dga.so.1
sudo ln -s /usr/lib32/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1
sudo ldconfig

```

It removes the file which it complains isn't a symbolic link, creates a symbolic link to the file I'm guessing it should be a symbolic link to (follows the same idea as the rest of the files in /usr/lib32), and then update the symbolic links.

---

