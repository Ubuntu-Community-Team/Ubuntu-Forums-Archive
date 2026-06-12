---
title: "Can't update or apt-get"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mitchbones on 2007-01-15
Fixed Problem! If anyone else has this problem, its caused by apt-get running out of virtual memory. Thanks to arnieboy in #ubuntuforums I solved it
```
 sudo gedit /etc/apt/apt.conf
 and add the following:
 APT::Cache-Limit 20000000;
```

----
I just tried updating some programs and got an error that said 
```
E: Dynamic MMap ran out of room
E: Error occurred while processing python-gnome2-extras (NewFileVer1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I close the window and it says "Fix broken packages"

Thanks for your help.

edit: When I try add or remove programs I get ```
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
``` When I try to use sudo apt-get update I get the first error.

---

### Post by scrooge_74 on 2007-01-15
how much room you have in the disk?

---

### Post by geezerone on 2007-01-15
sudo aptitude upgrade & sudo aptitude update?

---

### Post by Sef on 2007-01-15
Fixed.

---

