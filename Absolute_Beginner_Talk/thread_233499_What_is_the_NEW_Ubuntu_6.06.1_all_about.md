---
title: "What is the NEW Ubuntu 6.06.1 all about?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by elijahclarity on 2006-08-10
I was taken aback when I went to Distrowatch today and saw a DISTRIBUTION RELEASE of Ubuntu!!! For a split-second I thought its Edgy Eft...but SO SOON!!! I put myself together and then saw that it was some sort of "maintenance release".

What is the NEW Ubuntu 6.06.1 all about?

I read that it comes with plenty of security updates & bugfixes....but does it ALSO include package upgrades?

Does the new Kubuntu 6.06.1 come with KDE 3.5.4??

And are we going to see more such kind of "distribution releases"? Like 6.06.2 and then 6.06.3 etc.?? Will we keep seeing such "maintenance releases"? If yes then thats great!

I dont have an internet connection at home but my institute where I study has a fast internet connection from where I can download this NEW Ubuntu/Kubuntu and install it to my PC:p  I now have a 1 GB USB pendrive so I can carry ISOs back home easily!

Plz pardon me if my questions sound silly:(

---

### Post by steve.horsley on 2006-08-10
There's no mention of it that I can find on their web site. But I guess it's just a roll-up of all the updates that we have seen so far. That will reduce the number of updates people have to do immediately after an install. I don't think you will see anything other than the online updates in there.

---

### Post by Klaidas on 2006-08-10
> **steve.horsley said:**
> There's no mention of it that I can find on their web site. But I guess it's just a roll-up of all the updates that we have seen so far. That will reduce the number of updates people have to do immediately after an install. I don't think you will see anything other than the online updates in there.

That is true. Here's an extract from e-mail I have received:

> Over 300 post-release updates have been pre-applied, so that fewer
updates will need to be downloaded after installation, and a number of
bugs in the installation system have been corrected.  These include
security updates and corrections for other high-impact bugs, with a
focus on maintaining stability and compatibility with Ubuntu 6.06 LTS.
We do not expect that certifications against Ubuntu 6.06 LTS will need
to be updated for this maintenance release.

---

### Post by arjun.shankar on 2006-08-10
Thanks for the news. I'm getting the isos right now!
Need to hand them out to people in college... :)

---

### Post by davebgimp on 2006-08-10
All this is is new install packages with all the bug and security fixes applied since the release. If you've been updating your Ubuntu regularly, you don't need to do anything. This release just makes it easier for people doing new installs, taking a lot of the weight off that initial update after a fresh install.

---

### Post by 23meg on 2006-08-10
Another way to think of it for those more accustomed to the Windows model is: it's like a version of Windows that starts to ship with the service pack preinstalled some months after its release. It's still the same version, but with the fixes up to a certain point after its release preapplied.

---

### Post by Jucato on 2006-08-10
Guys, before you all go scrambling to get the new ISO's, check first your system. In a terminal, type in

```
lsb_release -a
```

If you have been faithfully upgrading your system the past weeks, chances are, you're already using 6.06.1.

So what is Ubuntu 6.06.1 LTS? It's what they called a "point" (.) release, a sort of maintenance release. Remember that Dapper is LTS (Long Term Support) and will be supported for 5 years (IIRC). So they need to have these releases in order to organize the support and upgrade of Dapper. This is specially useful for those just coming into Ubuntu right now and don't want to spend most of their time upgrading.

[https://wiki.ubuntu.com/DapperPointReleaseProcess](https://wiki.ubuntu.com/DapperPointReleaseProcess)

---

### Post by Drakkor on 2006-08-10
You're absolutely right, Fenyx Cheers ! :D 

drakkor@drakkor:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper
drakkor@drakkor:~$

---

