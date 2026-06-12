---
title: "Kernel upgrade borked my APM Sleep"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Orestes on 2006-08-01
Hi people!

This is my first post on the Ubuntu forums, so I apologise in advance if I offend anyone!

I have a little problem. With a recent, fresh install of Dapper from the official alternative installer CD, my IBM Thinkpad T20 slept perfectly with the kernel parameters "acpi=off apm=on". After a recent system-wide update, my t22 now freezes when attempting to sleep. ACPI never worked.

My question is this: can I revert to the kernel that I installed originally, and then lock it from updating? I tried:

```
root@Guthrie:/home/matt# apt-get install linux-image-386=2.6.25.15
Reading package lists... Done
Building dependency tree... Done
E: Version ‘2.6.15’ for ‘linux-image-386’ was not found
root@Guthrie:/home/matt#
```


and that obviously didn't work.

I'm new to Ubuntu but not to Linux; in Slackware I'd just have downloaded a kernel from kernel.org and done the old make menuconfig, make, make install but the Debian way is quite alien to me!

Thank you for your time.

PS, I googled and searched the ubuntu forums, but couldn't find anything.

---

### Post by ironfistchamp on 2006-08-01
Aren't previous kernels listed on the GRUB menu. Sorry that assumes you use GRUB. I do and it's got old ones on if I mess anything up.

---

### Post by Orestes on 2006-08-01
D'Oh! Thanks for the good hard whack with the cluestick, ironfistchamp!!! If I had another braincell I'd be a daffodil.

I'm off to try it now. :D

Edit: Works perfectly, thanks ironfistchamp! I have one more question that follows on from this (and it's in several parts):

[LIST=1]
[*]How do I remove the updated (2.6.25.26) kernel?
[*]How do I make the original kernel default in GRUB?
[*]Finally, how do I lock it so that it doesn't get upgraded anymore?
[/LIST]

Thanks for your help!

---

### Post by isharra on 2006-08-05
first linux-image is the package for 386, linux-image-686 would be the other option. :)

try looking at the settings for aptitude 'man aptitude' (I'm new to ubuntu and I prefer it to synaptic but you should be able to do the same thing using it.) I believe the following will work.

To delete the latest:
'sudo aptitude remove linux-image-2.6.15-26-386'
To stop upgrading:
'sudo aptitude hold linux-image-2.6.15-23-386'

Alternately forbid-version if you want to try out future upgrades but not use the most recent 2 versions.
'sudo aptitude forbid-version linux-image=2.6.15-25-386'
'sudo aptitude forbid-version linux-image=2.6.15-26-386'

---

