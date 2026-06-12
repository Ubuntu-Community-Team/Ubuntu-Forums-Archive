---
title: "Aptitude port"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-03-16
just out of curiousity... what port or ports does aptitude use to send and recieve from repositories???

---

### Post by louis_nichols on 2007-03-16
downloads are made using http, so that would be port 80.

---

### Post by JonConstantine on 2008-02-25
Hi, I have a little problem. My PC is behind the Kerio WinRoute Firewall and I have port 80 opened. But I cant update aptitude or install something with apt-get. What is the problem? What ports do I need to use? Ubuntu 7.10 running. Thanks.

---

### Post by JonConstantine on 2008-02-25
ok, solve it by myself.
Just add this lines to your /etc/environment file...

http_proxy="http://ip address:ip port"
ftp_proxy="http://ip address:ip port"

then run this command to apply the changes:

source /etc/environment

maybe will help to someone ;)

---

