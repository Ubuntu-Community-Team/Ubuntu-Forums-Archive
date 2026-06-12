---
title: "resolving windows hosts/mapping shares"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by kwyjibo on 2006-04-15
Ok, so i have done a lot of configuring on my new ubuntu install and almost done.  But now I want to be able to map shares of my 2 other windows machine to linux (not permanently, only when i need them and they are on ), plus i want it to resolve their names - this is for easy use of RDP in terminal services.

Currently the host name doesn't allow me to connect as it cant resolve it, although i can connect when using the IP address. although if i run the command smbclient --list hostname -U="User Name" it lists the shares (where hostname is the name and user is user, obviously).  So i'm a little confused as to why?

Basically what I'm asking is, can i add this ubuntu install to the windows workgroup?  can i map drives easily and temporary (some sort of GUI would be nice)?  Can i get it to resolve and pick up all other machines in the domain?

Again i apologise if this is all dumb, i'm extremely new to this and have managed to do quite a lot on my own, but i'm starting to tire  :P

---

### Post by BjornHaland on 2006-04-15
Does this thread help?

[http://ubuntuforums.org/showthread.php?t=160469](http://ubuntuforums.org/showthread.php?t=160469)

I was reading around a few posts and found this.. it seemed like you are attempting to do similar stuff.

---

### Post by kwyjibo on 2006-04-15
ah yes, thanks.  That should help with the mapping at least.

Know anything about workgroups or resolving hostnames though?

---

### Post by kwyjibo on 2006-04-15
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

found that, and that has sorted my resolving issue!  hoorah!

now on to the next issue, speak soon ;)

---

