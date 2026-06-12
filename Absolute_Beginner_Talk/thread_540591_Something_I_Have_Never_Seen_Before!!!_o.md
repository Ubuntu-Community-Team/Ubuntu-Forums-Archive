---
title: "Something I Have Never Seen Before!!! :o"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Church.Cameron on 2007-09-01
Ok,

so i am trying to update and for some reason i am getting this error so i do a  sudo dpkg --configure -a, and get i this message take a look at the last line here


cameron@ubuntu:~$ sudo apt-get updateGet:1 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 4B in 0s (6B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 newline in field name `ation.'


what do i do please help me..:(

---

### Post by Church.Cameron on 2007-09-01
Ok,

so i am trying to update and for some reason i am getting this error so i do a sudo dpkg --configure -a, and get i this message take a look at the last line here


cameron@ubuntu:~$ sudo apt-get updateGet:1 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 4B in 0s (6B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
cameron@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
newline in field name `ation.'


what do i do please help me..

---

### Post by iamhugeinjapan on 2007-09-01
Edit: sorry didn't notice that last sudo.  I don't know the answer.

---

### Post by Majorix on 2007-09-01
Move /var/lib/dpkg/updates/0000 to your home folder. Delete it from the original folder and try again. If that doesn't work please move the file back in the correct place again and post its contents here.

---

### Post by Dr Small on 2007-09-01
> **Majorix said:**
> Move /var/lib/dpkg/updates/0000 to your home folder. Delete it from the original folder and try again. If that doesn't work please move the file back in the correct place again and post its contents here.
```
sudo mv /var/lib/dpkg/updates/0000 /home/USERNAME
```

---

### Post by Church.Cameron on 2007-09-01
> **Dr Small said:**
> ```
sudo mv /var/lib/dpkg/updates/0000 /home/USERNAME
```

am i suppose to use this code because when i do i get this 


cameron@ubuntu:~$ sudo mv /var/lib/dpkg/updates/0000 /home/cameron
mv: cannot stat `/var/lib/dpkg/updates/0000': No such file or directory


i just want to update gosh :\:mad:

---

### Post by Majorix on 2007-09-01
How can it not exist, because its the file that gives the error holding you back from updating. Can you go into that folder in Nautilus and check whats inside? Also for us to see you can paste the results of this:
```
ls -a /var/lib/dpkg/updates
```

---

### Post by aJayRoo on 2007-09-01
Well, I'm not sure but I think that file is a temporary file left around by an interrupted install/update. I can do no better than point you [here](http://ubuntuforums.org/showthread.php?t=385886) where some one else has had and solved a similar issue. I hope that helps you out!

---

