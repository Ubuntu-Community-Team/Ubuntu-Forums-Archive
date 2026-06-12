---
title: "Update Manager - software &quot;can't be authenticated&quot;"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by VraiChevalier on 2007-02-03
I ran Update Manager a few hours ago and received a warning that the "software can't be authenticated".  (screenshot attached)

So I did **_not[U][B]**_[/U][/B] install it! I then searched the forums for any threads relating to this. Found some indicating there may be a problem with Feisty. I am running Dapper 6.06 alt.

Based on what I found I tried sudo apt-get update (I think) which also returned an error message. Then I tried sudo aptitude upgrade which seemed to have worked. 

My questions are: Is there a problem with the Update Manager and/or repositories? And, will sudo aptitude upgrade update the same software as the Update Manager?

---

### Post by hmLyons on 2007-02-03
What this sounds like to me is that you may have added some repositories without adding the corresponding authentication key. If this is the case that's okay, everything will still work fine. You are just foregoing an extra level of security.

As an example have a look at the [Automatix2 install instructions]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29"). Notice the 3 lines in the middle. These steps are adding the gpg key to your system so that you can have that extra level of security to know that no one has tampered with the software you are about to install.

I don't understand very well myself how this all works but if you're interested I think [this page]("http://wiki.debian.org/SecureApt") and also [this page]("http://www.debian-administration.org/articles/174") talk more about the technical details.

---

### Post by xp_newbie on 2007-02-04
> **hmLyons said:**
> What this sounds like to me is that you may have added some repositories without adding the corresponding authentication key. If this is the case that's okay, everything will still work fine. You are just foregoing an extra level of security.

No, I don't think this is the case, since I just encountered the same warning (problem?) and I know for sure that I never added any repository without adding the corresponding authentication key. In fact, in addition to the original "Officially supported" I only have "restricted copyright" checked (a reposity that already came with Dapper (6.06 LTS) out-of-the-box.

BTW, the package updates that are marked as "not authenticated" are libc6-dev, libc6, libc6-i686, app-install-data-commercial, 4 libgtk2.0  packages and synaptic.

This is seems to me like a bug, or a mishap.

I am curious to know what others think of this problem.

I am not authorizing the update until I am convinced that they are benign.

Regards,
Alex

---

