---
title: "portage + port hole"
date: 2011-05-28
forum: Any Other OS
---

### Post by boblizar on 2011-05-28
ok im going to attempt to install portage and port hole to ubuntu :popcorn:
[http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=5](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=5)

and just attach it to ubuntu after having ubuntu build up the terminal / compiler.

this is only for fun because i have an idea it can be done :popcorn:

```
tar xvjf /mnt/gentoo/portage-latest.tar.bz2 -C /usr
```

looks like im going to have to go further back than this and setup the make variables.  i see rpm in the apt repositories, why isnt portage there?

---

### Post by kk0sse54 on 2011-05-29
I don't think this is going to work the way you think it will....

[http://ubuntuforums.org/showthread.php?t=386973](http://ubuntuforums.org/showthread.php?t=386973)

I think there was a bit of discussion a while ago about porting portage to ubuntu but I doubt anything ever came out of it since there really is no point in doing so. Furthermore portage isn't in the ubuntu repositories because you can't simply  install it through a .deb package.

If you're still dead set on doing something that's probably close to impossible (at least in a pratical sense) you'll want to follow this guide on [**prefixed portage**]("http://www.gentoo.org/proj/en/gentoo-alt/prefix/")

[http://www.gentoo.org/proj/hen/gentoo-alt/prefix/bootstrap-solaris.xml](http://www.gentoo.org/proj/hen/gentoo-alt/prefix/bootstrap-solaris.xml)

---

