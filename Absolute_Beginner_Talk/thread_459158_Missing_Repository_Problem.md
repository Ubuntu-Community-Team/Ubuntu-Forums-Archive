---
title: "Missing Repository Problem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2007-05-30
Help,

I am trying to install a new program and am getting the following message in Synaptic.

E: Type ‘[http://givre.cabspace.com/ubuntu/’](http://givre.cabspace.com/ubuntu/’) is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: Type ‘[http://givre.cabspace.com/ubuntu/’](http://givre.cabspace.com/ubuntu/’) is not known on line 33 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Can someone please tell me how I go about solving the problem please.

Thank you.

---

### Post by moredhel on 2007-05-30
please post your sources.list

(in terminal:)

gedit /etc/apt/sources.list

and paste everything into here.

---

### Post by Inxsible on 2007-05-30
When you added the repository, did you put the word 'deb' (without the quotes) in front of it ?

---

### Post by cydec on 2007-05-30
> **pilgrim-online said:**
> Help,

I am trying to install a new program and am getting the following message in Synaptic.

E: Type ‘[http://givre.cabspace.com/ubuntu/’](http://givre.cabspace.com/ubuntu/’) is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: Type ‘[http://givre.cabspace.com/ubuntu/’](http://givre.cabspace.com/ubuntu/’) is not known on line 33 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Can someone please tell me how I go about solving the problem please.

Thank you.

```
have you tried the folliwing code in the terminal:
wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -
```

---

### Post by pilgrim-online on 2007-05-31
Hi,

Thank you all for your replies.

To explain a little more about the origin of the problem-
I opened Synaptic and clicked 'reload' this took a long time and finally produced a message saying that the repository which is now missing was no longer available as it could not be accessed.
_After that_ I somehow managed to remove the repository?

I will post my sources list and try the suggested code within the next couple of hours. [I need to use Windows at the moment.]

---

### Post by pilgrim-online on 2007-05-31
Sources list:-

deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
[http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/)

[http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/)
[http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/)
[http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) 

[http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) 
[http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) 

When I tried putting 'deb' in front of a line I was informed that the file is 'read only'.

When I entered 'wget [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc) -O- | sudo apt-key add' into a terminal I got the following:-

                   :~$ wget [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc) -O- |  sudo apt-key add
--15:18:37--  [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc)
           => `-'
Resolving givre.cabspace.com... gpg: can't open `': No such file or directory
65.175.85.100
Connecting to givre.cabspace.com|65.175.85.100|:80... failed: Connection timed out.
Retrying.

--15:23:47--  [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc)
  (try: 2) => `-'
Connecting to givre.cabspace.com|65.175.85.100|:80... failed: Connection timed out.
Retrying.

--15:28:58--  [http://givre.cabspace.com/ubuntu/givre_key.asc](http://givre.cabspace.com/ubuntu/givre_key.asc)
  (try: 3) => `-'
Connecting to givre.cabspace.com|65.175.85.100|:80...

This seems similar to what happened when I tried to reload Synaptic.

---

### Post by pilgrim-online on 2007-06-02
Synaptic now appears to be empty of files and refuses to reload, showing the same error message that I got originally.
Any ideas would be gratefully received.

---

