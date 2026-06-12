---
title: "Configuring apt-get"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-08-05
I did a fresh install of Ubuntu 5.04 today. I am very impressed by it's simplicity and the fact that every thing - right from my mp3 player to sound card worked fine. My laptop is connected to the internet through a proxy server. How do I configure apt-get to install packages from the internet?

 Regards, 
 Chandan

---

### Post by Sam on 2005-08-05
If you set your proxy from System, Preferences, Network Proxy, doesn't it do the trick ?

---

### Post by fng on 2005-08-05
open up /etc/profile in your favorite editor.
```
sudo nano /etc/profile
```
Scroll to the bottom of the file and add the following 2 lines (change the proxy address/port into your proxy address/port):
```
http_proxy="http://proxy.ubuntu.com:8080"
export http_proxy
```
If your proxy needs a username/password to connect ot the internet use this:
```
http_proxy="http://username:password@proxy.ubuntu.com:8080"
export http_proxy
```

log out
log back in and apt should be using the proxy now

---

### Post by jaqkar on 2005-08-05
Chandan

I also did my first install yesterday and had a similiar issue, what worked for me was as Sam said: System, Preferences, Network Proxy. But then I also did this on the Ubuntuguide: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Cheers
J

---

### Post by cnayak on 2005-08-05
finally, i managed to get apt-get working. It's an amazing piece of software. thanks to all those great people who helped.

 chandan

---

### Post by cnayak on 2005-08-05
I tried configuring Synaptic Package Manager using the following format in  

    http://<myusername>:<passwd>@10.8.11.3:80
 and ftp://<myusername>:<passwd>@10.8.11.3:80

 However, download the repo fails.It works in the text mode though. What's wrong ?

---

