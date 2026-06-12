---
title: "leningradskaya.canonical.com RU-legit ??"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by voltsy on 2007-03-29
My Dapper Drake box seems to spend hours connected to 91.189.88.31:80 and I cannot figure out why it is connecting or what it is doing (if anything) whilst connected.

I can easily see the connection with 

netstat -an|grep tcp

and this connection persists for a long time even after I close all my browsers and close all package managers. traceroute resolves the address to leningradskaya.canonical.com, and if I point my browser there, it appears to be a very new set of ubuntu-related folders.

what seems strange to me is that this site is NOT listed in my /etc/apt/sources.list file

chkrootkit says I'm clean, but is it time to install f-prot to search for nasty "gremlins"? If canonical/ubuntu are running this site legitimately, why do I have a persistent connection established to it?

thanks ;-)

---

### Post by dbbolton on 2007-03-29
that's really strange. i don't know what "leningradskaya.canonical.com" is, but since it is a second level domain of canonical.com, i'm guessing that you have nothing to worry about.

---

### Post by FidalgoMike on 2007-04-10
I'm thinkin' this might be related to this thread:

[http://ubuntuforums.org/showthread.php?p=2430875#post2430875]("http://ubuntuforums.org/showthread.php?p=2430875#post2430875")

Are you running Firestarter?

---

