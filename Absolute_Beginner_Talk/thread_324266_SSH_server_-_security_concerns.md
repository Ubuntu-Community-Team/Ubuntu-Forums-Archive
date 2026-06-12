---
title: "SSH server - security concerns"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by flabbas on 2006-12-23
I have an SSH server (open-ssh) running on my webserver (Ubuntu 6.06 LAMP) so that I can administrate it remotely, however recently brute force attacks are becoming more and more frequent.

The passwords are strong enough that an ordinary dictionary attack will get nowhere and neither will a brute force attack.

I wondered if there was a way to limit the number of failed login attempts **per unique host**.  I.e. 5 failed attempts from a specific host will result in that host being blocked (either permenantly or for a specific amount of time).  It is not of the upmost importance, I would just like to avoid tempting fate, and prevent spurious requests from hogging my server resources.  Unfortunately I cannot restrict the allowed hosts, as I often ssh in from many different locations.

Any help appreciated, 

Cheers

---

### Post by Jussi Kukkonen on 2006-12-23
Well, the best way to avoid "tempting fate" is to only allow key-based logins... But if that is not possible (as seems to be the case), the tool you are looking for is denyhosts. Available in the repositories.

---

### Post by dienush on 2006-12-23
i use fail2ban and it works like a charm to block brute force attacks

from fail2ban.log :  

2006-12-22 05:20:16,254 INFO: VSFTPD: 201.216.236.100 has 5 login failure(s). Banned.
2006-12-22 05:20:16,280 WARNING: VSFTPD: Ban (600 s) 201.216.236.100
2006-12-22 05:30:16,420 WARNING: VSFTPD: Unban 201.216.236.100
2006-12-22 17:44:30,173 INFO: SSH: 220.194.56.44 has 5 login failure(s). Banned.
2006-12-22 17:44:30,198 WARNING: SSH: Ban (600 s) 220.194.56.44
2006-12-22 17:54:30,353 WARNING: SSH: Unban 220.194.56.44
2006-12-23 05:06:51,791 INFO: SSH: 125.248.86.5 has 5 login failure(s). Banned.
2006-12-23 05:06:51,816 WARNING: SSH: Ban (600 s) 125.248.86.5
2006-12-23 05:16:51,992 WARNING: SSH: Unban 125.248.86.5

---

### Post by steve.horsley on 2006-12-23
If you want to restrict logins to certain IP addresses, you can do this:
to /etc/hosts.deny, add the line
> ALL: ALL
and to the file /etc/hosts/allow, add the line:
> sshd : 1.2.3.4
but use the IP address you will be calling from. You can allow several addresses separated by commas.

---

### Post by flabbas on 2006-12-24
Thanks for the replies - after looking at the wiki for fail2ban, it seems to be exactly what I am after.

Thanks again

---

### Post by Crakie on 2006-12-24
> **Jussi Kukkonen said:**
> Well, the best way to avoid "tempting fate" is to only allow key-based logins... But if that is not possible (as seems to be the case)

It is possible. I carry around my key on a thumbdrive, along with a copy of Putty :)

---

