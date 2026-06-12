---
title: "rpm command not found?"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-01-23
I tried installing Limewire on my 64-bit distro today.  It came as an rpm file, which is fair enough.  However, i can't run it from the command line.

I opened the terminal, gained root access, and typed:

> rpm -i LimeWireLinux.rpm

However, it gave me the error messsage that:

> bash: rpm: command not found

A while ago i was able to install files like this on another Ubuntu box with no problems at all.  Is there a file/program i missing to enable the rpm command?

---

### Post by earobinson on 2006-01-23
Ubuntu dose not use rpm's it use deb files. The command to install a deb file is sudo dpkg -i <debfile>

Note: you only need the sudo to get root axcess. the install command is just dpkg. man dpkg for more info. you could also look at uning alian to try and convert the rpm to a deb. I think the syntax is alian LimeWireLinux.rpm, but im not on my ubuntu box so I cant check, you can man alian for more info

---

### Post by dueY on 2006-01-23
Try

```
sudo alien -k LimeWireLinux.rpm
``` to make the .deb file. Then do what earobinson said.

---

### Post by earobinson on 2006-01-23
lol just as I added in the edit.

---

### Post by Perfect Storm on 2006-01-23
Alien is not installed by default.

```
sudo apt-get install alien
```

Remember that Java is needed to run Limewire.

---

### Post by Leigh on 2006-01-23
[Here's how to install an RPM]("https://wiki.ubuntu.com/rpm?highlight=%28rpm%29"). It's in the Wiki.

---

