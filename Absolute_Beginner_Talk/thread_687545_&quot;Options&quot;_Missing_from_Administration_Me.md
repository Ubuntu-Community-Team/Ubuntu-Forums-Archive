---
title: "&quot;Options&quot; Missing from Administration Menu"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by scoalegil on 2008-02-04
I have recently installed Ubuntu on a computer at work.  The purpose of the PC is to provide a common computer for staff to scan, edit/create graphics and print with our colour printer.

Everything works great ... except one thing.  There are a number of "options" missing from the System -> Administration menu including 'Users and Groups' and 'Synaptic'

I wanted to add a printer.  I was making my way through the process when it prompted me for a password (nothing out of the ordinary) but it rejects the password.  Clearly if I can use the password to log in it is correct.

There is only one user, the one created during set up.  I have no idea what do do from here.  If anyone has any insights, please let me know.  I'd like to add the printer and install some updates.

---

### Post by taurus on 2008-02-04
Do you belong to group admin?  You need to belong to that group if you want to use sudo/gksudo.  Open a terminal and post the output of this command here.

```
id
```
Also, you didn't happen to make any changes to /etc/sudoers, did you?

---

### Post by scoalegil on 2008-02-05
here is what that gave me ...

```
uid=1001(staffer) gid=1001(staffer) groups=4(adm),20(dialout), 21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),104(scanner),119(fuse),1001(staffer)
```

---

### Post by scoalegil on 2008-02-06
I really have no idea how to get passed this ... can anyone offer a suggestion?  I mean, it's the only user account (the one created during installation, I'm pretty sure).  I have to be able to perform administrative functions.

---

### Post by seventhc on 2008-02-06
I think if you boot into recovery mode you can reset the password from there.

---

### Post by bwtranch on 2008-02-06
Well, you set up your system with a root password, correct? Otherwise you wouldn't be able to login at boot. So, in a terminal type in

sudo su

This will ask you for your password

Now, you are root (#) example:
(I will list the files in my root folder using ls)

jim@jim-desktop:~$ sudo su
[sudo] password for jim:
root@jim-desktop:/home/jim# cd /
root@jim-desktop:/# ls
backups                              etc             media  sys
bin                                  home            mnt    tmp
boot                                 initrd          opt    usr
cdrom                                initrd.img      proc   var
cupswrapperdcp1000_1.0.2-1_i386.deb  initrd.img.old  root   vmlinuz
cupswrapperDCP1000-1.0.2-1.i386.rpm  lib             sbin   vmlinuz.old
dev                                  lost+found      srv
root@jim-desktop:/# 




Now, I had to get out of root because I don't want to stay there too long. Especially when I'm online. You can change your password "passwrd" and add users "adduser" and give the user attributes (privileges) . You can only do this as root. Hope this helps.

---

### Post by seventhc on 2008-02-06
2 links to look at:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
and look at this one, go to #5, it tells about adding users to sudo.
[http://www.linux.com/feature/54945](http://www.linux.com/feature/54945)

---

### Post by seventhc on 2008-02-06
> Well, you set up your system with a root password, correct?The root password is locked by default, sudo gives you the permissions needed to perform administrative tasks.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

example: you can do *'sudo su'*, but if you try *'su'*, your password will fail.

---

