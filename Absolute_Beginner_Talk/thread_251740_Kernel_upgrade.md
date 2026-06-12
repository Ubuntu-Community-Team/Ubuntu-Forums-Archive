---
title: "Kernel upgrade"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by kidders on 2006-09-05
Does anybody know what would happen if I ran Ubuntu with a vanilla 2.6.17 kernel on a Mac? Would it work? Do Ubuntu developers typically tinker with the kernel much?

Let me know what you think!

---

### Post by nudnik on 2006-09-05
Unless you are a true expert, or absolutely determined to teach yourself computer science, the end result will likely be a very buggy and somewhat if not completely unstable system.

Many programs from the repositories would probably behave oddly. You would have to compile some of them from scratch in order to attempt a stable build. 

It takes the Ubunti (I've invented a new word to describe the collective developers of Ubuntu) months to modify such a radical upgrade to the point where it is reasonably stable. For example, as I type this they are hammering the very kernel you have in mind into a usuable piece of software for the upcoming "Edgy Eft".

The Ubuntu Mascot>> ](*,)  :mrgreen:

---

### Post by kidders on 2006-09-05
Hmm... not encouraging :-( I'm well used to kernel tinkering and all that goes with it from using Gentoo for a few years, but perhaps I shouldn't risk it.

Thanks for your reply!

---

### Post by nudnik on 2006-09-05
If you've been using Gentoo for quite a while, you might be able to eventually beat the thing into submission, but as you probably know, it is a lot of work. I'd just wait a little while until Edgy Eft is done, shouldn't be too terribly long now.

Maybe you could test Edgy and help the developers along. A test version is available for download; Edgy uses the the 2.6.17 kernel to the best of my knowledge.

---

### Post by codejunkie on 2006-09-06
the kernel is rather easy to compile in a debian based system like ubuntu. if you're used to gentoo you should have no problems compiling a new kernel in ubuntu, here's a link explaining how to compile a new kernel it will walk you through the whole process and explain how it's done on ubuntu.
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

---

### Post by kidders on 2006-09-06
Yeah, I started to realise that after I'd posted this :-)

I'd be happy to test out Edgy ... perhaps I'll do just that.
Thanks a million.

---

### Post by kidders on 2006-09-06
Hmmm... choices, choices :-) Thanks codejunkie. I'm sure I'll want to do it at some point anyhow ... I have a bit of a thing about customising my kernel ... maybe I should see a shrink about it :-P

---

### Post by codejunkie on 2006-09-06
> **kidders said:**
> Hmmm... choices, choices :-) Thanks codejunkie. I'm sure I'll want to do it at some point anyhow ... I have a bit of a thing about customising my kernel ... maybe I should see a shrink about it :-P

if the shrink helps you give me there number ;) i got a thing about kernels too, im compiling one right now stripped of all the stuff i don't need and adding a few things that the dapper kernel didn't have.

---

### Post by empcrono on 2006-09-06
maybe you guys could help me ... or point me in the right direction. I am trying to figure out how installing files work. i.e. how to specify ware they install, why they usualy install ware they install and how to genraly munipulate the install of files. thnx

---

### Post by kidders on 2006-09-06
Lol codejunkie!

And naughty, naughty empcrono ... hijacking threads is very bold! [-( 

Still, we're nice and don't mind. It seems like you're referring to installing something you've compiled from source, yeah? You'd do something like ...

```

./configure && make && make install

```

... only to realise the stuff didn't go where you wanted it to be.

Most of the time, the install location is decided during the "configure" step. I'm sure the others can say if there's a generic way of specifying install targets at that time.

Other times, the install location gets determined by an environment variable at the "make install" step. If it were me, I'd leaf through any documentation that came with the app I was compiling, just to be sure I'm not completely wrong.

The locations themselves are the way they are purely out of convention. The same rules of thumb have probably applied for decades, at a time when there would have been a very definite reason for choosing them, that perhaps doesn't apply as strongly any more.

Any help?

---

### Post by empcrono on 2006-09-06
> **kidders said:**
> Lol codejunkie!

And naughty, naughty empcrono ... hijacking threads is very bold! [-( 

Still, we're nice and don't mind. It seems like you're referring to installing something you've compiled from source, yeah? You'd do something like ...

```

./configure && make && make install

```

... only to realise the stuff didn't go where you wanted it to be.

Most of the time, the install location is decided during the "configure" step. I'm sure the others can say if there's a generic way of specifying install targets at that time.

Other times, the install location gets determined by an environment variable at the "make install" step. If it were me, I'd leaf through any documentation that came with the app I was compiling, just to be sure I'm not completely wrong.

The locations themselves are the way they are purely out of convention. The same rules of thumb have probably applied for decades, at a time when there would have been a very definite reason for choosing them, that perhaps doesn't apply as strongly any more.

Any help?


alright thanks for the help man sorry for hijacking the thread, i think i know what needs done now. lol thanks agian.

on anthor note about kernals is there a good howto on kernals on the net. i seen some good books but lack the current funds at the moment.

---

### Post by kidders on 2006-09-06
Glad that helped ... I was worried my comments might've been a bit cryptic hehe!

What do you mean by a kernel howto exactly?

If you're looking for something to tell you what each option in the kernel configurator is for, that information is (by and large) in the configurator itself.

On the other hand, if you're after something more general ... a sort of strategic discussion on kernel tweaking, maybe ... then there are hundreds. Each writer often has his own particular opinions on what is safe/smart/etc. Google is your friend :-P

In case you're interested, here are a few cardinal rules:

[LIST=1]
[*]Never tweak something you don't understand.
[*]Make small numbers of changes at a time.
[*]Keep old kernels so that, if you break something, you can "roll back". ADD entries for new kernels to your bootloader list, rather than REPLACE.
[*]**lspci** is your friend. It can tell you more or less exactly what hardware you have.
[*]Don't accidentally compile out support for your root filesystem! (Silly, but I've done it more than once!)
[*]Try to establish what Ubuntu needs you to keep turned on. Most distros have specific basic requirements, without which they cannot function.
[*]Smaller is faster ... don't build support for something you're never going to use.
[/LIST]

If I think of more, I'll post them. I hope that's of some help.

---

### Post by empcrono on 2006-09-06
> **kidders said:**
> Glad that helped ... I was worried my comments might've been a bit cryptic hehe!

What do you mean by a kernel howto exactly?

If you're looking for something to tell you what each option in the kernel configurator is for, that information is (by and large) in the configurator itself.

On the other hand, if you're after something more general ... a sort of strategic discussion on kernel tweaking, maybe ... then there are hundreds. Each writer often has his own particular opinions on what is safe/smart/etc. Google is your friend :-P

In case you're interested, here are a few cardinal rules:

[LIST=1]
[*]Never tweak something you don't understand.
[*]Make small numbers of changes at a time.
[*]Keep old kernels so that, if you break something, you can "roll back". ADD entries for new kernels to your bootloader list, rather than REPLACE.
[*]**lspci** is your friend. It can tell you more or less exactly what hardware you have.
[*]Don't accidentally compile out support for your root filesystem! (Silly, but I've done it more than once!)
[*]Try to establish what Ubuntu needs you to keep turned on. Most distros have specific basic requirements, without which they cannot function.
[*]Smaller is faster ... don't build support for something you're never going to use.
[/LIST]

If I think of more, I'll post them. I hope that's of some help.

It all helps thanks i'm gonna check out lspci and do some more google stuff. thanks

---

### Post by nudnik on 2006-09-06
Its not too difficult to compile a kernel....the trick is getting your finished product, software included, to behave as well as Dapper does at the moment. I agree it is fun, if you enjoy that sort of thing, but a truly stable system is quite an achievment. 

I shall now return to my secluded location behind the pipes :-$

---

### Post by empcrono on 2006-09-06
I do enjoy those sort of things, however its not that simple its somthing that keeps pawing at me that is both understading and the desire to have everything. that is to have my cake and eat it too. lol its that sort of thing that makes it fun. if you can see ware im going with this.

---

### Post by d_xtremw on 2007-10-06
i have a problem with my kernel though. It keeps crashing everytime i try to hibernate. i googled the problem and everyone said i shuld update my kernel. my question is, is it possible to updte my kernel without losing all my settings and programs which i installed??

---

### Post by tdrusk on 2007-10-06
> **d_xtremw said:**
> i have a problem with my kernel though. It keeps crashing everytime i try to hibernate. i googled the problem and everyone said i shuld update my kernel. my question is, is it possible to updte my kernel without losing all my settings and programs which i installed??
Yes, the easiest, but more risky version would be to upgrade to Ubuntu Gutsy.
You can do that with
```
sudo update-manager -d
```

Or use this guide to just update the kernal. The update asks a lot of questions, so it's harder.

[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernal](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernal)

---

### Post by d_xtremw on 2007-10-06
using the 


Code:

sudo update-manager -d


it gave me a window  saying that a new distribution 7.10 is out and asked me to upgrade. i was going to do this last night but i wasnt sure that it would keep all my programs and settings which i have installed now , eg beryl, desktops, azureus, and different research programs i have.  if i upgrade using this will it keep all my things??

---

### Post by shae on 2007-10-06
I personally find compiling the kernel to be no big deal.  I do not understand what you mean by getting it to a finished product.  Basically I went through and disabled what I would never use, made a few adjustments(SLUB, Tickless, CPU family, etc), patched one thing (CFS), and built it.  I have not experienced any problems with this method since moving up to the 2.6.22.x kernels.  For some reason the ones before(2.6.21.* and 2.6.20.*, 2.6.18.* worked) would cause problems with the internet that I did not feel like tracing down.

Anyways, a couple tips for you:

module-assistant is your friend if you have to build modules from source.  When you use kbuild, it will build the modules against the kernel you are building automatically and make packages for you.

When in doubt, go with default.  If you are not sure if you want a kernel option or not, select the default.  It usually works out fine.

Strip out the gunk.  There are so many drivers in the kernel that no one ever uses.  Not only does it slightly reduce the size of the packages and in some cases memory consumption, but also it reduces how long it takes to build.

Save yourself some time.  Remember to save your config file between builds and to save the makefile too.  Why the makefile?  By sticking CONCURRENCY_LEVEL="2" (If you have a dual-core processor) in the build flags I reduce my build time by 33%.  

Try to remember to give your packages a unique version name and debian revision.  This is to allow you to build multiple times from the same source if you need to (i.e. bugs fixed by tweaking options).  

Never forget sudo -s.  You need to build with sudo or at the end you cannot have privileges to build the packages.  I suppose it might work with fakeroot if you are building outside of the /usr/src/ directory.

Google is your one-stop shop for bugs.  Just select some of the bug and stick it into Google.  You can usually find others with the same problem and some with the solution.

If you have further questions or would like a copy of my config file, please ask.

---

