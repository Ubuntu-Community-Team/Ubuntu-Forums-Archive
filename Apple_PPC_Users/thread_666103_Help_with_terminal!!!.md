---
title: "Help with terminal!!!"
date: 2008-01-13
forum: Apple PPC Users
---

### Post by jkman82 on 2008-01-13
I keep getting this message in my terminal when I try to install things on my newly installed
ubuntu 7.04. I was installing files via the terminal, forgot that 1 file was still downloading and put in another one, I guess it stopped the first one.


"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache"

Any help on how to solve this problem would be great,

---

### Post by Pandemic187 on 2008-01-13
Yep, just enter that exact command into a terminal. I can't remember, but you might need to use sudo in order for it to work.

---

### Post by Nero_Flint on 2008-01-13
Just reinstall and this time don't try uploading a file without the other one completing first.

Let us know if that works.

---

### Post by jkman82 on 2008-01-13
when I try to reinstall, I just get that same code back, and when I enter in the run dpkg, I get nothing, even with sudo

---

### Post by jkman82 on 2008-01-13
could I possibley remove what I installed even thought It did not install completely?

heres the command I put into the terminal that is messed up as of now

sudo aptitude update && sudo aptitude upgrade

---

### Post by jkman82 on 2008-01-13
anyone?

---

### Post by oswaldkelso on 2008-01-14
> **jkman82 said:**
> could I possibley remove what I installed even thought It did not install completely?

heres the command I put into the terminal that is messed up as of now

sudo aptitude update && sudo aptitude upgrade

  To remove an installed elvis package:
          sudo  dpkg -r elvis

Just put the package name you were installing  in after  dpkg -r 

type "man dpkg" without quotes in a terminal for more options

---

