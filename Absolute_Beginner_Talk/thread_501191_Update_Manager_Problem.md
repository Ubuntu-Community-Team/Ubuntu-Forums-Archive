---
title: "Update Manager Problem"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-07-14
When I try and install updates in the update manager it always come up with
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
So I typed in
> dpkg --configure -a
in the terminal and then it came up with
> dpkg: requested operation requires superuser privilege

coud someone please help me fix this problem? and what is a superuser?

---

### Post by ramjet_1953 on 2007-07-14
Copy and paste this into a terminal:

[COLOR="Red"]sudo dpkg --configure -a[/COLOR]

Just enter your password, when prompted.

Regards,
Roger :cool:

---

### Post by Immolatus on 2007-07-14
superuser is "sudo" in Ubuntu.
so you type in the terminal:

sudo --configure -a

it will ask for you're password. Give it you're login password.
BTW you should Google "superuser" as well as "sudo" and read a bit about the differences.
What this all means is to login as "root" with "root privileges".

---

### Post by Vuto on 2007-07-15
I did what you said to do and typed in "sudo --configure -a" and it came up with 
> sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
and then I went back to the update manager and tried to install but it came up with the same error again
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ramjet_1953 on 2007-07-15
The command is:

sudo dpkg --configure -a


Regards,
Roger :cool:

---

### Post by Vuto on 2007-07-15
ok i fixed that problem but now a new error is coming up *sigh*

it says
> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)


what does that mean? and how do I fix it?

---

### Post by isaacj87 on 2007-07-15
do this:

in terminal

sudo gedit /etc/apt/sources.list

check to see if you got double of the same source.

---

