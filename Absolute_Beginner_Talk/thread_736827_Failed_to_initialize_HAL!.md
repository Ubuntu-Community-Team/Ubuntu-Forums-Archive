---
title: "Failed to initialize HAL!"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Johnmacey on 2008-03-27
I have an IBM ThinkCenter (desktop)  with Win XP installed  Using Wubi I installed Ubuntu as part of the Windows environment, and this worked well.  Recently I was offered the opportunity to upgrade to v. 7.10,  which I did.  That's when I got the "Internal Error" message about  HAL. At the Command prompt and typed in : sudo apt-get install HAL.
 The response was:"Reading package lists - DONE
                             Building Dependency tree
                             Reading State Information - DONE
                             Couldn't find package  HAL" 

Please help
johnmacey

---

### Post by Johnmacey on 2008-03-27
moving to installation

---

### Post by philinux on 2008-03-27
HAL is not the name of the package. It's Hardware Abstraction Layer. And it's installed from day one.

Have you tried rebooting.

---

### Post by bumanie on 2008-03-27
Hardy heron alpha 3 did that to me. The only way I could get the computer started was by reinstalling. There may be a fix, but I don't know it. See if this link helps
[http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/](http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/)

---

### Post by Johnmacey on 2008-03-28
Well, I don't know why, but now the error message no longer exists.  What I did was to go to Applications > Accessories > Terminal  and type:  sudo  hald  --daemon=no  --verbose=yes
This told me what was going on and apparently somehow the cache was not available.  I tried several of the suggested solutions, none of which seemed to work.  But on one of the many reboots, suddenly, everything was working.  I just hope it's still working at the next start-up.          Thanks to all who responded.                                                       johnmacey

---

