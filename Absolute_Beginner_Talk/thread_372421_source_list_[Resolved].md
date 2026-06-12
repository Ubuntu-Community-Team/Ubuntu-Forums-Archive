---
title: "source list [Resolved]"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by stuart@gib.co.za on 2007-02-28
i get the following message E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/)

: Type '-' is not known on line 1 in source list /etc/apt/sources.list
E: Unable to lock the list directory

now i cant open package manager or do any updates.

any ideas

---

### Post by STREETURCHINE on 2007-02-28
can you post your source.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by stuart@gib.co.za on 2007-03-01
my source list is blank.

---

### Post by aysiu on 2007-03-01
> **stuart@gib.co.za said:**
> my source list is blank.
Can you post the output of these commands (in this order)? ```
cd /etc/apt
ls -al
cat /etc/apt/sources.list
sudo aptitude update
```

---

### Post by STREETURCHINE on 2007-03-01
what version are you using,edgy or dapper

---

### Post by Kateikyoushi on 2007-03-01
Then open your sources list for editing and copy paste the list of your ubuntu release in the sources.list file. [LINK]("http://www.psychocats.net/ubuntu/sources") 
After that copy this to the terminal.
```
sudo aptitude update
```

---

### Post by stuart@gib.co.za on 2007-03-01
ubuntu 6.10

---

### Post by Kateikyoushi on 2007-03-01
In that case open the list for editing.

```
gksudo gedit /etc/apt/sources.list
```

Copy paste in the following.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 

deb http://archive.ubuntu.com/ubuntu edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse 

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

deb http://archive.canonical.com/ubuntu edgy-commercial main
```

and update
```
sudo aptitude update
```

---

### Post by stuart@gib.co.za on 2007-03-01
kate really nows his stuff. i pasted the link he sent me and ran the update. everything is working.

thank you everyone for all the help.

---

