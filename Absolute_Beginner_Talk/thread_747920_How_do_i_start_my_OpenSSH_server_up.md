---
title: "How do i start my OpenSSH server up"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by buttheadxa on 2008-04-07
How do I make this work...I am a Nooblet....

---

### Post by Crafty Kisses on 2008-04-07
Assuming that your server hostname is userver.mydomain.com and username is butthead, you need to type the following command:

```
ssh butthead@userver.mydomain.com
```

To start SSHs server, enter:
```
sudo /etc/init.d/ssh start
```

Then if you ever want to restart the OpenSSH server, you'd have to do this:
```
sudo /etc/init.d/ssh restart
```

---

### Post by wormser on 2008-04-07
You need to be more descriptive in your questions.  We have to guess what you are trying to do.  Are you trying to install OpenSSH?  If so: Applications> Accessories> Terminal

```
sudo apt-get install openssh-server
```

---

### Post by hyper_ch on 2008-04-07
ssh server is a daemon which will - unless it's not installed or has been tampered with - autostart upon boot.

---

