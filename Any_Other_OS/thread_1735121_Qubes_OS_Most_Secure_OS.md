---
title: "Qubes OS Most Secure OS?"
date: 2011-04-20
forum: Any Other OS
---

### Post by Rashedul on 2011-04-20
I'm not sure if this has been discussed already but I just came across this and found it really intriguing. Ignoring the obvious response that the biggest security hole is the user, I think this type of virtualization/sandboxing is quite interesting. This kind of disposable VM and sandboxing is probably a bit more memory intensive and I probably don't need something like this but I thought I'd just bring a link about the OS to the surface anyway. Check it out: 

[http://qubes-os.org/Screenshots.html](http://qubes-os.org/Screenshots.html)

---

### Post by Megaptera on 2011-04-21
Interesting, thanks but I can't play with it 'cos ....
Hardware Requirements

Minimum:

4GB of RAM
64-bit Intel or AMD processor (x86_64 aka x64 aka AMD64)
Intel GPU strongly preferred (if you have Nvidia GPU, prepare for some troubleshooting; we haven't tested ATI hardware)
10GB of disk

---

### Post by Spice Weasel on 2011-04-21
OpenBSD and Tinfoil Hat are the most secure OSes.

---

### Post by Dlambert on 2011-04-23
Agree with BSD, might be confusing at first, but its secure.

---

### Post by codell on 2013-02-03
OpenBSD security is a myth. They don't even have signed updates.

---

### Post by Claire Voyant on 2013-11-19
> **Rashedul said:**
> I'm not sure if this has been discussed already but I just came across this and found it really intriguing. Ignoring the obvious response that the biggest security hole is the user, I think this type of virtualization/sandboxing is quite interesting. This kind of disposable VM and sandboxing is probably a bit more memory intensive and I probably don't need something like this but I thought I'd just bring a link about the OS to the surface anyway. Check it out: 

[http://qubes-os.org/Screenshots.html](http://qubes-os.org/Screenshots.html)

I have been fooling around for a few weeks with Qubes trying to install it (not trying very hard tho) and yesterday got serious about it. I installed it on my WD 2TB MyPassport with absolutely no problems. I even did a custom install with partitions and other settings not using default. (As you can see below I do not have a powerhouse computer) Once it was installed it took a little work to get networking running and then I was done. After about a half hour I decided I was in love. The look of the GUI is awesome and while it is sort of a Linux distro (and you can see the relation here and there) it has a very unique look and feel. It is very fast, very powerful, very flexible, and I hope very secure. I cannot speak to the security robustness as I am not knowledgeable enough but I am going to do some research on how I can test that out. Even if it doesn't live up to the hype security wise I still like it so much I will keep using it. With that on my external and Windows 8 (ugh!) on my desktop I have the bases covered. Next is an install of Fortress Linux on the external next to Qubes. I am interested to see Fortress Linux in action.

Lenovo All-in-one C540
Windows 8
4 GB RAM
1 TB HDD
2 TB WD MyPassport

---

### Post by trent.josephsen on 2013-11-19
> **codell said:**
> OpenBSD security is a myth. They don't even have signed updates.

I think you do the OpenBSD team a disservice by picking on one issue like that. Package signing is good, but the lack of it makes no further statement about the quality of the software.

I have always thought that signed packages are a bit overblown, because you have to first trust the master key before you can trust any of the packages, but key distribution has the same problem as package distribution, so it's a chicken-and-egg problem. Like getting a scam e-mail and calling the phone number in it to see if it's legit.

---

