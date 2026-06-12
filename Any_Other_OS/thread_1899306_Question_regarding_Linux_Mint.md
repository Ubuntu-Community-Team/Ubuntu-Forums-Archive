---
title: "Question regarding Linux Mint"
date: 2011-12-23
forum: Any Other OS
---

### Post by linuxuser12345 on 2011-12-23
Is Linux Mint Debian Edition a rolling release?

---

### Post by Elfy on 2011-12-23
Thread moved to Other OS/Distro Talk.

---

### Post by d2btoo on 2011-12-23
yes :)
(Linux Mint Debian Edition (LMDE) is a rolling distribution based on Debian Testing.)
more info [http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)

---

### Post by TBABill on 2011-12-23
Only one edition of Mint is rolling (LMDE, as mentioned above). The others are Ubuntu based. 
 
LMDE is not "rolling" in the same sense something like Arch or Sabayon or PCLinuxOS are. Those receive regular, frequent updates, sometimes at a high rate. LMDE has now moved to its own repositories where updates from Debian are tested to help ensure they don't break the system, then made available to users on a monthly basis. By doing so, you still get all the updates from Debian Testing, but at a much slower pace and sometimes updates are withheld until stability can be obtained.
 
In addition to the method used, Debian Testing will go into a freeze where it is prepared to be released as stable. During that time there will be little change to the system compared to when it is outside that freeze. Once those packages are accepted as stable and Testing is released as stable, the unstable repository (called sid) is dumped into testing and the process begins again as they work toward the next stable release.
 
I just wanted to point all that out because Debian uses testing to prepare for release where others use their rolling release method as the primary distro. Testing is not really meant as a primary distro, although it obviously works pretty well for that. Sid does as well for some, both in Debian and aptosid and others.

---

### Post by linuxuser12345 on 2011-12-23
Should Linux Mint Debian Edition be considered a "stable" environment, or would you not recommend it for everyday and business users?

---

### Post by jjex22 on 2011-12-23
> **linuxuser12345 said:**
> Should Linux Mint Debian Edition be considered a "stable" environment, or would you not recommend it for everyday and business users?

This really depends on your definition - if you went with the debian definition then no - it's based on the testing barnch. Linux mint would maintain that it is a stable OS - as TBAbill says the packages from debian testing are... well tested before being released to the masses.

In my experience it is not as stable as 11, but is more stable than 12, the trade off is packages - there's still a lot to get through the testing process and become available... I'd therefore not recommend it for business users just yet, In debian terms, it's probably best to think of it as a technology preview like gnu/kfreebsd - most of the important packages are ported and stable but there's still quite a bit to do.

For business use, if you want a debian based system - debian squeeze, if you want a mint one - isodora lts... or katya if you want later packages would be my recommendations.

for home desktop you really can use any of them, ubuntu based distos will always have the scope to be more user friendly than debian as this is what ubuntu aims for, but then debian does have a more traditional, stable approach, and the relatively slow expansion of packages for lxde suggests that mint intend to keep it this way.

---

### Post by TBABill on 2011-12-23
I wouldn't risk my business to anything less than rock solid stability...Debian 6, Ubuntu 10.04, CentOS, Scientific Linux...something extremely solid that is NOT "up to date". New means less stable. Nothing new is perfect and business cannot afford to be test beds or risk interruption. Well tested and stable software only get that way with age and widespread use. Rolling distros are probably the worst idea I can imagine for business use by the very nature of the frequent package changes.

---

### Post by bluexrider on 2011-12-23
> **linuxuser12345 said:**
> Is Linux Mint Debian Edition a rolling release?

There some other things:

**How does LMDE compare to the Ubuntu-based editions?**

              Pros:
     
[LIST]
[*]             You don't need to ever re-install the system. New versions of software and updates are continuously brought to you.
[*]             It's faster and more responsive than Ubuntu-based editions.
[/LIST]
              Cons:
     
[LIST]
[*]             Although it's using Romeo for unstable packages, LMDE continuously  changes as it receives updates and new software. Compared to a frozen  version of Linux Mint which changes very little once it's publicly  released, it's not as stable. Things are likely to break more often but  fixes can also come quicker. For this reason, LMDE requires a deeper  knowledge and experience with Linux, dpkg and APT.
[*]             Debian is a less user-friendly/desktop-ready base than Ubuntu. Expect some rough edges.
[/LIST]
     



**[B]Known problems in Linux Mint Debian**[/B]

[http://www.linuxmint.com/rel_debian.php](http://www.linuxmint.com/rel_debian.php)

---

### Post by snowpine on 2011-12-23
> **linuxuser12345 said:**
> Is Linux Mint Debian Edition a rolling release?

It is marketed that way, but in my opinion you could do better (Arch etc) if you are in the small minority of users who truly need a rolling release distro.

---

### Post by d2btoo on 2011-12-24
> **TBABill said:**
> I wouldn't risk my business to anything less than rock solid stability...Debian 6, Ubuntu 10.04, CentOS, Scientific Linux...something extremely solid that is NOT "up to date". New means less stable. Nothing new is perfect and business cannot afford to be test beds or risk interruption. Well tested and stable software only get that way with age and widespread use. Rolling distros are probably the worst idea I can imagine for business use by the very nature of the frequent package changes.

Ditto

---

