---
title: "No internet connection via FF?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-19
Hi everyone,
It's been about 36 hours I can't use FF. I've tried evrything I know how but no go and I didn't fiddle with it. This didn't happen following updates or anything.
Konqueror works fine...even faster but I like FF.
Thank you for any help you may post.

---

### Post by Brunellus on 2006-09-19
Disable ipv6 routing according to [ these instructions ](http://www.ubuntuforums.org/showthread.php?t=202838) and also [within firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox) (note that even though the last link is for SuSE, it's not distro or version-specific)

---

### Post by xyz on 2006-09-19
Thanks Brunellus!
I had already disabled (set to true) IPV6 in FF and... permanently.
> # 1, 2, 3 new lines
alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here. 
alias ipv6 off  --
#alias net-pf-10 ipv6
rebooted and all!
Am I missing something else?

---

### Post by xyz on 2006-09-19
Would the only way to get FF back on its FFeet to restore my entire system which I have got backed up safely a few days ago?
THX. I hope not!!

---

### Post by xyz on 2006-09-21
Well I'm sure glad I had a 'rocking' backup of my system. Restoring put everything back in good order and I just could not figure why FF was screwed up nor how to fix it.
Thanks for paying attention to my problem, though.  :D

---

