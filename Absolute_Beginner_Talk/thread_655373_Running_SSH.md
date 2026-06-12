---
title: "Running SSH"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by m i k e on 2008-01-01
I want to be able to connect to my computer via SSH.  Does Ubuntu come with an SSH server preinstalled?  If not what would be the best one to use and how would I get it?  apt-get?  Thanks.

---

### Post by astoltz on 2008-01-01
The client is installed by default but the server is not.  Just install the "ssh" package. ```
sudo apt-get install ssh
```

---

### Post by jimrz on 2008-01-01
```
sudo apt-get install openssh-server
```
Works well for me. You can also use Synaptic to install it.

---

### Post by astoltz on 2008-01-01
ssh is just a meta package that will install both openssh-server and openssh-client.  Since the client is already installed by default, both those commands will result in the same action.

---

### Post by m i k e on 2008-01-01
Thanks for the replies.  This worked perfectly:
```
sudo apt-get install ssh
```

Now... I am going to be using wake-on-lan so I want to be able to log in via vnc while the Ubuntu is at the login screen but Ubuntu doesn't start the remote desktop service until you log in.  So is there anyway to set remote desktop to initiate before login (preferable) or how can I start vnc from ssh?  Thanks.

---

