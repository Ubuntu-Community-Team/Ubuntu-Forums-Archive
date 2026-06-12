---
title: "can't link to an ISP"
date: 2010-06-05
forum: Apple Hardware Users
---

### Post by davidpaterson on 2010-06-05
Morning folks. (I am in New Zealand on a cold wet winter's day)
 I guess previous  answer to my question topic are   here on the forum somewhere but  *just can't find it*. 
I have a fairly new IMac with a Intel dual core chip. And I now have loaded it with Ubuntu 10.04. I use a wireless broadband. Ie I get a signal from a mast some distance away to an antennae on my roof which is then linked to box on my desk which links to my computer via ethernet cable.  It works just like standard broadband but it just doesn't  come by a copper telephone wire.  The link worked fine  with MacOs  and still works fine with a PC laptop. I have tried just about everything but I cant link my computer to my ISP. 
Using terminal  with various different commands all I get is a lot of information that is meaningless to me except there is a common thread which amounts to "not connected".
I was starting to think that was a missing driver  issue but my ISP, who knows nothing of Ubuntu, poo pooed that. 
Any suggesstions please
David

---

### Post by linuxopjemac on 2010-06-06
cannot you hook it up to a cable and do :
```

sudo apt-get update
sudo apt-get upgrade
```

and then go to Administration -> Hardware and find the appropriate driver...

Can you give us the output of:

```
lspci -vvnn | grep 14e4
```

---

### Post by sha.goyjo on 2010-06-06
If it is a driver issue, I'd suggest using the solution posed by linuxopjemac. Another thing to consider is that often times, even though a device "functions" in linux, it may not have quite the signal reception strength it did before. Downsides of trying to use VERY proprietary devices in a distinctly unproprietary enviroment.

---

### Post by davidpaterson on 2010-06-09
Thank you for your input. Unfortunately when installing Ubuntu everything was erased on the HD and no drivers to be found. I reinstalled Mac OS and did a reinstall of Ubuntu side by side with MacOs. That works fine now. Why? don't know but this might help some with similar predicament. 

David

---

### Post by sha.goyjo on 2010-06-09
Could you clarify? Is the cellular modem now working fine when you boot into linux?

---

