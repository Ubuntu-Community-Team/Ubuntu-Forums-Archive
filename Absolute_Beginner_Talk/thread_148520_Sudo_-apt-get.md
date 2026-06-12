---
title: "Sudo -apt-get"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Leeghoofd on 2006-03-22
This command gives me several error messages which all appear to come down to the following: cannot initiate the connection to 80:80(0.0.0.80)

Now it looks to me that some config file still has the standard internet settings and that i need to enter my proxy info in order to solve this "error"
I've managed to enter the proxy information into the synaptic app and the
firefox browser and both can connect to the internet

Where do I set up proxy info in order for my sudo command to function properly? 

Again thx and sorry for all the questions :confused:

---

### Post by localzuk on 2006-03-22
I know there is a way of setting it in your /etc/apt/apt.conf file (I think that's its name) but I am not sure what it is.

To do it manually by typing these before you run apt-get

```

export http_proxy="http://proxyserver:port"
export ftp_proxy="http://proxyserver:port"

```

---

### Post by public_void on 2006-03-22
See this [post](http://www.ubuntuforums.org/showthread.php?t=123984&highlight=proxy) on editting apt.conf with proxy details to get apt-get working.

---

### Post by Leeghoofd on 2006-03-22
thx public void.

I had actually already done the following

Setting up apt-get to use a http-proxy
gedit ~/.bashrcadd these lines to the bottom of your .bashrc file 

http_proxy=http://yourproxyaddress:proxyport
export http_proxy

However it appears I screwed the proxy setting line somehow. Changed it and it works fine now. Thx for the assistance.

---

