---
title: "Access my computer from via the internet?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Aussie on 2006-07-04
Hi all,

I've been using Ubuntu since breezy was first released, so I'm not a total noob when it comes to linux.  I'm new to servers and very confused so you may have to bear with me.  

Essentially what I want to do, is be able to access my Ubuntu desktop from either my XP computer at the office or my brother iBook running osX from his place.  I've been searching the forums, but it's really hard to find when I don't know what the hell i'm looking for. 

Is it also possible to access files from the ubuntu machine as say a networked drive on the XP and OSX machines.

I'd also like to make this secure aswell, but don't eve know where to begin.

Thanks.

---

### Post by aysiu on 2006-07-04
This may help...
[http://doc.gwos.org/index.php/BreezyFreeNX](http://doc.gwos.org/index.php/BreezyFreeNX)

---

### Post by scxtt on 2006-07-04
SSH for terminal access [ install openssh-server ]
VNC for X viewing [ install vncserver or x11vnc (or tightvncserver / xtightvncserver) ]

then all you have to do is forward the right ports (22 for ssh, 5900 for vnc) from your router to your boxes IP address (and know your modem's IP address so you can connect to it from somewhere else) ...

note that you'll also need clients (ssh and vnc) on the boxes you're connecting from ...
[indent]check out putty for connecting to an SSH server in XP ...
check out RealVNC for connecting to VNC server in XP ...[/indent]

you're on your own for anything mac related :p

---

### Post by Aussie on 2006-07-04
Thanks heaps for the quick replys.

Sorry,  I forgot to mention that I'm now using dapper.

So is FreeNX what I need to set up to be able to do this?  How secure is it?  Will random people be able to gain access to my ubuntu machine if it is always on without me knowing?

Also how hard is it to set up freeNX?

---

### Post by killernurd on 2006-07-05
It looks like it's not that difficult to set up FreeNX - I added Seveas's Dapper repository to my apt sources, and installed the freenx package.

```

#sources.list
deb http://mirror.ubuntulinux.nl dapper-seveas all

```

Then:

```

tony@lugh:~$ sudo apt-get install freenx

```

However, while I've been able thus far to *connect* just fine, I have yet to get an actual desktop, though I'm not sure why.

As to security, NX uses SSH to transmit data. It's actually idle until someone attempts to connect, at whichpoint an SSH connection is opened under the user 'nx' - the server itself isn't a daemon, it just listens along with sshd.

I'm not sure if I need to add myself as an NX user, though... when I connect as myself using my Linux machine's login, it connects fine, but doesn't display my desktop. *shrug*

As for finding active nx connections...

```

root@lugh:~# nxserver --list

```

Alternatively:

```

tony@lugh:~$ ps aux | grep ssh

```

and look for 'ssh: nx'

---

