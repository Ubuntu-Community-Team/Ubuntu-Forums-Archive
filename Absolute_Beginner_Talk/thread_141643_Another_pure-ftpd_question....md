---
title: "Another pure-ftpd question..."
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Griff on 2006-03-08
I think i have pure-ftpd with pureftpd-admin installed correctly from the wiki.  I've never set up my own ftp server before, but I have used other ftp clients like gftp.  There seem to be two problems.  I can't 'start server' from the pure-admin gui (but I can start pure-ftpd from terminal so not huge deal) and uh...can't figure out how to access ftp from another computer. (like what is the address or whatnot?)  :rolleyes: 
I looked all though the forums and saw nothing similar to this prob so bear with beginner question please.  ;)

---

### Post by Rumor on 2006-03-08
Hello Griff,
I use pure-ftpd on my computer to run my little ftp server. I have set it up using this guide: [http://www.ubuntuforums.org/showthread.php?t=91052](http://www.ubuntuforums.org/showthread.php?t=91052) and it works just fine for me.

As to the address of your server, are you trying to access it from another computer on a local network, or a computer outside the network?

If you want to access if on the local network, you can find out your computer's IP by typing ```
ifconfig
``` in the terminal.

If you want to access it from outside the network, you can go to a site like [http://www.whatismyip.com/](http://www.whatismyip.com/) and read your computer's IP address from there.

---

### Post by Griff on 2006-03-08
[QUOTE=Rumor]Hello Griff,
I use pure-ftpd on my computer to run my little ftp server. I have set it up using this guide: [http://www.ubuntuforums.org/showthread.php?t=91052](http://www.ubuntuforums.org/showthread.php?t=91052) and it works just fine for me.[/QUOTE]

That's the same guide I used; it's on the wiki too.  Were you able to start your ftp service from within pureadmin?  That option is greyed out on my menu.  Also, there are currently 4 comps behind a router here, so we all have the same IP.  And yea, I would like to access stuff from outside the network.  How would I do that now?  Thanks.

---

### Post by Griff on 2006-03-08
Ok.  It was a port forwarding/router/firewall issue.  Users are able to connect to the server, but cannot log in.  The server will accept the user name as correct, but when the correct pass is entered the user recieves an 'authentication' error and is disconected.
Anyone know what is going on here?

---

### Post by deBaas on 2006-03-08
Which option do you use? The virtual users option?
About starting pureftpd, it's probably started by the inet deamon instead of being a deamon itself.

Shouldn't this be in server talk thoug?

---

### Post by Griff on 2006-03-08
[QUOTE=deBaas]Which option do you use? The virtual users option?
About starting pureftpd, it's probably started by the inet deamon instead of being a deamon itself.[/QUOTE]

Yea, they're virtual users.  And I'm not sure how it is started.
And this probably belongs somewhere else now, but when it started I thought it would be an easy answer and I wouldn't have any more problems.  Apparently, I was a little too optimistic.;)

---

### Post by deBaas on 2006-03-08
To use virtual users ther should be a file /etc/pure-ftpd/puredb wich is a symlink to /etc/pure-ftpd/conf/PureDB . That file should point to the right db file. On my pc:
```

/etc/pure-ftpd/pureftpd.pdb

```
Are you sure you executed 
```

#sudo pure-pw mkdb

```
to create this file?

To install "The Internet Superserver":
```

#sudo apt-get install netkit-inetd

```
The file /etc/inetd.conf should contain the following line.
```

ftp	stream	tcp	nowait	root	/usr/sbin/tcpd /usr/sbin/pure-ftpd-wrapper

```
Basacally, the superserver stay active in the background and start pure-ftp whenever there is a call on the ftp port (21).

Good Luck,

---

### Post by Griff on 2006-03-09
Solved! It works! Thank you!
Griff

---

