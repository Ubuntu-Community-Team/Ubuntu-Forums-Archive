---
title: "Old application versions in Dapper. Why?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-05
Hello.

I'm running Ubuntu Dapper and I'm planning to do it at least until Edgy+1 is out. As far as I know, Dapper is a long term support version. However, I cannot find recent versions for the programs I use, such as Firefox 2.0 or VLC 0.8.5. I also use Gaim, and I like the new beta version in Edgy, however, it is not in Dapper repositories (maybe because it's beta?!?).

Can anyone please explain me why is this happening?

Thanks.

---

### Post by dmizer on 2006-11-05
you are correct, gaim beta is not in the repos because it is beta.

the rest ... you're talking about software that's JUST been released.  after it is released, it has to be ported to debian, and then tested for compatibility with ubuntu.  so there will always be delays in the official ubuntu release of a program as compared to the official release of the code.

that said, there are lots of howto's to get what you're looking for.  just do a search for 'howto firefox 2.0' for example

---

### Post by CatKiller on 2006-11-05
> **zugu said:**
> Can anyone please explain me why is this happening?

New versions of software will not be put in the standard repositories. Updates because of security or bug fixes will be put in there, but newer versions for new features won't be.

You may be lucky and get your newer verions of the software back-ported to Dapper through the backports project.

You can still install whichever software you want independently of the repositories in any case.

---

### Post by bsussman on 2006-11-05
> **zugu said:**
> Can anyone please explain me why is this happening?

Because 6.06 is represented to be a reliable release.

The testing necessary to certify version X+1 of package Y is an unreasonable burden and would compromise efforts to put out 6.06+1, 6.06+2 and, depending on the dependencies of X+1, might expand into a certification of Y,Z,A,B etc.  

Gee - this sounds like 6.06+1 doesn't it?

So your choices are, at your own risk, to install releases untested for reliable compatability or new distributions with possible unreliabilities of their own.  Not ideal but the best they can offer.

---

