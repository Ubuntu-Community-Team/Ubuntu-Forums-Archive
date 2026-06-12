---
title: "Confused about permissions chmod and chown"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by pdoukas on 2007-09-27
Hi all,

can someone point me in the correct direction? I'm a linux n00b and I'm trying to work with an application on the LAMP server. I'll post what was said in the other forum and then post what I did to get info and then we'll work from there.

What was said:  

I think you are mixing the chown with the chmod command, as all you need to do is to grant Read permission to whatever user account Apache is running as, in order for Apache to read files from the directory where PacsOne (the application) is installed.

What I did next:

root@mdigpacs:~# ps aux| grep "apache"
root      3842  0.0  1.0  18284  5568 ?        Ss   11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3876  0.0  1.7  20428  8712 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3877  0.0  1.4  19976  7360 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3878  0.0  1.5  20496  7640 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3879  0.0  1.5  19792  8112 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3880  0.0  1.5  20432  7624 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  3882  0.0  1.2  19100  6192 ?        S    11:20   0:00 /usr/sbin/apache2 -k start -DSSL
root      4032  0.0  0.0   1636   496 pts/0    R+   13:41   0:00 grep apache

The whole idea is to find out the permissions of the user running apache and the group permissions that the user has so that I can make sure that the directory that I have my application installed into has those permissions so I can run this application.

Any assistance in the right direction would be appreciated as I cannot tell what user is running apache. Is it root or www-data?

Pete

---

### Post by pdoukas on 2007-09-27
Anyone want to take a shot at this?

---

### Post by Linux_Man on 2007-09-27
Well, technically any user can run apache, from what you put down, your logged in as root so it is root thats running apache, because it says root@*name of computer/server*, thats just my guess though, im not a sysadmin though, so don't count on it being fully correct.

---

### Post by pdoukas on 2007-09-27
That gets me no where. I logged in as a normal user and get some of the same strings. Thanks for the attempt. Still fielding from experts.

---

### Post by jordanmthomas on 2007-09-27
www-data is running your apache process.  You can tell because the user who owns a process is listed at the beginning of the line (note your last line, root is running grep)

Is that what you were wanting to know?

Then, you can either chown the PacsOne directory to be owned by www-data or use chmod to ensure www-data has read permission.

---

### Post by pdoukas on 2007-09-27
Exactly what I was looking for and thank you so much!!!

Pete

---

