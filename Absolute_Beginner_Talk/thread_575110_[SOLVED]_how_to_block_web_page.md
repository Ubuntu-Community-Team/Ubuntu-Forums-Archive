---
title: "[SOLVED] how to block web page ?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-10-13
How do we block web page on ubuntu.. am using Firefox..

---

### Post by aysiu on 2007-10-13
Add it to your /etc/hosts file and it'll be blocked for every web browser (not just Firefox): ```
sudo nano -B /etc/hosts
``` Add the line ```
0.0.0.0 www.siteyouwanttoblock.com
``` Save (Control-X, Y, Enter). Refresh the page. Otherwise, you can install the NoScript Firefox extension.

---

### Post by dhani99 on 2007-10-13
Thanks a lot..

---

