---
title: "after unpacking tarball what's next?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Matthyis on 2007-06-28
hi I got a question after unpacking a tarball I read the INSTALL file and sometimes the directions don't work after I follow the directions steps I unpack the tarball in the directory I have it in gunzip -c <tgz_file> | tar -xvf -
but what do I need to look for or type after this I'm confused because I read the direction's and sometimes they don't work with Debian package mangers some direction's say this.
if anyone can help me out I would appreciated thanks

---

### Post by starcraft.man on 2007-06-28
> **Matthyis said:**
> hi I got a question after unpacking a tarball I read the INSTALL file and sometimes the directions don't work after I follow the directions steps I unpack the tarball in the directory I have it in gunzip -c <tgz_file> | tar -xvf -
but what do I need to look for or type after this I'm confused because I read the direction's and sometimes they don't work with Debian package mangers some direction's say this.
if anyone can help me out I would appreciated thanks

[Installing from source.]("http://www.psychocats.net/ubuntu/installingsoftware#source")

I don't recommend compiling unless you absolutely have to (i.e. rare app not in any other source), most programs can be readily found in the repos or in prepackaged debians on the net.

If its more complicated then that, please past the directions here and we can help more specifically.

---

### Post by Rocket2DMn on 2007-06-28
Agreed, you should get it with apt-get or Synaptic if possible.  Often when you download from source it goes something like this:
```
tar -xzvf filename.tar.gz
./configure
make
make install
```
Different programs have different setup processes which should be explained in the INSTALL or README file that comes with the tarball.

---

### Post by Matthyis on 2007-06-28
yea I just did that with synaptic I just was looking at irssi for irc client and I seen it in synaptic
I should have known to check their and I was browsing around and stuff. I did the update from source will this hurt my system the commands worked thanks a lot some updates come in a tar ball for some program's so I wanted to learn how to install the tar balls and it was kinda of fun
should I remove build-essential or something?

---

### Post by Rocket2DMn on 2007-06-28
You should be able to remove the files that were extracted from the tarball and the tar file itself.  I wouldn't fiddle with anything it installed, its probably now tied to what you got from apt-get.

---

