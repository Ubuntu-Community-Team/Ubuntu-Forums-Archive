---
title: "LMDE: How to apt-get &quot;Additional Drivers?&quot;"
date: 2011-05-19
forum: Any Other OS
---

### Post by Anton8604 on 2011-05-19
After messing around with Linux Mint Debian in VirtualBox I decided to switch over, but it doesn't have "Additional Drivers." Is there a way to simply download that program? Or will I have to use ndiswrapper?

---

### Post by cafejunkie on 2011-05-20
What wireless chipset? Also, in Debian you need to enable the contrib and non-free repositories in your /etc/apt/sources.list to be able to install non-free drivers.

---

### Post by krapp on 2011-05-20
Do you mean the restricted drivers GUI Ubuntu uses?

No.

To follow up on what cafejunkie said, do

```
su
gedit /etc/apt/sources.list
```

and insert "contrib non-free" (no quotation marks) after "main" in your sources, and then aptitude/apt-get away.

You can also do a search here [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) to see what drivers may be among Debian's packages. Or browse them in Synaptic after changing your sources.list and updating aptitude.

---

### Post by wolfen69 on 2011-05-20
The "additional drivers" app is called *jockey-gtk* in the repos.

---

### Post by krapp on 2011-05-20
> **wolfen69 said:**
> The "additional drivers" app is called *jockey-gtk* in the repos.

Unless I'm mistaken it's not in the Debian repos, so I don't think the OP will/should have access to it.

---

### Post by shuttleworthwannabe on 2011-05-21
this is something I wish LMDE would implement-jocky-gtk-I will switch like a flash! The response time in Debian is so much better than Ubuntu, comparable to the Fedora system. I have not idea why Ubuntu is so sluggish (almost like Windows).
 
I just discovered LMDE devs are working on something: [http://forums.linuxmint.com/viewtopic.php?f=141&t=64717](http://forums.linuxmint.com/viewtopic.php?f=141&t=64717)

---

