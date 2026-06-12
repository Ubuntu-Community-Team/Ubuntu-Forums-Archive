---
title: "smbpassword"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by stever on 2006-08-06
Hi, 
I have samba installed, setup a share, can see the share from other WinXp machines, ready to set up a samba user for the login to the share from the XP machine but when I try setup a samba user called 'steve' get the following message: 

--------------------
steve@steve-desktop:~$ sudo smbpassword -a steve
Password:
sudo: smbpassword: command not found
--------------------

Any help would be great
Thanks
Steve

---

### Post by BitTorrentBuddha on 2006-08-06
It's smbpasswd, without "o" or "r," understandable mistake, I've made it a few times as well. ;)

---

### Post by stever on 2006-08-06
How stupid do I feel, looked over all the notes I have and it clearly says smbpasswd. All sorted,

Thanks BitTorrentBuddha

Regards
Steve

---

