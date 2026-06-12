---
title: "Error authenticating some packages libmono-accessibility1.0-cil"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-12-29
I'm getting this error when I click on the upgrade icon:

Error authenticating some packages 
It was not possible to authenticate some packages.
See below for a list of unauthenticated packages.
libmono-accessibility1.0-cil

I've retried updating over several days.
Does this have to do with a missing public key?
If so, where do you obtain the public key?

Thanks

Carl

---

### Post by fiddledd on 2007-12-30
I've had similar problems before with Update manager. The fix was to type: 'sudo apt-get update' in the terminal and run the update again. Upto now it works and you don't get the Authentication error.

---

