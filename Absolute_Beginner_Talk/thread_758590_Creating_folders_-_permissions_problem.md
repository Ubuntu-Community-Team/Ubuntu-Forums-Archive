---
title: "Creating folders - permissions problem"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by superjacent on 2008-04-18
I've just installed XAMPP to /opt/lampp/ and localhost is pointing to /opt/lampp/htdocs.

What is the easiest way for me to create folders and files under htdocs.   At the moment using the File Browser I don't have the necessary permissions.   Can I some how temporarily act as root so as I can create folders and upload files.

---

### Post by george9233 on 2008-04-18
use:
```
sudo nautilus&
```
That shall give you the root permission in the file manager

---

### Post by Trail on 2008-04-18
Try **gksudo** nautlus& instead.

---

### Post by northern lights on 2008-04-18
While the above is true, I'd highly recommend running "nautilus", or any graphical app for that matter, with "gksu" rather than "sudo". Use ```
gksu nautilus
```
to tamper with system files, such as those in "/opt/"

--> [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by superjacent on 2008-04-18
Thank you all.

---

