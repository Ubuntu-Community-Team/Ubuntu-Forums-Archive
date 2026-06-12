---
title: "Error telling me &quot;File '/etc/resolv/conf' could not be opend for writing&quot;"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by heyilikeyoursweater on 2006-12-18
When I connect to my wireless home connection it says "File '/etc/resolv/conf' could not be opend for writing Nameserver(s) and/or domain are not set." 

What does this mean? I figured I could just go to the file properties and change it to read/write but when I go to the file properties it says the file owner is root. I am the administrator. Why can't I change it? Is this what I need to do?

---

### Post by heyilikeyoursweater on 2006-12-18
Please help. I posted one other time and was abandoned. Don't do it again. I really love Ubuntu except for few minor things.

---

### Post by tbroderick on 2006-12-18
In order to edit anything outside of your /home, you need root access. In Ubuntu, you would use sudo and/or gksu. Usually, you use sudo when running commands from a terminal/console and gksu when using an X GUI. So to edit /etc/resolv.conf, you can use sudo nano -w /etc/resolv.conf or gksu gedit /etc/resolv.conf from a terminal.

---

### Post by heyilikeyoursweater on 2006-12-18
Thanks for telling me how to edit it, but **I** don't want to edit it, I want the wireless manager to be able to edit it.

---

