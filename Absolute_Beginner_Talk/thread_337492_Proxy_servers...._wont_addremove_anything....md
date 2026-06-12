---
title: "Proxy servers....? wont add/remove anything..."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-13
Trying to use add/remove, but when it tries to update the list it gets kinda stuck, then message comes up saying each of these attempts failed:

[http://ie.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_IE.bz2)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_IE.bz2)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_IE.bz2)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_IE.bz2)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_IE.bz2)
[http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_IE.bz2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_IE.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_IE.bz2)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_IE.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_IE.bz2)

Guessing this mite have something to do with me being connected to a proxy server which will only let port80 through? I had same problem trying to install ndiswrapper for my wifi card, command sudo 'apt-get update' leads to 0% 
[Connecting to 136.206.252.254 (136.206.252.254)] [Connecting to 136.206.252

No idea whats going on really...more than little annoying tho.. any help would be brill

---

### Post by el-sio on 2007-01-13
apt needs to know a little about your proxy to fetch your packages ^ ^ 

Let's tell him :

open (or create ) the apt config file with :

```
sudo nano /etc/apt/apt.conf
```

and add the following line before your repository list :

```
Acquire::http::Proxy "http://insert.yourproxyurl.here"
```

save exit and try to update

```
sudo apt-get update
```

but you could have found this answer by yourself with just a litle googling :p

NOTE : if you use password autehntication for your proxy, the line to add in apt.conf should look like that : 

Acquire::http::Proxy "http://myname:mypassword@ourproxy.ourdomain:Portnumber"

---

### Post by john.n on 2007-01-13
this still wont work, if i do that i just get an error saying theres junk at the end of the file...?

---

### Post by john.n on 2007-01-14
Anyone here know what i should do?

---

### Post by 09adi09 on 2007-01-14
Editing the apt.conf file worked for me..

---

### Post by pichinco on 2007-02-02
I've run into the same issue with edgy. I've managed to get apt-get working fine from the command line by editing /etc/bash.bashrc.  I added:

export = http_proxy = http://<username>:<password>@proxyconf

Where proxyconf is the name of an automatic proxy configuration script. The graphical version however will not work. There is something I'm missing. In edgy there doesn't seem to be apt.conf file. I assume there is another location for the configuration of the proxy information that the graphical version uses, but I can't find it. I've tried using the "Network Proxy" app under administration, but it has NO effect. I also can't get Synaptic to work. I've tried entering similar information as shown above into it's network configuration area, but it doesn't work.

Hope this helps others struggling with this issue. I've seen plenty having the same issues, but no fixes offered thus far.

---

### Post by Naikei on 2007-02-21
> **john.n said:**
> this still wont work, if i do that i just get an error saying theres junk at the end of the file...?

A bit late but:

[QUOTE=el-sio]and add the following line ***before your repository list*** :

```
Acquire::http::Proxy "http://insert.yourproxyurl.here"
```
[/QUOTE]

Hope this helps. I failed to take in the "BEFORE" bit :).

NOTE: Another thing I had to do to get things working was to go into Synaptic Package Manager > Settings > Preferences > Network and change from "direct connnection" to inputting my proxy details manually.

Regards,
Naikei
x

---

