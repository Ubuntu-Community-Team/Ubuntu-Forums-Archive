---
title: "cannot sudo on new installation"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by fpcheck on 2008-01-05
I just installed server 7.1 and when I try to run "sudo apt-get update" i get response that i am not in sudoers file so I cant perform any action.
When I try to edit the sudoers file I get permission denied 
ex - visudo /etc/sudoers
help :confused:

---

### Post by reckless2k2 on 2008-01-05
do you know/remember your admin user or did you setup a root password?

---

### Post by fpcheck on 2008-01-05
I did not set up a root account except - during mysql installation i set the root password ... did that effect the user accounts

---

### Post by qpieus on 2008-01-05
The correct command to edit the sudoers file is```
sudo visudo
```Do not use a regular text editor to edit this file.

But before you edit that, check to see if you are in the admin group. Any user in the admin group should be able to use sudo. Type id at a command prompt to see your groups.

---

### Post by fpcheck on 2008-01-05
I checked to see if I am in the admin group - I  am in (4) adm and a bunch others the last being 1000 fpcheck - my user name
when i type sudo visudo I get fpcheck not in sudoers file

---

### Post by Dr Small on 2008-01-05
Are you using a *second* account that you just created, besides the default account that you created when installing?

If so, you may not have given it Administrative Permissions.

If all else fails, you will need to boot into recovery mode and add your user to the admin group to use sudo.

Dr Small

---

### Post by lswest on 2008-01-05
make sure you're in the Wheel group (is usually enabled in the sudoers file by default)

---

### Post by fpcheck on 2008-01-05
I did not create any other accounts. It is the first boot after installation

---

### Post by Dr Small on 2008-01-05
> **fpcheck said:**
> I did not create any other accounts. It is the first boot after installation
Then boot into recovery mode, from GRUB, and when it brings you to the root prompt:
```
root@host:~#
```

Run this command:
```
adduser fpcheck admin
```

Then reboot:
```
reboot
```

And boot normally and see if sudo will work.

Dr Small

---

### Post by fpcheck on 2008-01-05
I went to add fpcheck to admin group - it did not exist
I added the group then user
still nothing

---

### Post by lswest on 2008-01-10
as i mentioned above, adding your user to the group "wheel" should solve your sudo problem.  Because, if i remember correctly (i'll check later and get back to you, running on windows atm), it's a default entry in the sudoers file, so that if you add a user to that group you'll gain the ability to use sudo.

I just checked, looks like my information was slightly out of date, or maybe it was Fedora with the wheel group?  in any case, if you go to system-->administration-->users & groups and choose properties for your username go to the tab "user privileges" and check the box "administer the system"  or, while in Users & Groups you can manage groups and choose the admin group, hit properties and see if your account is in there.  The Last thing you can try is in booting into the recovery mode, logging in as root and typing "visudo" and finding the entry for admin, copying that and changing admin with the name of your account, which is also a group.  not the best fix, but it should work.

---

