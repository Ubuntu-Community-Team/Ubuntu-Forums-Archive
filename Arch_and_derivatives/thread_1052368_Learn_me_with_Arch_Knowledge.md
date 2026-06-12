---
title: "Learn me with Arch Knowledge"
date: 2009-01-27
forum: Arch and derivatives
---

### Post by Mason Whitaker on 2009-01-27
Anyone mind explaining to me what Arch is all about, and its advantages over other Linux Distros?

---

### Post by smartboyathome on 2009-01-27
> **Mason Whitaker said:**
> Anyone mind explaining to me what Arch is all about, and its advantages over other Linux Distros?

Arch is all about you making your system how you want. It tries to keep the system simple by providing a minimal base and the tools to build it up, but thats it. What keeps me on Arch is makepkg and its power to build pkgs using simple build scripts.

---

### Post by raul_ on 2009-01-27
[http://www.archlinux.org/about/]("http://www.archlinux.org/about/")

I will never go back to a distro that is not rolling release

---

### Post by Mason Whitaker on 2009-01-27
> **raul_ said:**
> [http://www.archlinux.org/about/]("http://www.archlinux.org/about/")

I will never go back to a distro that is not rolling releaseI don't really trust descriptions given by groups themselves, they are always glorifying XD;

I'd rather like to see a third party's perspective on them.

---

### Post by cardinals_fan on 2009-01-27
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)
[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

The Arch Way is an essential read, and the lower link is a handy and objective comparison.

---

### Post by crimesaucer on 2009-01-27
> **Mason Whitaker said:**
> Anyone mind explaining to me what Arch is all about, and its advantages over other Linux Distros?

I think Arch is more about "learning Arch" yourself..... with the well written ArchWiki pages and the easy to configure system..... and the way you install with the console and nano/vi for editing your important configuration files.


After that it's all about paying attention to the updates and maintenance for any new bugs...... be sure to pay attention to the .pacnew files in the /etc directory or any new changes that they make...... usually they post the important stuff on the home page, and the less important stuff will be written in the terminal as a note after upgrading packages.

---

### Post by K.Mandla on 2009-01-27
> **Mason Whitaker said:**
> I'd rather like to see a third party's perspective on them.
I think Arch is a natural step for anyone who learns about Linux (not necessarily Ubuntu, but it seems to happen that way), wants to improve performance and isn't afraid of the command line. That last part might be the most important.

Arch reverses the standard that Ubuntu uses to introduce people to Linux: It starts at nothing and you build up. It forces you to learn a little more about the insides of your machine, but the payoff is a system that is lighter and cleaner than what Ubuntu does by default.

It's not for everybody and not everybody *should* like it, or even try it. If you're comfortable with Ubuntu and having everything done for you, then Arch won't be fun. On the other hand, if you would like to take control (and responsibility), Arch is an improvement over a prepackaged system.

Is that a fair answer? :)

---

### Post by cardinals_fan on 2009-01-27
> **K.Mandla said:**
> I think Arch is a natural step for anyone who learns about Linux (not necessarily Ubuntu, but it seems to happen that way), wants to improve performance and isn't afraid of the command line. That last part might be the most important.

I would replace the last component with "and is willing to learn about the complexities of their system".  Arch requires very little CLI *knowledge*.  It does require a willingness to *acquire* CLI knowledge :)

---

### Post by Mason Whitaker on 2009-01-27
> **K.Mandla said:**
> Is that a fair answer? :)Why yes it is :)

---

### Post by kerry_s on 2009-01-27
simply put: arch is linux your way.
arch gives you the power to have the linux you want, you build it, pick what you want, set it up your way.
in arch everyones install is custom, nobody has the same as any 1 else. ;)

every one do one pick of your arch.

---

### Post by chucky chuckaluck on 2009-01-27
for me, it was just a way of only installing what i wanted. i hate extra crap, but i don't know enough to be able to start with ubuntu and get rid of everything i don't need. even though i'd tried the ubuntu minimal installation, i was still lured by the speed of arch and the option to use other filing systems (readily). oddly, i think it's pretty good for an end user who just needs access to to a few common, simple apps.

---

### Post by smartboyathome on 2009-01-27
> **kerry_s said:**
> simply put: arch is linux your way.
arch gives you the power to have the linux you want, you build it, pick what you want, set it up your way.
in arch everyones install is custom, nobody has the same as any 1 else. ;)

every one do one pick of your arch.

There is a screenshot thread in this forum for your enjoyment. ;)

---

### Post by cardinals_fan on 2009-01-27
> **chucky chuckaluck said:**
> for me, it was just a way of only installing what i wanted. i hate extra crap, but i don't know enough to be able to start with ubuntu and get rid of everything i don't need. even though i'd tried the ubuntu minimal installation, i was still lured by the speed of arch and the option to use other filing systems (readily). oddly, i think it's pretty good for an end user who just needs access to to a few common, simple apps.
I have to give Arch credit for that.  Far too many systems nowadays don't support JFS :x

I can deal with an EXT3 /, but I need to be able to mount my JFS data partition.

---

### Post by handy on 2009-01-28
I have found that once Arch is set up how I like it, it really requires very little maintenance; you upgrade with -Syu --aur, & occasionally find that there is a .conf.pacnew file to have a look at to see if it contains anything useful, or if you can just delete it as usual.

Twice in 9 months I've upgraded into trouble, the first time taught me how to get out of it easily & quickly:

*_[http://ubuntuforums.org/showpost.php?p=6283883&postcount=3](http://ubuntuforums.org/showpost.php?p=6283883&postcount=3)_*

The 2nd time came down to easily finding the solution for the problem that many of us had with the X.org update, on the Arch Wiki.

Both of those problems came from upstream.  It is a something to expect from time to time when you live on the cutting edge. 

Once set up to my liking, I think Arch/Xfce is probably the laziest OS I've ever used, next to OSX.  Though it is the opposite to OSX in so many ways, which I know I really don't have to go into. :-)

Here are some links that can be useful for new Archers:

*_[http://bbs.archlinux.org/viewtopic.php?id=56373](http://bbs.archlinux.org/viewtopic.php?id=56373)_*

There is too much info' here on handling .pacnew files, but it surely makes it easier to make an informed decision:

*_[http://ubuntuforums.org/showthread.php?t=881270&highlight=.pacnew](http://ubuntuforums.org/showthread.php?t=881270&highlight=.pacnew)_*

---

### Post by kerry_s on 2009-01-28
> **smartboyathome said:**
> There is a screenshot thread in this forum for your enjoyment. ;)

alright. i'm getting it ready to go back to my niece anyways.

---

