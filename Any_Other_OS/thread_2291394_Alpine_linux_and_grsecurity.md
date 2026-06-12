---
title: "Alpine linux and grsecurity"
date: 2015-08-19
forum: Any Other OS
---

### Post by HardTrickySecurity on 2015-08-19
I didnt know where to post it, feel free to move it.

I am using Alpine linux distro and trying to run the tor browser bundle .

[http://alpinelinux.org/](http://alpinelinux.org/)
[https://www.torproject.org/](https://www.torproject.org/)

Thing is, I have to execute start-tor-browser script, so in terminal I put command:

/home/alex/tor-browser_en-US/Browser/start-tor-browser

Nothing happens, the browser wont start cause Alpine Linux is using Trusted path execution, grsec.

Now if I put command, and enter my password: 

sudo /home/alex/tor-browser_en-US/Browser/start-tor-browser

The browser starts without problem but the script is not suppose to be run as root or with root privileges, I think that running it with sudo is not secure at all and is not recommended.

The same goes for this other browser, I have to execute flashpeak-slimjet script

[http://www.slimjet.com/en/dlpage.php](http://www.slimjet.com/en/dlpage.php)

Is there anyway I can run the scripts without using sudo?
Or do I have to disable trusted path execution option in the kernel? If yes, how can I do that?
Or is imposible to run this 2 browsers in Alpine Linux distro?

---

### Post by howefield on 2015-08-19
> **HardTrickySecurity said:**
> I didnt know where to post it, feel free to move it.

Thread moved to the "*Any Other OS*" forum.

---

