---
title: "Trouble with Edgy live CD"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-01-04
I have used Dapper in the past until I had trouble with your upgrade to Edgy a couple months ago and it crashed. I now have cleaned up the partition and burned a copy of Edgy. The live CD opened fine except when I open Firefox I can only go to a couple Ubuntu sites and it won't let me go to Yahoo or Google. Why? If it can go to a Ubuntu site it should be able to go to any site. 

So far my experience with Ubuntu has been fine with Dapper but Edgy seems unstable. 

What is wrong? How can I fix the browsing problem?

---

### Post by kebes on 2007-01-04
Are you sure the "ubuntu sites" you are seeing are web-sites? They might be files on the CD that you are browsing. Look in the titlebar and see whether it says "http://" or "file://".

If you were actually looking at files, try going to other sites and see if they work. If no networking is working, you can activate it in the usual way (open Network Settings, etc.). You may have to enter your DNS settings, and so on (depending what your setup is).

If you were able to access ubuntu sites but not other sites (like google) then that's very strange. Did you enter DNS server settings? It could be a problem with your internet host's DNS server. You can switch to openDNS ([http://www.opendns.com/](http://www.opendns.com/)) and see if that fixes it. You should also try using "ping" on the commandline and see if it works:
ping 127.0.0.1
ping localhost
ping [www.google.com](www.google.com)
ping [www.ubuntuforums.org](www.ubuntuforums.org)
etc.

---

### Post by geovino on 2007-01-04
I fixed it, I've seen this happen before in other distros using Firefox.

go to: about:config

scroll down to: network.dns.disableIPv6 and set it to true. That's it. I don't know why this happens but once its set it works fine.

---

