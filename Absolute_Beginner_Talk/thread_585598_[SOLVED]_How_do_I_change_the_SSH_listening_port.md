---
title: "[SOLVED] How do I change the SSH listening port?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by evilregis on 2007-10-21
I am setting up an Ubuntu machine for my dad.  I'd like to be able to remotely admin it for him.  So I'm trying to set up SSH/VNC (or FreeNX -- anyone got this working in Gutsy yet?) on it.

I've edited /etc/ssh/ssh_config and changed the port value to 8443 but every time I run a portscan on it I get SSH service open on 22.  I've restarted the ssh service, I've rebooted.

Am I editing the wrong file?

---

### Post by HermanAB on 2007-10-21
You edited the wrong file. The SSH server is configured with /etc/ssh/sshd_config.

Change the Port command to (close to the top):
Port 2222

Then restart sshd.

Now connect with:
ssh -p 2222 user@server

Cheers,

Herman

---

### Post by evilregis on 2007-10-21
Thanks!  That did the trick.

---

### Post by Dr Small on 2007-10-21
Open your sshd configuration file:
```
sudo nano /etc/ssh/sshd_config
```

Find:
```
Port 22
```

Change this to:
```
Port 8443
```

Save the file by pressing:
```
CTRL + O
```

And exit nano by pressing:
```
CTRL + X
```

Restart sshd:
```
sudo /etc/init.d/sshd restart
```

Dr Small

---

