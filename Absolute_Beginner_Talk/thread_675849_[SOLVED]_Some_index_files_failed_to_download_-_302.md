---
title: "[SOLVED] Some index files failed to download - 302 redirect"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by OffHand on 2008-01-23
Hi Guys,

I have just installed 7.10 server but when I try to update I get the following error:

A lot of: Failed to fetch <url here> 302 Redirect [IP: ip here]

Last message:

E: Some index files failed to download, they have been ignored, or old ones used instead.

I could really use some help solving this issue.

Thanks in advance,
OffHand

---

### Post by mikeyphi on 2008-01-23
Looks as though either the repos were down at the time or your list has errors.
Could you post the contents of /etc/apt/sources.list

---

### Post by OffHand on 2008-01-23
> **mikeyphi said:**
> Looks as though either the repos were down at the time or your list has errors.
Could you post the contents of /etc/apt/sources.list

I can't show it unless I type every single entry by hand as it is a server install without a webbrowser.

The ones that are uncommented though are:

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe

---

### Post by mikeyphi on 2008-01-23
OK!!
These are mine - from a Desktop install:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe

As you know - only the uncommented ones get used but I would have thought you needed more than 2 .... however your 2 look OK - so perhaps it was an Internet problem at the time? Or are you still seeing the same problem?....Perhaps try another server (instead of the nl one?)

---

### Post by OffHand on 2008-01-23
I think it's not the entries in the sources list but the firewall we use. wget gave me some feedback that the firewall might be interfering with the updates. I'll report back when I find more information.

---

### Post by OffHand on 2008-01-23
It indeed was the firewall doing a redirect. apt-get does not like being redirected.

---

