---
title: "Cannot be root?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-04
```

nic@nic-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
nic@nic-desktop:~$ 

```

Ftw?  Im trying to install Java, and I cannot get it to work past step 1, 

"# At the terminal: Type:
su
# Enter the root password.
# Change to the directory in which you want to install. Type:
cd
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java

Note about root access: To install the JRE in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
# Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-1_5_0-linux-i586-rpm.bin
# Start the installation process. Type:
./jre-1_5_0-linux-i586-rpm.bin"

---

### Post by steeleyuk on 2007-06-04
would it not be easier to use sudo?

if you really want to use su then you'll need to change its password. by default, Ubuntu generates a random password for the root account. to change it go to the System menu, Administration and then Users & Groups. highlight root then click properties. from there you can change the su password.

---

### Post by iZmu on 2007-06-04
try
sudo su

---

### Post by jonward0690 on 2007-06-04
Well if you want to be root first you need to type in sudo passwd to set your root password then go to system administartion the login window then to security and put a x by let local adm login.

---

### Post by LollYouSuckZor on 2007-06-04
> **iZmu said:**
> try
sudo su

Hahaha! Stupid me.  Thanks alot :)

---

