---
title: "Ubuntu Server"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by wrighty on 2007-08-28
Just installed the sever edition on an old Pentium 3.  I want to run a LAMP server I can test sites, run an intranet, etc.

Because of the limited memory the machine went into "low memory mode" during install.  I have ended up with no graphic interface just a DOS like prompt.  In itself, this is not a problem.

I have had it up and running and shown that Apache is working by accessing it from a Windows machine on the network.

I have installed the FTP server and tested it as above.

The problem is that the FTP server does not point to where Apache expects to find web pages and I cannot navigate to that folder with my Windows FTP client.

Can anyone help?  You will have realised that I am really a Windows man - but willing to learn.

Thanks,

Ian

---

### Post by hyper_ch on 2007-08-28
Well, the whole reason of using a server setup is to load as little features as possible so the server has as many resources at disposal as possible... hence you have no gui ;)

Furthermore, why do you want to have FTP? SFTP/SCP should be a lot simpler:

(1) install openssh-server
```

sudo apt-get install openssh-server

```

(2) Get a SCP-capable program on windows:
[http://www.winscp.com](http://www.winscp.com)  --> free

(3) Connect to the server with using your user/password that you have on the server

(4) If you cannot write to /var/www you may need to chown/chmod it accordingly.

If it's just you who is accessing the server to do stuff on it, I think that's the simplest way...

---

