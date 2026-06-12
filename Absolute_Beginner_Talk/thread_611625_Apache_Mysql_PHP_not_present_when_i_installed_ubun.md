---
title: "Apache Mysql PHP not present when i installed ubuntu 7.1 desktop"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by jaschahal on 2007-11-13
hi guys,

i did everything but couldn't find apache2, php, mysql on my fresh install of ubuntu desktop 7.1.

when i try to execute 
sudo apt-get install apache2

it will throw an error saying "Couldn;t find package apache2

what should i do. i am moving away from windows but all of this is just hurting me


thanks in advance
jas

---

### Post by Scorpuk on 2007-11-13
Have you tried using synaptic package manager and installing those from there?

System -> Administration -> Synaptic Package manager

---

### Post by eldepeche on 2007-11-13
Apache, MySQL and PHP are installed by default in the Server version, but not in the Desktop version. The GUI is installed by default in the Desktop version, but not the Server version. If you want both, you have to either:
1. Install the Server version, then install ubuntu-desktop
2. Install the Desktop version, then install the LAMP metapackage (don't remember the name)

Since you've got a desktop install and don't seem to want a CLI-only system, I'll assume you want to keep your Desktop install and add the LAMP package. If APT can't find the package, then the first suggestion I have is to make sure the repositories are enabled. Go to System -> Administration -> Software Sources and make sure the main and universe repositories are enabled.

If that doesn't work, come on back and ask again.

---

### Post by jaybombalous on 2007-11-13
```
tasksel
```

u type that at a command line and then make sure the ubuntu-desktop and the LAMP server is selected then make the changes. Be careful, I deleted my desktop using tasksel before. When I rebooted I had to re-install the desktop from the command line. If u are not sure or comfortable breaking your system then don't use tasksel.


edit: Read here, [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by jaybombalous on 2007-11-13
> **Scorpuk said:**
> Have you tried using synaptic package manager and installing those from there?

System -> Administration -> Synaptic Package manager

I would do as this man says first. I did a search of the apt-cache and it comes back as apache2 here as well. The command u issued should work, unless u don't have the right repository selected.

---

### Post by jaschahal on 2007-11-13
thank you thanyou you guys are champions

it all worked.

if i face any other problem i will get back to you


with all due respect thank you **eldepeche**

jas

---

### Post by eldepeche on 2007-11-13
No problem. Could you mark the thread as solved?

---

