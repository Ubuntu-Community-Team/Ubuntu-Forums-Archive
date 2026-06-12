---
title: "How do I change permissons?"
date: 2006-06-23
forum: Apple PPC Users
---

### Post by spencer on 2006-06-23
Hi, I have a cd disk that isn't accesible. Message says I do not have enough permissions to read the disk. This is running off a Ubuntu live cd and reading from an external cd drive. How do I change the permissions running from live cd to access these files? 

-spencer

---

### Post by tidris on 2006-06-23
[QUOTE=spencer]Hi, I have a cd disk that isn't accesible. Message says I do not have enough permissions to read the disk. This is running off a Ubuntu live cd and reading from an external cd drive. How do I change the permissions running from live cd to access these files? 

-spencer[/QUOTE]
You can try sudo nautilus in a terminal window.

---

### Post by spencer on 2006-06-23
That gives me the same message. I tried "sudo chown ubuntu user /location_of_files_or_folders". That didn't work either. Thanks!

-spencer

---

### Post by tidris on 2006-06-23
I assume you are getting the permissions error message when you try to browse the directory where the CD is mounted. What sudo nautilus would do is launch a file browser window with root privileges. From that window you should be able to access any file in any directory regardless of permissions or ownership.

---

### Post by spencer on 2006-06-23
Yes, that was the problem, got it working. Thanks again!

-spencer

---

