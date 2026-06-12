---
title: "Mldonkey"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2006-06-11
Hello there! I've been trying to setup mldonkey on my old machine for the last 4 hours. And I've never seen a such crappy documented software in my life.

I've looked everywhere for docs, the main site, should simply do no exists.

The big problem is that I can't find a place where explains how things works. for example: how can I enable other machines on my network to connect on the web ui?
Where do I add servers to the list? Why can't my machine using mlgui can't connect to the server. and the most important of them all...

WHY IN THE WORLD THE /etc/init.d/mldonkey-server DOES NOT WORKS WHEN  ./mlnet DOES???

I'm sorry for this, but I'm really considering the idea of erasing my linux machine and putting a win xp home with an torrent/emule software.

Does anyone has ever configured this crap before?

Best regards

---

### Post by blackjack6.21.91 on 2006-06-11
Woah.  Dude, I don't know much about Mldonkey, but it's no reason to quit linux.  Limewire and Frostwire are all very easy p2p programs to install.  No hassle.  Just install the debian and depackage.

---

### Post by viniciuscarvalho on 2006-06-11
Thanks dude. But I'm not quiting linux on my machine (my laptop) just on the old server (duron 800 256mb ram). It has a ubuntu 6.06 server install. and no X server configured (actually it does have an XFCE). Frostwire seems to be very very cool, but it needs a X server right? The only good point about the mldobnkey is that I can have a core server running.
Do you have any ideas for that?

---

### Post by hugmenot on 2006-06-12
See the extensive docs on mldonkey.net. There&#8217;s plenty of information.

---

### Post by sailor2001 on 2006-06-12
try amule in repositories

---

### Post by u.b.u.n.t.u on 2006-06-12
viniciuscarvalho I use aMule and it works well enough. Very rough around the edges but it gets the job done.

If you have some specific questions about aMule then I will assist where I can. It is late here so it may be several hours, like tomorrow morning, before you will see a reply, but ask anyway and I will check in.

---

### Post by sobe on 2006-06-15
I had the same problem and what i did to fix it was to open /var/lib/dpkg/status. 

```
gedit /var/lib/dpkg/status
```

then i searched  for "mldonkey-server". 
once you find it the line right below that should say something like:
```
installed ok half-configured
```

now what you want to do is change that line to:

```
purged ok not-installed
```

save your file and then open your browser to:
[http://packages.debian.org/unstable/net/mldonkey-server](http://packages.debian.org/unstable/net/mldonkey-server)

This is the latest unstable deb package from debian. down the page you can select to download for your architecture and then save the file somewhere easy to get to (ie. your desktop). 

next open up a terminal window: Applications -> Accessories -> Terminal

execute the command: ```
cd ~/Desktop
```

then to install the package execute this command:
```
dpkg -i mldonkey-server_2.7.3-2_i386.deb
```

once dpkg is done installing your application you can quit the terminal.you now have mldonkey installed. 

and vowala it all works now. 

its not the best fix but then again i've been on linux hiatus for over 3 years now so atleast its something.

---

### Post by airtonix on 2007-11-10
he means whre the fek is the documentation on where all the files are...

the whole site does not have anything that tells us this

---

