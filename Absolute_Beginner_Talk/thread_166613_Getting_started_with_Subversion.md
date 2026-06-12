---
title: "Getting started with Subversion"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-04-26
Hello all,
I'm trying to get Subversion set up on my new Ubuntu server. The first thing I did was create a repository called test under my home directory. I then executed:
chmod 777 test

Then, I ran svnserve -d to run it as a daemon.

Finally, I tried to connect to the server from another machine on the same network using TortoiseSVN (path to repository is 192.168.3.5/test). I tried the following path:
SVN://192.168.3.5/test
but I'm getting a message that says there is no repository there.

I then tried to telnet onto the box and hit port 3690, but it didn't work. However, I can have the server run a portscan on itself, and it shows a connection open at 3690.

Where do I go to fix this?

---

### Post by garner_nc on 2006-04-26
Linux Journal did a good article on Subversion some months ago. You can probably find the article on their website now.

All the Best,
Doug White

---

### Post by auroraborealis on 2006-04-26
From the machine that is running subversion, can you do `svn co svn://localhost/test` ?

---

### Post by gantww on 2006-04-26
Actually, I'm getting the same error. That's a start though.

---

### Post by hw-tph on 2006-04-27
I think [this](http://www.linuxjournal.com/article/8596) is the article Doug referred to. It's worth a read.


Håkan

---

### Post by kvdbreem on 2006-08-05
> I can have the server run a portscan on itself, and it shows a connection open at 3690.

If I'm not mistaken, that doesn't mean much of anything, as the server system itself is probably not going to let any old computer connect to it, no?

---

### Post by revdev on 2006-08-17
I was getting the same error, doing the same thing (Ubuntu repo with TortoiseSVN). The thing I forgot to do was import the files in to the repository. I did a ```
svn import /tmp/myproject file:///path/to/repos/myproject -m "initial import"
```
and then it worked great.

---

