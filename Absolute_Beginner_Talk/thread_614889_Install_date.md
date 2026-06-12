---
title: "Install date?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-11-16
Does Ubuntu store the date it was first installed, if so how can I access it? I'm just wondering because I am coming up to my first anniversary on Linux but I can't remember exactly when that was.
TIA

Mick

---

### Post by Inxsible on 2007-11-16
> **MickS said:**
> Does Ubuntu store the date it was first installed, if so how can I access it? I'm just wondering because I am coming up to my first anniversary on Linux but I can't remember exactly when that was.
TIA

MickI don't have an answer to your question, but congratulations on your anniversary ;):popcorn::guitar:

---

### Post by OffAxis on 2007-11-16
I don't know specifically but
```
ls -lt /
```
On the bottom of the list will be the earliest folder.

---

### Post by Inxsible on 2007-11-16
> **OffAxis said:**
> I don't know specifically but
```
ls -lt /
```On the bottom of the list will be the earliest folder.provided he has at least 1 un-modified folder after the install (very less chance that he doesnt tho ) 

You will probably find at least 1 which wasn't modified in the entire system.

---

### Post by overdrank on 2007-11-16
> **Inxsible said:**
> provided he has at least 1 un-modified folder after the install (very less chance that he doesnt tho ) 

You will probably find at least 1 which wasn't modified in the entire system.

The oldest I have is 2007-04-12

---

### Post by Inxsible on 2007-11-16
> **overdrank said:**
> The oldest I have is 2007-04-12and you are using Ubuntu since before then?

Also, if and when up upgraded/installed a new version it would have the new modified date as opposed to the previous install date.

---

### Post by overdrank on 2007-11-16
> **Inxsible said:**
> and you are using Ubuntu since before then?

Also, if and when up upgraded/installed a new version it would have the new modified date as opposed to the previous install date.

Yea and this drive came form another system because I have just had this system going for a couple of months.

---

### Post by OffAxis on 2007-11-16
> provided he has at least 1 un-modified folder after the install  
(within this folder)
true, but there should a few there that haven't had any action since the initial install. I've got /mnt, /opt, and /srv that haven't been time-stamped since install.

> You will probably find at least 1 which wasn't modified in the entire system.
Not true. You gotta dig a little, but they're there. For instance, there's a lot of them in 
**/usr/share/doc**
that are neither modified by system processes nor by the user.
```
ls -lt /usr/share/doc
```

There are also files that persist unchanged from initial install. I think 
/usr/bin/sudo is one of 'em.

What may be easier is the release schedule [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases") which will just ballpark it for ya.

---

### Post by Inxsible on 2007-11-16
> **OffAxis said:**
> (within this folder)
true, but there should a few there that haven't had any action since the initial install. I've got /mnt, /opt, and /srv that haven't been time-stamped since install.


Not true. You gotta dig a little, but they're there. For instance, there's a lot of them in 
**/usr/share/doc**
that are neither modified by system processes nor by the user.
```
ls -lt /usr/share/doc
```There are also files that persist unchanged from initial install. I think 
/usr/bin/sudo is one of 'em.

What may be easier is the release schedule [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) which will just ballpark it for ya.If you notice the original command was searching through the root (/) The directories that you mention will fall under that search. That's why I said you would find at least 1 in there :)

---

### Post by OffAxis on 2007-11-16
ahh.
it was the 'entire system' part that I read too much into.
No worries  :)

---

### Post by MickS on 2007-11-16
Thanks guys, I did  ls -lt / and it gave me (this is just the bit at the end)
lrwxrwxrwx   1 root root    11 2007-01-12 19:34 cdrom -> media/cdrom
drwxr-xr-x   2 root root 49152 2007-01-12 19:33 lost+found
drwxr-xr-x   2 root root  4096 2006-08-06 00:19 initrd
drwxr-xr-x   2 root root  4096 2006-08-06 00:19 srv
drwxr-xr-x   2 root root  4096 2006-05-22 15:00 mnt


Then I did  ls -lt /usr/share/doc And that gave me
org-core
lrwxrwxrwx  1 root root   19 2007-01-12 19:35 openoffice.org-writer -> openoffic
e.org-core
lrwxrwxrwx  1 root root    4 2007-01-12 19:35 perl-base -> perl
lrwxrwxrwx  1 root root    4 2007-01-12 19:35 perl-modules -> perl
lrwxrwxrwx  1 root root   17 2007-01-12 19:35 python-minimal -> python2.4-minima

So from that I reckon it was 12th January this year which would be about right so that gives me 8 weeks until I've been  with Ubuntu for one year, thanks again.

Mick

---

### Post by Inxsible on 2007-11-16
> **MickS said:**
> Thanks guys, I did  ls -lt / and it gave me (this is just the bit at the end)
lrwxrwxrwx   1 root root    11 2007-01-12 19:34 cdrom -> media/cdrom
drwxr-xr-x   2 root root 49152 2007-01-12 19:33 lost+found
drwxr-xr-x   2 root root  4096 2006-08-06 00:19 initrd
drwxr-xr-x   2 root root  4096 2006-08-06 00:19 srv
drwxr-xr-x   2 root root  4096 2006-05-22 15:00 mnt


Then I did  ls -lt /usr/share/doc And that gave me
org-core
lrwxrwxrwx  1 root root   19 2007-01-12 19:35 openoffice.org-writer -> openoffic
e.org-core
lrwxrwxrwx  1 root root    4 2007-01-12 19:35 perl-base -> perl
lrwxrwxrwx  1 root root    4 2007-01-12 19:35 perl-modules -> perl
lrwxrwxrwx  1 root root   17 2007-01-12 19:35 python-minimal -> python2.4-minima

So from that I reckon it was 12th January this year which would be about right so that gives me 8 weeks until I've been  with Ubuntu for one year, thanks again.

MickThe earliest date you have there is 22nd May 2006. Are you sure it was January 2007 when you first installed ?

---

### Post by mali2297 on 2007-11-16
> **Inxsible said:**
> The earliest date you have there is 22nd May 2006. Are you sure it was January 2007 when you first installed ?

There are certainly system files older than the install date, so *ls -lt /* won't be reliable.

I found this suggestion elsewhere:
```

ls -a --sort=t /dev -l | tail -n1

```
It gave at least a plausible date for my most recent install.

---

### Post by MickS on 2007-11-16
That puzzled me because I know I only installed it this year and the 12th January would be about right, no idea what those other listings are.

Mick

---

### Post by OffAxis on 2007-11-16
> found this suggestion elsewhere:
Code:

ls -a --sort=t /dev -l | tail -n1

It gave at least a plausible date for my most recent install.

Do you mean latest upgrade? Mine's from about 2 weeks ago, which is about right.

---

### Post by mali2297 on 2007-11-16
> **OffAxis said:**
> Do you mean latest upgrade? Mine's from about 2 weeks ago, which is about right.


Well, I haven't done any upgrades after I made a fresh install.
For me, the date of sudo is 2006-10-09, about a year before my installation.

---

### Post by OffAxis on 2007-11-16
you are quick at the keyboard mali ;)
(I edited that previous post when it dawned on me that the date on that file was utterly meaningless).

---

