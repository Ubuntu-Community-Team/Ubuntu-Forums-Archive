---
title: "Command line Bitttorrent"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-09-30
Hi i'm after a tutorial on how to install and configure a command line client bittorrent.  
Does any one know where i may look. 

In future i will be looking into getting a server where i can issue ssh commands to the bittorrent. However at the moment i just want to be able to set it up over my local machine,
Thanks in advance.

---

### Post by sab0403 on 2007-09-30
Doesn't wget work for torrents?

---

### Post by sab0403 on 2007-09-30
Oh well. I guess not.

Anywhere, here's a decent tutorial - Google is your friend.

[http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html](http://www.cyberciti.biz/tips/linux-command-line-bittorrent-client.html)

---

### Post by pfwd.tech on 2007-09-30
Yeah i was trying this before but got stuck so i gave up.
This is where im getting problems. 
```
sudo rpm -ivh BitTorrent-5.0.3-1-Python2.4.noarch.rpm
error: Failed dependencies:
        /usr/bin/python2.4 is needed by BitTorrent-5.0.3-1.noarch
        python >= 2.3 is needed by BitTorrent-5.0.3-1.noarch
        python(abi) = 2.4 is needed by BitTorrent-5.0.3-1.noarch
        python-crypto >= 2.0 is needed by BitTorrent-5.0.3-1.noarch
        python-psyco is needed by BitTorrent-5.0.3-1.noarch
        python-twisted >= 2.0 is needed by BitTorrent-5.0.3-1.noarch
        python-zopeinterface is needed by BitTorrent-5.0.3-1.noarch
        wxPython >= 2.6 is needed by BitTorrent-5.0.3-1.noarch

```
Where would i get these dependencies from do you think?

---

### Post by Acglaphotis on 2007-09-30
Try rtorrent

---

### Post by pfwd.tech on 2007-09-30
I Have Python version 2.5.1 and have just fully updated my machine via apt-get update etc 
Not sure what to do now

---

### Post by pfwd.tech on 2007-09-30
Whats the difference with rtorrent and bittorrent?

---

### Post by metroplex on 2007-09-30
rTorrent is for sure the client to recommend. Have a look at:

[http://en.wikipedia.org/wiki/Rtorrent](http://en.wikipedia.org/wiki/Rtorrent)

and

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by pfwd.tech on 2007-09-30
Ok will give it a go thanks

---

### Post by metroplex on 2007-09-30
> **pfwd.tech said:**
> Whats the difference with rtorrent and bittorrent?

rTorrent is an actual client program. BitTorrent is usually the term describing the protocol (method) used to distribute files.

---

### Post by MetalMusicAddict on 2007-09-30
You can use bittornado. "bittornado - Bittorrent client with enhanced curses interface"

Command looks something like: **btdownloadheadless.bittornado /path/to/.torrent**

---

### Post by pfwd.tech on 2007-09-30
Do you know how i can check to see what ports i can open.  I've tried the following but get errors
```
sudo iptables -A INPUT -p tcp --dport 6890-6999 -j ACCEPT
iptables v1.3.6: invalid port/service `6890-6999' specified
Try `iptables -h' or 'iptables --help' for more information
```

Taken from [http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-Version-of-rTorrent-51166.shtml)

---

### Post by mikewhatever on 2007-09-30
You've tried to open about a 1000 ports, what for? Not only is it unnecessary, but also insecure. One open port is all it needs.
[http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

---

### Post by pfwd.tech on 2007-09-30
I know i tried one port a first but then thought i should follow the guide on the site as it had a range

---

### Post by pfwd.tech on 2007-09-30
great  thanks that worked fine

---

