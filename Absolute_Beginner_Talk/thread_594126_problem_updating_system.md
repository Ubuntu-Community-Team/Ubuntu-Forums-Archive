---
title: "problem updating system"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jonpon on 2007-10-27
hello ubuntuers
for some reason I keep geting this message when I try to update my system.
[B]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/B]

I have no other problem accessing the internet. and up until a week ago I had no problem updating. 
Does anyone have any ideas what might be the problem here?

---

### Post by zvacet on 2007-10-27
Chek your source list and try other server in software sources.

---

### Post by jonpon on 2007-10-27
which ever I choose its the same:

[B]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...tu0.2_i386.deb](http://archive.ubuntu.com/ubuntu/poo...tu0.2_i386.deb)
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/B]

 the repository list fails too
I get this when I reload


[SIZE="1"][SIZE="1"]http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg: Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/multiverse/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/restricted/i18n/Translation-en_US.bz2:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)[/SIZE]
[/SIZE]

---

### Post by kenny1948 on 2007-11-05
I am having exactly the same problem it started about two weeks ago!

I have posted this on other threads, but no one has replied. It's getting very frustrating. I am almost ready to switch back to a Windows operating system. This is the shits!

---

### Post by Maestro23 on 2007-11-05
> **kenny1948 said:**
> I am having exactly the same problem it started about two weeks ago!

I have posted this on other threads, but no one has replied. It's getting very frustrating. I am almost ready to switch back to a Windows operating system. This is the shits!

Please direct me to one of your threads.

---

### Post by kenny1948 on 2007-11-07
OK, I'm still fairly new to this. Please bear with me.  I have been using Ubuntu since the beginning of June.  So far the experience has been great.  

Just within the past few weeks, have I been experiencing problems.  Normally I check the forums for advice and fix the problems myself.  However lately, I haven't been able to find the answers to my problems anywhere. Hence the frustration.

I was able to find my other messages, by checking on my user name. You can do the same to find them.  Believe it or not, I just now figured that out.  I had been paging and paging through the forums trying to find my old posts. DUH! ;-{

You are one of the first though, that has replied directly to one of my posts lately.

Here is my problem:
I recently moved.  I have a cable connection.  I use Road Runner.

Lately I have been unable to get mail in Evolution.  It starts to download, then times out and shuts down.  When the messages do appear, they have a headline but no body. I sometimes get an error message stating that it cannot download mail, try later. OH and when the messages do finally turn up its two or three days later.

When I try a ping- it says everything is ok.

Likewise when I try to get any updates I get an error message:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.4-2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.4-2ubuntu2.1_i386.deb)
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused)

I have read some suggestions but did not understand.  I am not a computer geek. --please don't take that the wrong way.  I simply mean that I am not really into computer programming etc. I simply don't have the savvy nor the time to devote to it.  I try but my abilities are limited.

---

### Post by zvacet on 2007-11-07
It is probably error in sources.list because 
**[http://archive.ubuntu.com/ubuntu/dists/feisty/Rel](http://archive.ubuntu.com/ubuntu/dists/feisty/Rel) ase.gpg** is no valid address.It should be **[http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)**

```
gksudo gedit /etc/apt/sources.list
```

correct it and save.

```
sudo aptitude update
```

---

