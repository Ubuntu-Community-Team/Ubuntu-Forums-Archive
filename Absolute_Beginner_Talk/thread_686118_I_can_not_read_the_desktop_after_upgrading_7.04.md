---
title: "I can not read the desktop after upgrading 7.04"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by daniel_bel on 2008-02-02
THis is what I did to updrade from 6.6 to 7.04 

1made sure your computer is plugged into the internet
2. restart the computer - with that 7.04 Ubuntu disk NOT in any disk
 drive!
3. login via my account
4. open a terminal
5. type in this command (NO linebreak): sudo 
cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
6. type in this command: sudo gedit /etc/apt/sources.list
7. type in the password for my account when prompted
8. TOTALLY REPLACE everything that's in that file 

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
 multiverse

 
9. save that file and close it
10. back in the terminal, type: sudo apt-get update
11. then type: sudo apt-get upgrade
12. then type: sudo apt-get dist-upgrade
13. restart the computer

The result 
- no access to internet
- old system 6.06
- no letters on desktop - but boxes

I am very very grateful for any advice 
Bless you

---

### Post by macogw on 2008-02-02
No access to internet?  er....that means my suggestion of using the update manager instead of dist-upgrade (because dist-upgrading manually from Dapper was broken) isn't gonna work...  

Wait you tried to go from 6.06 to 7.10?  Without 6.10 or 7.04 in between?  That can only (safely) be done through a clean install.  Skipping versions on upgrades isn't supported, probably since as dummy packages go in to mark replacements (like gaim -> pidgin) they disappear after one round.

If possible, can you boot the old 6.06 kernel (just arrow down in GRUB)?  If you have internet access from there, do an upgrade to Edgy, then to Feisty, then to Gutsy.

---

### Post by daniel_bel on 2008-02-03
Macogw,

Thank you for your kindness
If you have time I will be grateful for a bit more details. I am completely new to UBUNTU.

Do you suggest the best option being is to download the new version from INternet - what where it takes.

Secondly, I do not understand about the arrow and GRUB.

ONly if you do have time

Thank you again good man

---

