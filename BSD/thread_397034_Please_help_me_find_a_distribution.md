---
title: "Please help me find a distribution"
date: 2007-03-30
forum: BSD
---

### Post by zugu on 2007-03-30
Hello everyone!

I'm looking for an operating system where software is handled in a similar-to-PC-BSD fashion: self contaied libraries for every application. IMHO, this is the only correct approach to software management, and every OS should be built that way.

I'll try any *NIX that satisfies this only condition.

So, is there anything else out there with such software management, excluding PC-BSD? Other BSD? Linux? Solaris? Unix?

Cheers.

---

### Post by Jussi Kukkonen on 2007-03-30
Mac OS? Can't think of any others, and I believe the reason is that pretty much every 
*nix developer just disagrees with your opinion on package management...

---

### Post by mips on 2007-03-30
Windows ?

---

### Post by zugu on 2007-03-30
Thanks for the replies. 

I still fail to see why my opinion is a big no-no in the *NIX community. 

Redundancy can be reduced through optimization to something we can all live with. HDD space is not a luxury anymore, and application developers should not only patch their creations, but also the libraries distributed with their programs, using the latest upstream security fixes.

This means a little bit more work in development, but think about how much testing time would be cut. This would increase the number of responsible maintainers and would eliminate dependency hell once and for all!

An apt-get ecosystem stability relies mostly on the assumption that the user is going to install software from the official repository only. Install anything else and you risk bringing the whole OS to its knees. 

Having non-shared dependencies allows the user to install anything, without worrying something might go wrong. Commercial software is using this approach. Have you seen how simple it is to install Skype or Picasa or neroLINUX on Ubuntu? One package and that's it. Look at Crossover Office: you can create a unique Windows-like universe, a"bottle", for every Windows application you install. NO CONFLICTS AT ALL.

This is, IMO, the next step towards applying the "Just Works" badge to any Linux distribution. Please tell me what's wrong with my judgment.

---

### Post by mephisto786 on 2007-03-30
The closest Ive encountered to what you describe, before using PC BSD, are the slax based distros.......originating from the live slax (slackware based) distro, which allows you to download modules and drop them in your modules folder.  However, I'm not sure how that would work when using these live projects in a  full hard disk install...which most provide as an option. Then i believe they rely on slapt-get and the like.   Look into slax based options like slax, mutagenix, and  backtrack (pen test tool distro) .

Anything wrong with PC BSD?  Freespire and Xandros tend to have variant of one click pkg mangement as well.....

cheers

---

### Post by Jussi Kukkonen on 2007-03-30
> **zugu said:**
> 
This is, IMO, the next step towards applying the "Just Works" badge to any Linux distribution. Please tell me what's wrong with my judgment.

The security part most importantly. You say that application developers should patch all libraries they use...That is a gigantic **should**. It creates problems that grow exponentially with the size of the application universe: It doesn't matter if 99% of the software gets fixed in time. You just need one developer to miss a security bulletin or misjudge the threat a vulnerability poses, one program that is not maintained with the care it should be maintained. If one of those hundreds of links fails, your security is, at least theoretically, toast.

Another point is constant development -- application developers would like to use old versions of libraries, they're not interested in porting their code to the next version. It's understandable, but in the long run it just hurts the community: lot's of different versions in use, new versions do not get the user base they need. library development isn't focused on one version.

I'm not saying it can't work. I'd like to see it done in a Debian-scale before I'm convinced though.

---

### Post by Rounin on 2007-04-18
GoboLinux?

---

### Post by Extreme Coder on 2007-04-20
So I'm not alone thinking the way you think too Zugu. I will watch this thread then :)

---

### Post by Thulemanden on 2007-04-22
Isn't it obvious to to mention Linspire and Freespire?

Besides most Linux is one click via selection in package manager.

You'll have to look pretty far to find a command line only application installation interface.

BTW what's wrong in PC-BSD since you aren't satisfied with it? I was very happy with it, if it not were for the fact that dual boot installation is a pain if at all possible for non geeks.  :lolflag:

---

### Post by mips on 2007-04-23
> **Thulemanden said:**
>  I was very happy with it, if it not were for the fact that dual boot installation is a pain if at all possible for non geeks. 

Whats so hard about dual booting it ? I had it triple booting on my laptop with GAG. Grub would probably have worked as well seeing it works for openbsd.

---

### Post by Pobega on 2007-04-23
> **Thulemanden said:**
> You'll have to look pretty far to find a command line only application installation interface.

aptitude/dselect?

---

