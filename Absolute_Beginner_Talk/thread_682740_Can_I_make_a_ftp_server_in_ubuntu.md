---
title: "Can I make a ftp server in ubuntu"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by karq on 2008-01-30
So can I make a ftp server in ubuntu?
I want to share some pics with my friends. In windows I used bulletproof ftp server to make a server.

---

### Post by beercz on 2008-01-30
Try installing proftpd.

I think it is available in the repositories.

---

### Post by karq on 2008-01-30
So installed proftpd and now I have this problem, when someone tries to connect to that server outside my network then it says "No connection could be made because the target machine actively refused it". I tried Gene6 FTP Server ™ - Online FTP Test and that connected succesfully into my ftp.
So where is the problem?

---

### Post by Rocket2DMn on 2008-01-30
Are they connecting to the correct ftp port?  Standard FTP uses port 21 and SSH/SFTP uses port 22.

---

### Post by rasta_freak on 2008-01-30
I think, by default, anonymous access is disabled. You should edit "/etc/proftpd.conf" or something like that, and restart proftpd.
EDIT: oh, didn't read fully previous post, sorry.

---

### Post by karq on 2008-01-30
Ok thx, got my server running now, but how can I give premissions in proftpd?My friend tried to go into a folder on my ftp and it says premissons denied.

---

### Post by Rocket2DMn on 2008-01-30
Make sure your friends know what port you are on, and know if you are running SFTP or just plain FTP b/c they will have to tell their FTP clients that.  Also, although that website seemed to work, if you have a router, make sure you have that port forwarded to your internal IP.

---

### Post by rasta_freak on 2008-01-30
About permissions, you have to make sure that all files & dirs under /home/ftp or wherever is your FTP home, are world readable (and dirs executable) IF they log in anonymously. Do the good old 'chmod' or 'find, xargs, chmod' friends :)

For example:
FILES: find /home/ftp -type f -print0 | xargs -0 chmod o+r
DIRS:  find /home/ftp -type d -print0 | xargs -0 chmod o+rx

Note1: double check that for spelling and corectness before doing it :)
Note2: it might impose security issues if you have valueble data under /home/ftp :)

EDIT: if they log in as some existing user - not anonymously, they'll use/see files under /home/<user> so no need to change anything.
EDIT2: you might need "sudo", depending on ownership of stuff there.

EDIT3: oh yes, i think you could also make stuff under /home/ftp owned by user "ftp" & group "ftp", but you have to configure/double check that in /etc/proftpd.conf and see as which user/group does proftpd daemon run as (when anonymous access is in question). I myself never did actualy get it to work like that, but i guess it was a buggy version of mine...

---

### Post by karq on 2008-01-30
So thanks everyone, got everything working :D
Linux is a killer :D That ftp didint work under win that well.:guitar:

---

### Post by rasta_freak on 2008-01-30
Just watch out what you put under /home/ftp and don't put any symlinks there which point to somewhere like '/', as anyone will be able to read it (and write/delete it if persmissions allow it) - or make some proper firewall setup.

---

### Post by Rocket2DMn on 2008-01-30
> **rasta_freak said:**
> Just watch out what you put under /home/ftp and don't put any symlinks there which point to somewhere like '/', as anyone will be able to read it (and write/delete it if persmissions allow it) - or make some proper firewall setup.

It is common with FTP to still be able to see much of the root filesystem tree, but so long as the permissions are correct on the system, they won't be able to write, just read.  There should be ways to limit users to the ftp subdirectory, you can definitely research that.

---

### Post by rasta_freak on 2008-01-30
Yeah, I think it's by default (in config file) to disallow anonymous to do "cd .." from anonymous home, but better double check that.

---

