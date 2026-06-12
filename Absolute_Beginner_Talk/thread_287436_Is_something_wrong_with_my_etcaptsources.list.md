---
title: "Is something wrong with my /etc/apt/sources.list"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-28
Does my /etc/apt/sources.list look normal for Edgy ?


The reason I ask is because when I try to run Synaptic the data looks different in the data sent to ubuntu.


This is my sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

This is the info sent to fetch data from ubuntu

```

 http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-3ubuntu3_i386.deb
  


```

---

### Post by meng on 2006-10-28
No that sources.list looks fine and the discrepancy you're talking about is not really a discrepancy.

---

### Post by kent41 on 2006-10-28
> **meng said:**
> No that sources.list looks fine and the discrepancy you're talking about is not really a discrepancy.

Should I remove the comments # from certain lines?

---

### Post by qamelian on 2006-10-28
> **kent41 said:**
> Should I remove the comments # from certain lines?
You can uncomment several lines to get access to more software in other repositories (i.e., universe and multiverse). Basically, any line with deb or deb-src after the hash (#).

---

### Post by meng on 2006-10-28
You can if you want to expand the number of repositories you are installing from. Alternatively, you can achieve the same thing by going to Synaptic and editing the repositories using that program (enabling the universe and restricted ones).

---

### Post by kent41 on 2006-10-28
> **qamelian said:**
> You can uncomment several lines to get access to more software in other repositories (i.e., universe and multiverse). Basically, any line with deb or deb-src after the hash (#).

Thank you thats what I needed to know.

---

### Post by kent41 on 2006-10-28
I can not seem to ping  [www.us.archive.ubuntu.com](www.us.archive.ubuntu.com)   can anyone else ping

 [www.us.archive.ubuntu.com](www.us.archive.ubuntu.com) because if you can I must have a synaptic problem.

Thanks for a reply

---

### Post by PriceChild on 2006-10-28
> **kent41 said:**
> I can not seem to ping  [www.us.archive.ubuntu.com]("http://www.us.archive.ubuntu.com")   can anyone else ping

 [www.us.archive.ubuntu.com]("http://www.us.archive.ubuntu.com") because if you can I must have a synaptic problem.

Thanks for a replyI've heard they were down earlier... LOTS of people upgrading.

---

### Post by kent41 on 2006-10-28
> **PriceChild said:**
> I've heard they were down earlier... LOTS of people upgrading.

May I ask how we can find out when the servers are down?

---

