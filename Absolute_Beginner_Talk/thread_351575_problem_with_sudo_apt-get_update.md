---
title: "problem with sudo apt-get update"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by pluskwa on 2007-02-02
Hi, when i try to update i get a folowing problem
Get:10 [http://www.kadu.net](http://www.kadu.net) ./ Packages [3368B]
99% [Working]                                                       29.6kB/s 0s
gzip: stdin: not in gzip format
Err [http://www.kadu.net](http://www.kadu.net) ./ Packages
  Sub-process gzip returned an error code (1)
Get:11 [http://www.kadu.net](http://www.kadu.net) ./ Packages [3368B]
99% [11 Packages gzip 0]                                             1900B/s 0s
gzip: stdin: not in gzip format
Err [http://www.kadu.net](http://www.kadu.net) ./ Packages
  Sub-process gzip returned an error code (1)
Fetched 5641B in 13s (418B/s)
Failed to fetch [http://www.kadu.net/download/binary/ubuntu/0.5.0-svn/edgy/./Packages.gz](http://www.kadu.net/download/binary/ubuntu/0.5.0-svn/edgy/./Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://www.kadu.net/download/binary/ubuntu/0.5.0-svn/edgy/./Packages.gz](http://www.kadu.net/download/binary/ubuntu/0.5.0-svn/edgy/./Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://deb.svx.pl](http://deb.svx.pl) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C12ADDB16FB65A0F
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

How can i fix it

---

### Post by jd65pl on 2007-02-02
Looks like you are using non-standard repos, are you sure you should be? 

>  W: GPG error: [http://deb.svx.pl]("http://deb.svx.pl/") edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C12ADDB16FB65A0F

The line above means you need a public key to use the repo

---

### Post by pluskwa on 2007-02-02
how i get the public key,
i know the prog i try to download and i used to use it before with ubuntu

---

### Post by jd65pl on 2007-02-02
You get the public key by asking the repository owner for it

---

### Post by pluskwa on 2007-02-02
how should i do this...?

---

### Post by psyne on 2007-02-02
This should work for you 

Download the key

```
wget http://poczta.prezu.one.pl/miastoplusa_sms/gpg.txt

```

We add it to APT trust keys database: 

```
sudo apt-key add gpg.txt
```

Clean up our mess

```
rm gpg.txt
```

Pulled from kadu.net [http://www.kadu.net/w/English:Download:Ubuntu](http://www.kadu.net/w/English:Download:Ubuntu)

---

### Post by pluskwa on 2007-02-02
still the same when i try
sudo apt-get update

---

### Post by psyne on 2007-02-02
have you followed all the instructions on the Kadu.net page I may have missed a step.

---

### Post by pluskwa on 2007-02-02
yes i tried it and it worked some time before
but lately  it doesn't
...

---

### Post by pluskwa on 2007-02-02
I have those kadu lines in the source.list in /etc/apt
maybe I shoud del them from there??

---

### Post by psyne on 2007-02-02
Could be they updated the key for the new year. I would suggest posting on their forum.

If you don't speak polish they have a english forum at the bottom of the page

[http://www.kadu.net/forum/](http://www.kadu.net/forum/)

I would make sure the lines are correct like they are in the kadu.net faq.

---

### Post by pluskwa on 2007-02-02
ok, thanks ill try there

---

