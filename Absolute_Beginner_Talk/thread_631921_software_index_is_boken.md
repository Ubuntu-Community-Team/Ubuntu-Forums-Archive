---
title: "software index is boken"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by tommynz1975 on 2007-12-04
I have read other threads but am none the wiser....  your advice please
I am using ubuntu 6.06LTS

samba hasn't been configured yet so was thinking of deleting it but synaptic package manager will not let me, Samba shows up with a red flag in synaptic.

****
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
*****

I went to terminal and typled "sudo apt-get install -f"  and I got

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/2850kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 90935 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.3 (using .../samba_3.0.22-1ubuntu3.5_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

***
Many Many Thanks.

---

### Post by ruibernardo on 2007-12-04
Hi tommynz1975,

maybe this can help: [https://answers.launchpad.net/ubuntu/+question/1556](https://answers.launchpad.net/ubuntu/+question/1556)

---

### Post by tommynz1975 on 2007-12-05
Thanks epimeteo.. gosh I hope I spelt the name right :)
I have followed the instructions 

- got inside this folder by: $ cd /etc/rc2.d/
- and checked all the links, particularly to see the link between K09samba and samba by: $ ls -al (this is what we found K09samba -> /samba)
- then removed K09samba by: $ sudo rm K09samba
- then removed samba by: $ sudo apt-get remove -f samba
- we then did this: sudo apt-get -f install (might not do anything)
- the install samba: $sudo apt-get install samba

 sudo apt-get insall samba
password
E: Invalid operation insall


leaving these instructions.

- and created the soft link: $ sudo ln -s ../init.d/samba K09samba
Then everything worked. We followed the same procedure in rc3.d strating changing the directory.
Edit/Delete Message

I dont get what to do with /rc3.d/  but as I have removed samba? do I leave that alone

---

### Post by ruibernardo on 2007-12-05
You're welcome tommynz1975,

in their case they were having problems with rc3.d also. If it's not your case, leave it. If you want to reinstall samba later and rc3.d gives you problems, then maybe you should do the same (guessing here).

Cheers.

---

