---
title: "PPC repositories"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by jmelton on 2008-12-16
After being only in OS X for a few months (no wireless in Ubuntu), I logged into Ubuntu and discovered that I wasn't able to update anything.  I'm assuming I don't have correct addresses for the PPC repositories any more.  I can't seem to find out where they might have moved to.  So, that's my question:  Where are they?  Thanks!

---

### Post by Leslie Viljoen on 2008-12-16
> **jmelton said:**
> After being only in OS X for a few months (no wireless in Ubuntu), I logged into Ubuntu and discovered that I wasn't able to update anything.  I'm assuming I don't have correct addresses for the PPC repositories any more.  I can't seem to find out where they might have moved to.  So, that's my question:  Where are they?  Thanks!

What are your servers?
Can you ping them?

---

### Post by mkvnmtr on 2008-12-16
The question might what distro are you using? I think 7.10 just lost support. I think there are still repositories for 7.04, 8.04 and of course 8.10. It might be you need to upgrade.

---

### Post by stream303 on 2008-12-16
You may have run into the change to the repos from the old mirrors to the new ports.  This might help you get back on track:

[http://ubuntuforums.org/showthread.php?t=970056&highlight=repository](http://ubuntuforums.org/showthread.php?t=970056&highlight=repository)

It threw me at first when they made the change..

---

### Post by JazzledSoul on 2009-02-08
Hi!

I've got serious problems with the repositories on my fresh install of 6.10 on my B&W G3.

My internet connection is exceptional and i'm able to install some source-packages via internet.
The problem is that almost everything is too old for anything and needs to be updated.

Anyway - **it seems like there is no update-support for PPC with 6.10 anymore**, but why would that stop me from being able to download programs like vlc from apt-get/synaptics??

Any suggestions on working repositories?

Thnx

// Jazzled

---

### Post by JazzledSoul on 2009-02-10
Is there really no one having the same problem..?
Maybe I'll try to upgrade to 7.x..

---

### Post by avtolle on 2009-02-10
The reason that Synaptic, etc., doesn't work is because the apps are looking for the repositories which have been taken down (in the case of 6.10, since April of 2008). You need to look for the old release site, which I believe is something like oldreleases.ubuntu.com (try a Google search), where the old stuff is supposedly kept.

On upgrading, 7.04 reached end of life in October, 2008; 7.10 will reach end of life in April, 2009, and the same fate will befall these repos. I'd suggest that you upgrade to 8.04, which is a LTS, good for three years, IIRC, or until April, 2011, or the current 8.10, which is a normal release with an 18 month support cycle. Good luck.

---

### Post by JazzledSoul on 2009-02-10
Thanks for the answer.

Ok, so the new updates of applications can't be runned on 6.10?
 Is it possible to run the latest debian-version of them?



I will look for that archive - but if someone's got a link to it my life would be easier ;)

The computer is almost too slow for 6.10 with Gnome, it could possibly run 7.10 with xfce, but I really doubt 8.10 even is an alternative for it.
If I would upgrade it I propably would use a disk.

---

### Post by avtolle on 2009-02-10
[https://help.ubuntu.com/community/EOLUpgrades#6.10%20to%207.04](https://help.ubuntu.com/community/EOLUpgrades#6.10%20to%207.04) 

I've looked around a bit, and there aren't any packages, etc. for 6.10 that I can find anywhere. The above link discusses an EOL upgrade from 6.10 to 7.04 (but you will run into the same issue, as 7.04 has reached its EOL; further down the linked page is a discussion of going from 7.04 to 7.10, BTW). Looks like you may need to do an upgrade.

On your other questions, I don't have an answer, but my suspicion is that the answer is "no", due to changed depedencies (newer versions required, for example), possible issues with newer kernel modules being needed, etc. Perhaps using the Debian stable distro is what you need, if updating Ubuntu is problematic; or, try other ppc distros, such as yellow dog, openSUSE as examples. Good luck with your chosen option.

---

### Post by JazzledSoul on 2009-02-10
Thanks a lot!

I've though about the other dists, but I wont neither upgrade or change dist for a while.

I'll look around for older releases of applications. Would be brilliant if I wouldn't have to ./configure make everything.

An other little question:
Suppose I'd get a list of the last working applications for 6.10 PPC - would I be able to set up an apt-mirror for other users?

---

### Post by avtolle on 2009-02-10
Yes, you could (from what I've read on the various sub-fora) but the how-to is without my limited competence. Good luck.

---

### Post by mkvnmtr on 2009-02-10
Google Ubuntu minimal install. It{s there for ppc also. Check it out and if you think you can do it it offers some good options for low resource machines. You can do it in 8.04.

---

### Post by JazzledSoul on 2009-02-10
Nice, it looks fine. 
I'm not that afraid of low memory while my father upgraded it a lot on that machine back in the days (don't remember exactly how much), I'm more concerned about the cpu-capacity.
But I guess it's all about ram when it comes to GUIs?

The though of having an up-to date system - even if it's under low-prestanda-conditions - is very tempting :P

---

