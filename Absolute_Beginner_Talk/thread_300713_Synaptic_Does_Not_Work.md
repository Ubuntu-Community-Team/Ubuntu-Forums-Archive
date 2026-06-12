---
title: "Synaptic Does Not Work"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Amit Yaron on 2006-11-16
Hi all.

I will appreciate your help on the following:
I installed Ubuntu recently, and when trying to start Synaptic or any other desktop application requiring a password it gives an error message on root password, and does nothing when I enter my login account's password.

Thanks,
  Amit.

---

### Post by LLRNR on 2006-11-16
If it's YOU that installed Ubuntu, and if there's only one user account, put in the password that you also use to login. If there's more than 1 account, put in the password of the first user account you created.

---

### Post by Amit Yaron on 2006-11-16
That's exactly what I do, and still get nothing.

---

### Post by taurus on 2006-11-16
Make sure you belong to both adm & admin in /etc/group.  What does it say when you run this command from a terminal?

```
id
```

---

### Post by Amit Yaron on 2006-11-16
I added a group named 'admin' which did not exist before, and added my user name. It still doesn't work.

---

### Post by LLRNR on 2006-11-16
Good idea, post in the output of "id" that Taurus suggested.

---

### Post by taurus on 2006-11-16
> **Amit Yaron said:**
> I added a group named 'admin' which did not exist before, and added my user name. It still doesn't work.
Are you using Breezy, Dapper, or Edgy?  Again, what is the output of the "id" command from a prompt.  Also, what does your /etc/group look like anyway?

```
cat /etc/group
```

---

### Post by Amit Yaron on 2006-11-16
amity@homeLinux:~$ id
uid=1000(amity) gid=1000(amity) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(amity),1001(admin)

---

### Post by taurus on 2006-11-16
Group admin should not have an ID of 1001!  It should be 114!!!

---

### Post by Amit Yaron on 2006-11-16
This is the output after deleting the group 'admin' and creating it with the id=114.

amity@homeLinux:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:amity
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:amity,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:amity,hal
floppy:x:25:amity,hal
tape:x:26:
sudo:x:27:
audio:x:29:amity
dip:x:30:amity
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:amity
sasl:x:45:
plugdev:x:46:amity,hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
amity:x:1000:
lpadmin:x:104:amity
scanner:x:105:amity
crontab:x:106:
ssh:x:107:
messagebus:x:108:
hal:x:109:
slocate:x:110:
saned:x:111:
gdm:x:112:
admin:x:114:amity

---

### Post by taurus on 2006-11-16
Reboot and see if you can run sudo from a terminal!

```
sudo aptitude update
sudo aptitude upgrade
```
p.s.  What version of Ubuntu are you running right now:  Breezy, Dapper, Edgy, or Feisty?

---

### Post by 3rdalbum on 2006-11-16
If you installed from the Alternative CD, and opted to do an "Expert" install where you set a root password:

Boot up under Recovery mode (you will be prompted for the root password you set during the install)
Open the Users and Groups control panel.
Edit your normal user account so its user privileges include "Executing System Administration tasks".

---

### Post by Amit Yaron on 2006-11-17
Hi!

1. I'm using the Breezy version.

2. Neither "sudo" nor the User and Group control panel works. All I see when starting the cp is a tab reading "Starting Users and Groups" and then it closes.
Is there any error log I can view?

Thanks,
  Amit.

---

### Post by anaconda on 2006-11-17
One lazy solution is to boot to recovery mode and type
```
passwd
```
and give your root user a password.
then you can use "sudo su" with the new root pasword.

---

### Post by Amit Yaron on 2006-11-17
It seems to me that the problem is with "sudo".
Anyway, I've found something else I can use:
% su - -p root
and having logged in:
% synaptic
or
% users-admin
or
% update-manager

etc.

Thank you all.

---

