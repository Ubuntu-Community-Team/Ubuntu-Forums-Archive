---
title: "Scanner Trouble"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2007-02-19
I posted in the thread about the Canon Pixma MP500, but I thought I would try here, too. Below is a link to my post.

[http://ubuntuforums.org/showpost.php?p=2180086&postcount=12]("http://ubuntuforums.org/showpost.php?p=2180086&postcount=12")

---

### Post by 42Wired on 2007-02-19
I still need help with this, if anyone has any ideas.

---

### Post by Bachstelze on 2007-02-19
Your scanner seems to be supported by SANE. I guess it would be simpler to use that.

```
sudo apt-get install sane-utils
```

then try to run *sane-find-scanner* and see if it detects something, run it with sudo if necessary.

---

### Post by 42Wired on 2007-02-20
When I use this command with apt-get, it tells me that the package is not available or referred to by another package, and that the package sane-utils is missing, obsolete, or I need to get it from another source.

When I use aptitude with this command, it tells me that there was no candidate version found.

---

### Post by 42Wired on 2007-02-20
I got it. Apparently, you need to be in the directory you extracted the downloaded archive to.

```
cd /tmp/mp150-0.12.2
```

and then enter the [FONT="Courier New"]./scan[/FONT] command.

---

