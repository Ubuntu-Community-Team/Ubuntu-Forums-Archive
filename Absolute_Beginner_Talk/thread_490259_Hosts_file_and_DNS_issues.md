---
title: "Hosts file and DNS issues"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ipreferpi on 2007-07-02
So there is a website i enjoy to visit, but they are having DNS issues. The workaround is to modify my hosts file, so programs can go straight to the correct ip, and this works when I boot vista. However, when i edited the /etc/hosts file in ubuntu, nothing changed. The website still doesn't work. Any ideas? thanks

---

### Post by Cypher on 2007-07-02
After you modified your /etc/hosts file, could you ping that website from the terminal? If not, then perhaps you didn't enter the right information..

---

### Post by ipreferpi on 2007-07-02
Pinging the ip works, but the website name doesnt. thats odd. The syntax for the hosts file is:
IP  website.com                        
correct? I didn't think it was that complicated. Maybe its cached somewhere? Is my system even paying attention to the hosts file?

---

### Post by ipreferpi on 2007-07-02
I tried playing around with 127.0.0.1 and google.com to see if that changed anything, but it seems like nothing is paying attention to the hosts file.

edit: I did this and it worked:
sudo su
password
echo 'ip website.com' >> /etc/hosts

---

