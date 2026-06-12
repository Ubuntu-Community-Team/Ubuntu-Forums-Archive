---
title: "firefox 2.0 for ubuntu?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-10-24
Hi, I was just wondering if there was a way one can download firefox 2.0 for ubuntu through the respositories? Thanks

---

### Post by Donshyoku on 2006-10-24
If you update to Edgy Eft (final release in a few days... it is running problem-free for me), you will have the final release of FF2.0.

If you are interested in this, post back and we can help you upgrade to the new version of Ubuntu really easily.

---

### Post by aysiu on 2006-10-24
Upgrade to Edgy on Thursday.

---

### Post by ewl1217 on 2006-10-24
Firefox 2.0 RC3 was available in Edgy Eft (the next version of Ubuntu, due out this week; the version of it I tried was a testing release) last time I checked. It should be update to the final 2.0 release by now or soon, but only in Edgy. Dapper Drake (the current version of Ubuntu) will probably stick with Firefox 1.5. Unless you need the long-term support (3 years of security updates) provided by Dapper, then you can just wait it out until Edgy comes out. There should be upgrade instructions from Dapper to Edgy when the final release is made. If you're sticking with Dapper, then you're stuck with Firefox 1.5 for the forseeable future unless you install Firefox 2.0 manually.

---

### Post by aysiu on 2006-10-25
If you don't like waiting for Ubuntu's Firefox to update, take a look at this thread: [HowTo: A script to install the latest Firefox](http://ubuntuforums.org/showthread.php?t=151179)

---

### Post by deadgobby on 2006-10-25
I thought it was Friday...MMM I am going to wait to see if any one had any problems yet. I just wounder if I have to reinstall codecs.
Gobby

---

### Post by cptjaben on 2006-10-25
OOO I forgot about Edgy's release this week, I'll just wait. Thanks for the info everyone.

---

### Post by japurcell on 2006-10-25
Is there a swiftfox 2.0 coming too?

---

### Post by japurcell on 2006-10-25
Nevermind.  There is :-).  Get it [here]("http://www.getswiftfox.com/releases.htm").

---

### Post by ronmarley1 on 2006-10-25
> **aysiu said:**
> If you don't like waiting for Ubuntu's Firefox to update, take a look at this thread: [HowTo: A script to install the latest Firefox](http://ubuntuforums.org/showthread.php?t=151179)
Thanks for the pointer.  However, the script got held up downloading the key and bagged out before Firefox got installed.

---

### Post by TitusDalwards on 2006-10-25
> **aysiu said:**
> If you don't like waiting for Ubuntu's Firefox to update, take a look at this thread: [HowTo: A script to install the latest Firefox](http://ubuntuforums.org/showthread.php?t=151179)

i have just tried it and now i'am using firefox2.0 non-problem. Thanks lot.

---

### Post by ronmarley1 on 2006-10-25
> **ronmarley1 said:**
> Thanks for the pointer.  However, the script got held up downloading the key and bagged out before Firefox got installed.
Here's the error I got:

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.

---

### Post by ronmarley1 on 2006-10-26
> **ronmarley1 said:**
> Here's the error I got:

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.
I found another post that had me chmod something and the script worked just fine.  If I find the post, I'll link to it.
<EDIT> Here's the fix:
```
chmod ~/.gnupg/gpg.conf
```
I ran this before running the script and then everything works great.  Thanks!

---

