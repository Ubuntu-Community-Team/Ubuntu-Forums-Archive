---
title: "Error in Synaptic"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-04
I am downloading and installing some stuff using Synaptic. after the download is done and while applying changes: (Changes applied) where it shows the process in terminal (black background) ... when finished and gave me this error:

The following problems were found on your system:
E: setiathome: subprocess post-installation script killed by signal (Interrupt)

what's wrong? it happened like twice now ... please help!

---

### Post by louis_nichols on 2006-05-04
Well... it hangs at download time. It's most probably because the servers are down or something., It's not actually a synaptic issue. The particular package setiathome is one that just contains some scripts that download the setiathome package from its homesite (its licence prevents it from being distributed directly with Ubuntu) and then installs it.

Installing any other package will work fine.

---

### Post by Isoss on 2006-05-04
Well ...  I see that a lotta important installations use this package, such as aMSN and Mercury-Messenger ...
In Terminal it's:
```
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...

```
it just stops right after the three dots .. I can't do anything untill I hit Ctrl+C ... is there any solution for this? and if it's because the server is down , I can't just wait till the server is "up" ... there got to be some solution or substitution for this!

I mean, why do I always have to be under the mercy of servers??? ](*,)

---

### Post by catlett on 2006-05-04
There are other ways to install programs without synaptic, it's just that synaptic is extremely easy and efficient. 
There is no way to install from a server when it is down. You either wait or compile the install yourself. 
Google the package you want. Find the Linux compatable download. There are 2 file types that work easily with Ubuntu, "deb" files and "tar.gz" files. You can install either file by following this guide [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) . This way you don't have to wait for servers and synaptic.

---

### Post by Isoss on 2006-05-04
Alright .. I guess you are right ... but I really wanna make sure that server is down. Just wanna know it's really the server or it's just my connection ... cuz I am using proxy-server .. cuz sometimes some website just don't work with my ISP while it works with other ISP's. 

Thanks.

---

### Post by louis_nichols on 2006-05-05
[QUOTE=Isoss]Well ...  I see that a lotta important installations use this package, such as aMSN and Mercury-Messenger ...
In Terminal it's:
```
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...

```
it just stops right after the three dots .. I can't do anything untill I hit Ctrl+C ... is there any solution for this? and if it's because the server is down , I can't just wait till the server is "up" ... there got to be some solution or substitution for this!

I mean, why do I always have to be under the mercy of servers??? ](*,)[/QUOTE]


I think the problem is somewhere else, about other packages. amsn surely doesn't need setiathome.

So what you should do first is do a complete removal of setiathome and then try to install other packages.

otherwise, synaptic will try to configure packages not completely installed before installing others. (I think :) )

---

