---
title: "Amarok 1.4.5 and Kaffeine 0.8.3"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by luckyjonny on 2007-02-26
I've just installed Ubuntu and I'd like to install Amarok (as I've read so many good things about it) and Kaffeine (to use with my Nebula DigiTV PCI card). But when I look in the repositories (universe, multiverse, main, restricted), they only seem to have Amarok 1.4.3 and Kaffeine 0.8.2. I'd like to use the latest versions. 

What would be the best way to get the latest versions? Is there a trustworthy repository that I could add to my sources.list to get them? And this isn't intended as a criticism, merely a curiosity, but why aren't the latest versions in the repositories?

Many thanks.

---

### Post by Maestro23 on 2007-02-26
Latest Amarok: [http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)
Install Guide: [http://amarok.kde.org/wiki/Installation_HowTo](http://amarok.kde.org/wiki/Installation_HowTo)

Kaffeine:[http://kaffeine.sourceforge.net/index.php?page=download&PHPSESSID=c00ec0792627e2250602b4dc2b930994](http://kaffeine.sourceforge.net/index.php?page=download&PHPSESSID=c00ec0792627e2250602b4dc2b930994)

Read the install instructions.  Good luck.

---

### Post by luckyjonny on 2007-02-26
Thanks for your swift reply, Maestro23. I'd actually been to both those pages and wasn't quite sure whether I was on the right track. 

I've added the Kubuntu repository for Amarok and that's now installed :) I guess for Kaffeine 0.8.3 I should download the source and compile it? I've read a little about compiling ... but I'm a little nervous about missing dependencies?

---

### Post by nickoli_02 on 2007-02-26
Latest versions of software can take awhile to get added to the official repositories because someone actually has to take the time to create the .deb package and send it in... To be honest I don't know the specific process of adding packages to the repos, but the process takes some time.

---

### Post by Maestro23 on 2007-02-26
> **luckyjonny said:**
> Thanks for your swift reply, Maestro23. I'd actually been to both those pages and wasn't quite sure whether I was on the right track. 

I've added the Kubuntu repository for Amarok and that's now installed :) I guess for Kaffeine 0.8.3 I should download the source and compile it? I've read a little about compiling ... but I'm a little nervous about missing dependencies?

No prob man.  Compiling programs from source is not recommended for someone new to linux.  You can really hose things up if you are not careful.  If it's not killing you, just stay with the current version of Kaffein from the Repositories.  Then when you feel more at ease with command line and compiling, try your hand a the source file.

---

### Post by luckyjonny on 2007-02-27
Heh. Yeah, I did have a quick go at compiling Kaffeine 0.8.3 and was getting that "hosing things up" feeling. It needed X libs, so I installed those from Synaptic, then it wanted Qt ... but I thought I'd stop there :D

Yes, it must be a big job keeping all the programs in the repositories up to date, nickoli_02.

---

### Post by Darko Beta on 2007-02-27
I have Amarok 1.4.3, and I've been wondering about how to upgrade to 1.4.5.  If I add the Kubuntu repository, will I be able to simply upgrade?  Or will I have to re-install?

---

### Post by Marsolin on 2007-02-27
One way is to request a backport [here]("https://launchpad.net/ubp") and see if someone will add it to the edgy-backports repository.

---

