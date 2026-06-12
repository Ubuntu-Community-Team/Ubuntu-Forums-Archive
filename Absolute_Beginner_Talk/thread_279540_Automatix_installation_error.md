---
title: "Automatix installation error"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by kintsa on 2006-10-18
I tried installing Automatix following instructions from [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

> [B]Installing on (K,X)Ubuntu 6.06 i386,amd64 (Dapper)
[/B]
Edit your sources.list:
[QUOTE]sudo gedit /etc/apt/sources.list 
from terminal (substitute gedit with the text editor of your choice).

Add the following to your sources.list:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Now save the file and close it.

To finish off:
> 
sudo apt-get update
sudo apt-get install automatix2[/QUOTE]


When I type 
> sudo apt-get update 
There is this message
> .
.
.
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems


I in any case continued with installation, there is this message in the middle> 
WARNING: The following packages cannot be authenticated!
  automatix2
Install these packages without verification [y/N]?
Automatix is setup when I press Y

But I get the following error when I try opening Automatix
> Failed to run /usr/bin/automatix.py 'kitty' '/home/kitty' '1000'

Unable to copy the user's Xauthorization file.

---

### Post by arnieboy on 2006-10-18
do the following from terminal
```
 wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
```
and run AX2 again

---

### Post by arnieboy on 2006-10-18
for all further support questions regarding AX, please go to [www.getautomatix.com/forum](www.getautomatix.com/forum)

---

### Post by kintsa on 2006-10-18
Thanks arnieboy.. installed without a problem.

---

