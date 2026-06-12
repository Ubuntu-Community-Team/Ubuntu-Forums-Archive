---
title: "OpenSSH Server works, but doesn't start on boot"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Sholainen on 2007-06-03
I have successfully installed OpenSSH Server through Synaptic. The SSH server has been working flawlessly, but only until reboot, meaning that it fails to launch automatically on start-up (even though it should by default--as far as I know). Again, it works perfectly after manually inputting 'sudo /etc/init.d/ssh start'.

This is my first time working with Ubuntu (7.04 'Feisty Fawn') and I have been tackling this problem for some days now, but no method seems to give me any positive results. I've tried adding the command '/etc/init.d/ssh start' into files such as /etc/rc.local, and even tried making a shell script of it to run upon boot, but nothing seems to work.

The OpenSSH Server has worked (launched automatically) for me on a Debian system without any problems, just by installing it with apt-get. Am I neglecting something important? Thanks in advance.

---

### Post by Ek0nomik on 2007-06-03
You could add the command to your startup by going to Preferences/Sessions.

Also, you could right a script to handle it, but you just said that didn't work.  (Which by the way, it should work, you might have just screwed something up?)

---

### Post by Sholainen on 2007-06-03
Thank you for your quick reply, Ek0nomik.

I tried adding the command '/etc/init.d/ssh start' to Preferences/Sessions, but unfortunately it didn't seem to do the trick.

As for the shell script I mentioned before (the one that didn't work), I set it up as follows:

 ```
cd /etc/init.d
sudo nano sshserv.sh
chmod ua+x sshserv.sh
sudo update-rc.d sshserv.sh
```

...where 'sshserv.sh' was composed of:

```
#!/bin/sh
/etc/init.d/ssh start
```

---

### Post by Xappe on 2007-06-03
have you tried reinstalling the openssh-server package? during installation it should've configured the ssh rc.d script to start at boot...

---

### Post by Sholainen on 2007-06-03
> **Xappe said:**
> have you tried reinstalling the openssh-server package? during installation it should've configured the ssh rc.d script to start at boot...I've reinstalled it, removed it completely, and reinstalled it again multiple times (also by using apt-get).

---

### Post by Pollywoggy on 2007-06-06
> **Sholainen said:**
> I've reinstalled it, removed it completely, and reinstalled it again multiple times (also by using apt-get).

Look in /etc/ssh/ and make sure there is no file there that has a name suggesting it will not boot.  Some distributions have a file in /etc/ssh/ that prevents ssh from starting unless the file is first removed, but I don't recall having had to remove such a file in Ubuntu.

Try 'sudo /etc/init.d/ssh start' and if that works, then do this:

sudo update-rc.d ssh defaults

That will generate the default startup links.  For ssh, the defaults will work.

---

### Post by slinky602 on 2007-06-12
I have the same issue, although I see the ssh already in my init.d directory.   Out of chance, I ran the command and this was the response:

daniel@d******:/etc/init.d$ sudo update-rc.d ssh defaults
Password:
 System startup links for /etc/init.d/ssh already exist.


my SSH only starts up only after someone logs into the GUI, while this normally wouldn't be an issue, this is the machine my nieces use when they visit.

Any help on how to start SSH without logging into the GUI would be appreciated.  
- fyi  SSH was installed with the Synaptic Package Manager

--Daniel

---

### Post by carcioni on 2007-06-12
Maybe I am missing something here, but are we trying to support ssh logins to the system, or just have ssh available to do secure connection outbound. 

Shouldn't there be an instance of sshd (the ssh daemon) running to allow inbound connections to ssh? It would usually either be running from boot up, or be started by a process like xinetd when a request came in on the specified ssh port (usually 22).

Not quite sure that I'd want to have 'ssh' start on its own (it's a client not a server AFAIK). I'm relatively new to Ubuntu, but I have lived for a few years in Linux land, and I always run sshd to support connections, not ssh.

Am I OTL here ??

Cheers
D

---

