---
title: "where i can obtain libssl.so.4 ?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-01
Hi
I am trying to install one of my applications and it log an error related to libssl.so.4 file
It says that this file is not present in my system, 

what can i do?

Thanks

---

### Post by sankarv on 2007-06-01
This is ok , i suppose.....


[http://rpm.pbone.net/index.php3/stat/3/srodzaj/1/search/libssl.so.4]("http://rpm.pbone.net/index.php3/stat/3/srodzaj/1/search/libssl.so.4")

---

### Post by beatbros on 2007-06-01
Hi,
it seems that some hardlink stuff is missing:

in /usr/lib you should  find:

libcrypto.so.0.9.8 
libssl.so.0.9.8

Then you can create links like this for .4:

cd /usr/lib
ln -s libcrypto.so.0.9.8 libcrypto.so.4
ln -s libssl.so.0.9.8 libssl.so.4

And for .6:
ln -s libcrypto.so.0.9.8 libcrypto.so.6
ln -s libssl.so.0.9.8 libssl.so.6


bye

---

### Post by legolas_w on 2007-06-01
Hi
thank you for your reply

Can  you please tell me what should i do about **libreadline.so.4** ?
I searched inside /usr/lib and there is not file like that there.
Thanks

---

### Post by sankarv on 2007-06-01
goto 


[http://rpm.pbone.net/index.php3]("http://rpm.pbone.net/index.php3")


there u type libreadline.so.4 in the search and u will get the rpm of 'readline'. i suppose installing that could solve ur problem.....

---

### Post by legolas_w on 2007-06-01
Thank you for reply.
How i can install rpm in ubuntu?
I thought Ubuntu use deb file and does not support rpm.

Thanks

---

### Post by mlentink on 2007-06-01
use alien to convert from rpm to deb

---

### Post by sankarv on 2007-06-01
i think theres rpm utility for ubuntu too. its ur choice to install it from .rpm/.deb....

---

### Post by mlentink on 2007-06-01
You might want to take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=457274&highlight=convert+rpm+to+deb")

---

### Post by mahalie on 2007-11-02
I don't know what you're trying to install but I'm trying to install Plone and the instruction say:
> Ideally, you should also have the libssl and readline libraries and development headers loaded. These are not required, but add desirable functionality. libssl is required to use TLS with your mail server, which may be vital if it's not local. See the Unified Installer README.txt for details.
Googling libssl didn't return anything decipherable by me. I don't understand the above statement AT ALL. If anyone could hand me a clue, I'd love it!

---

