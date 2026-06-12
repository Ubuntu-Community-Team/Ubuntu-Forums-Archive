---
title: "Become sudo in sh script"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by helino on 2007-11-04
Hi,

I want to become sudo in a shell script, but I don't know how to do it. I tried this solution, but I doesn't launch the program:

```
#!/bin/bash
foo=`gksudo -u root -k -m "Enter your password for root terminal access" /bin/echo "got r00t?"`
sudo /usr/local/games/etqw.demo/etqw.x86 &

```

Can someone help me with this? I just want a box or terminal that pops up and asks for my password

thanks

---

### Post by cmnorton on 2007-11-04
#!/bin/bash

read -s -p "Enter your password: " TEMP_PASSWD

echo $TEMP_PASSWD | sudo -S <some-command>

I could not get this to work with sudo -i.  If your shell script has to run as root, I would suggest sudo -i from the command line and using at, or editing /etc/crontab and letting your script run as root. Just have a test system standing by.

---

### Post by Perfect Storm on 2007-11-04
Why would you run ETQW with sudo?
You can install ETQW with sudo so it installs so every user account can use the game - but never run the game with "sudo" - The safest would be installing the game in your home if your are single user.

---

