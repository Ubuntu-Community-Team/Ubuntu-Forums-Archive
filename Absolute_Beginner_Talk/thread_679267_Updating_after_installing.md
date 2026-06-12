---
title: "Updating after installing"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mdb17 on 2008-01-26
i just went out and bought a real cheap pc to have around just so i could try out Ubuntu for a friend that is looking into getting a dell with it on it but every time i try to install the updates i get this message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So i opened the terminal and tried to run the program. i am not exactly sure if i did it right but this is what i put in and this is what it gave me back:

```
matthew@matthew-desktop:~$ 'dpkg --configure -a'
bash: dpkg --configure -a: command not found

```

Do you have any ideas on what to do to get the updates to install.

---

### Post by taurus on 2008-01-26
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Use the same password that you log in with and you won't see anything on the screen when you type it so don't panic.

---

### Post by NapsterX on 2008-01-26
have you tried 
sudo apt-get update
?

---

### Post by mdb17 on 2008-01-26
alright i entered that and it is saying:
```
Setting up capplets-data (1:2.20.1-0ubuntu1) ...

```

how long should i expect it to say that? cause that is the same spot it hung up last time.

---

### Post by mdb17 on 2008-01-26
> **NapsterX said:**
> have you tried 
sudo apt-get update
?



i just tried that and this is what i got
```
matthew@matthew-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
matthew@matthew-desktop:~$ 

```

---

### Post by taurus on 2008-01-26
> **mdb17 said:**
> alright i entered that and it is saying:
```
Setting up capplets-data (1:2.20.1-0ubuntu1) ...

```

how long should i expect it to say that? cause that is the same spot it hung up last time.

How long did you wait for it the last time?  Just let it run for a while and see what happens.

---

### Post by mdb17 on 2008-01-26
okay thank you i will see what it does

---

