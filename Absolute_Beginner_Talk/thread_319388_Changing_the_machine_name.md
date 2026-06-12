---
title: "Changing the machine name"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
How do i go about changing the machine name of my ubuntu machine

---

### Post by sam81 on 2006-12-15
if you go from the main menu to System>Administration>Networking and click on the "General" tab, you can change the hostname of your machine.

---

### Post by keithweddell on 2006-12-15
If you do a search on hostname you'll find a number of opinions.  My opinion is that the best method is  to manually edit /etc/hosts and /etc/hostname.


Keith

---

### Post by Bachstelze on 2006-12-15
Here's how I usually do :

1. Become root : *sudo -i*

2. Change the hostname : *hostname your_very_cool_new_hostname*

3. Edit /etc/hostname and /etc/hosts accordingly


You can swap 2. and 3. if you want but be sure to become real root with sudo -i before ! The reason for this is that if the host mentioned in /etc/hosts doesn't match the current hostname, you won't be able to sudo, so you need to be real root to be able to edit the files without using sudo. Also, editing /etc/hostname makes sure the changes are kept after a reboot.

---

