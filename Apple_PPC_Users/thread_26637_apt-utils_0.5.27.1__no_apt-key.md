---
title: "apt-utils 0.5.27.1  no apt-key ?"
date: 2005-04-13
forum: Apple PPC Users
---

### Post by jkr on 2005-04-13
Ok so I need a development version to get w32codecs?

can't do 
 
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

as apt-key doesn;t exist  
any ideas?

cheers

---

### Post by jkr on 2005-04-14
=; 

Ok So I RTCFM  (the correct one).
Appears apt-key is indeed part of apt-utils 0.6 and all the secure gpg stuff is not for 
4.10 - ok no problem.  

finally solve it by manually getting required package as an i386.deb and doing dpkg -i --force-architecture - et VOILA!

If it wasn;t just a load of codecs I would have opened it first to see where stuff was going honest ;-)

---

