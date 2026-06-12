---
title: "LAMP setup on 7.10(edgy?)"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-02
are there any good tutorials on how in install apache 2, mysql 5 and php 5 on ubuntu 7.10?

---

### Post by Tatty on 2008-03-02
7.10 is Gutsy Gibbon not Edgy :popcorn:


If you download the Ubuntu Server CD then it gives you an option to install a default LAMP server when you are installing.

If you want to install a LAMP server on an existing Ubuntu install then try this [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

---

### Post by RyanZec on 2008-03-02
looks like a good docs but have a question about apache.  when i try to start/stop/restart i get this error:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

now the server does stop and start but just wondering about that error.

---

### Post by robertmf on 2008-03-08
[COLOR="DarkRed"]You need to use the forum [SEARCH]  For example, search on [START STOP APACHE] [/COLOR]

> **Etiol said:**
> I've never had any problems just leaving apache running, but if you wanted to start & stop it on demand, you could create a little script like this: ```
#!/bin/bash
#apcon.sh - simple apache control script

  if pgrep apache2
  then
    zenity --question --title="Apache Controller" --text="Apache is running. Do you want to stop it now?" && gksudo apache2ctl stop
  else
    zenity --question --title="Apache Controller" --text="Apache is not running. Do you want to start it now?" && gksudo apache2ctl start
  fi
``` and add a custom launcher for it to your panel.

---

