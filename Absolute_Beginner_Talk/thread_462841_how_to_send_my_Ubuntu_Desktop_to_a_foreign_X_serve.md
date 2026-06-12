---
title: "how to send my Ubuntu Desktop to a foreign X server (7.04) ?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by light333 on 2007-06-03
Hi,

I have 2 PC's, one with an X server and one running Ubuntu 7.04. I want that the whole Ubuntu
X session, including the desktop and all X applications, will be displayed on the X server that I have
on the other PC.

is that possible ?

Thanks,
Light

---

### Post by arkham on 2007-06-06
Yes it is possible, and to accpmlish it I recommend using the sh approach for security - otherwise everything you type on the remote X session will be sent in plain text over the network.

I will assume you are logged into the Ubuntu machine and wish to run prgram on the remote X server.  Run the following command and sub in for the actual xserver:

```
ssh -X user@xserver
```

Once you log in you will then be able to execute remote commands, such as gnome-terminal, Firefox or gimp etc. - they will run on the remote machine but display on your Ubuntu machine

Some applications may now require a -Y option rather than -X (for trusted forwarding) so you can try that if you get any weird application errors.

If the command does not work, then make sure that the X server is set up to allow forwarding in the /etc/ssh/sshd_config file like so:

```
X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
```

Hope it helps

---

