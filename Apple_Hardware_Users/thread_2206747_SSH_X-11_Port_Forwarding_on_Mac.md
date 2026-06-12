---
title: "SSH X-11 Port Forwarding on Mac"
date: 2014-02-20
forum: Apple Hardware Users
---

### Post by thault on 2014-02-20
I've got a MacBook Pro and I was wondering how to X-11 Port forward via SSH from my ubuntu 12.04 lts server? On my Windows laptop i had to download X-ming to handle the port forwarding. Do I have to do that as well on the Mac?

---

### Post by brokenhachi on 2014-02-20
since OSX has a similar bash shell, you just need to enable the ssh switch for x11 forwarding, which i believe is ```
ssh -X *user@ip*
```

Found this on the googles for ya: [http://dyhr.com/2009/09/05/how-to-enable-x11-forwarding-with-ssh-on-mac-os-x-leopard/](http://dyhr.com/2009/09/05/how-to-enable-x11-forwarding-with-ssh-on-mac-os-x-leopard/)

---

### Post by thault on 2014-02-20
For when I specify the port would it be?
```
ssh -x -p xxxx user@ip
```

---

### Post by Lars Noodén on 2014-02-20
Normally it is port 22, which is the default.  If you have not gone out of your way to change the port on the OS X machine you can leave that part off when you connect.  It will then look for the standard port.

---

### Post by thault on 2014-02-20
I connect to my server outside of the network so I changed the port to a different one for security purposes.

---

### Post by Lars Noodén on 2014-02-20
Use the port that you configure for sshd then, if it is non standard.  But be sure to [use the capital X](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh.1.html) instead of lowercase x, they mean different things.  The capital X enables X11 forwarding.   [s]I'm not sure how many applications will work with X any more on OS X. You may have to tunnel VNC.[/s]

Edit: going from the Ubuntu machine to the OS X machine should be fine as-is.

---

### Post by thault on 2014-02-20
Vnc?

---

### Post by Lars Noodén on 2014-02-20
Sorry.  I got confused as to the direction.  Running programs on the Ubuntu machine and displaying them on the OSX machine should work fine using X11 forwarding.  VNC is a clumpier method of displaying remote graphics.  But it is insecure, so it has to be tunneled over SSH if used.  It's probably not relevant here since X11 should work.  If there is a lot of network latency the program can feel sluggish though.

---

### Post by brokenhachi on 2014-02-20
You've got it right with -p for port, and as Lars mentioned, it needs to be **X**, not *x*

---

### Post by 1clue on 2014-02-20
Why mess with the port?  By default, the ports match up.  I would only move the port if something is exposed to the outside world.

You want XQuartz on your Mac, and you also might want to look at homebrew for the Mac.

XQuartz is the best X server I know of for the Mac.  Pretty much zero configuration on your part.

Homebrew [http://brew.sh](http://brew.sh) is a bunch of open source software for your Mac, it has a package manager built-in.  Everything is installed in a single directory then symbolically linked to directories in your PATH.  There is an easy script to uninstall, and it works.

I do this all the time.  You just** ssh -X <your_linux_box_ip>** and then **firefox** or whatever.

---

### Post by Lei_Jiang on 2014-02-20
I often do **ssh -Y**. Looking at ssh man page it's almost same as **-X** except it's exempt from X11 security extension controls.

Also if you get complaint about dbus errors, consider prefixing your command with **dbus-launch**. Lots of X11 applications are relying on dbus nowadays.

---

