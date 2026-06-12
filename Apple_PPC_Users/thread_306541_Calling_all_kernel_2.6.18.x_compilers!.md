---
title: "Calling all kernel 2.6.18.x compilers!"
date: 2006-11-25
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-25
What are your favorite kernel options for a G5?

Ok, I've successfully compiled several vanilla kernels now for my G5 iMac using g5_defconfig and then manually adding some options using makemenuconfig.  

[http://www.ubuntuforums.org/showthread.php?t=299360](http://www.ubuntuforums.org/showthread.php?t=299360)

The latest that I compiled was 2.6.18.3 which is running great so far. 

The only things I configured it for beyond g5_defconfig was:

kernel freq: 1000 hz desktop use
Netfilter Xtable
IP Tables support (for possible future firewall)

I'm having a blast reading about these compile options online, and my old Running Linux book from 1995 is no longer relevant :)

I'm not looking for complete explanations, but maybe pointers to your favorites so I can study them and see if they fit *my* needs.

I'm aware of the risks of using vanilla kernels, and I'm really interested in stability options, not speed.  I'm not running any servers, just your standard desktop using dsl for connectivity.
 
As always, thanks!

---

### Post by stream303 on 2006-11-27
Ooops..  found this very subject in the HowTo guides forum... switching to decaf! :)

---

