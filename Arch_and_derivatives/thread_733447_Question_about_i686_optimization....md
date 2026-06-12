---
title: "Question about i686 optimization..."
date: 2008-03-23
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-03-23
Is only the Arch kernel optimized for i686, or is everything in the repos i686? But how could that be so with the proprietary apps? 

And, in terms of my processor, what does it really mean to be i386 or i686 optimized? I know that PII and newer are i686, but what does that mean in terms of cycles and data and calculations?

---

### Post by MisfitI38 on 2008-03-23
> **EmosSuck777 said:**
> Is only the Arch kernel optimized for i686, or is everything in the repos i686? But how could that be so with the proprietary apps? 

And, in terms of my processor, what does it really mean to be i386 or i686 optimized? I know that PII and newer are i686, but what does that mean in terms of cycles and data and calculations?

All Arch packages, including kernels are built for i686 or x86-64. 

i686 includes newer instruction sets with some performance advantages.
The difference between an i386 and i686 package is small, performance-wise; typically not humanly perceivable. The trick is, though, that when an entire distribution is compiled for i686 all of the packages have that small increase and it can (not necessarily, but usually) make a perceivable difference. 
One of the main reasons that distros like Slackware, Arch and CRUX are touted as "fast" is because they are inherently *light and simple*. Everything from system conf files, (which are sourced, and therefore, must be read) to init and daemon scripts are kept very simple and minimal with little or no redundancy. This keeps resource demands lower and results in improved responsiveness.
These systems are independently developed, and not based on other systems, so there is no added "bloat" attached to an already functioning base distro. Bloat can be anything from added scripts for hardware autodetection, to unnecessary daemons running in the background.
Of course, you could theoretically, strip virtually any distro down to its barebones, and rebuild with i686 optimizations, and get similar results, but that would be an amazingly time consuming and unrewarding process. ;)

---

### Post by deepclutch on 2008-03-24
well,how can we build say,optimized for prescott pentium processor etc?I know some CFLAG are used .do explain if you know stepbystep.

actually would like to rebuild whole arch system optimized for prescott;that's why :D thanks!

---

### Post by fwojciec on 2008-03-24
> **deepclutch said:**
> well,how can we build say,optimized for prescott pentium processor etc?I know some CFLAG are used .do explain if you know stepbystep.

actually would like to rebuild whole arch system optimized for prescott;that's why :D thanks!

You can set compiler flags by editing /etc/makepkg.conf -- to have packages built with optimizations for your particular system you could change them like this, for example:
> #CFLAGS="-march=i686 -mtune=generic -O2 -pipe"
#CXXFLAGS="-march=i686 -mtune=generic -O2 -pipe"
CFLAGS="-march=native -O2 -pipe"
CXXFLAGS="-march=native -O2 -pipe"
You can also have a look at [this wiki page]("http://wiki.archlinux.org/index.php/Safe_Cflags").

As for your project with rebuilding the whole system with prescott optimizations -- this would certainly be educational but wouldn't improve the system speed in any noticeable way, unless you respond well to placebo effects :P

If you want to have a system optimized for your particular machine I suggest using a source distro like Gentoo or Crux -- source distros are designed to be used this way, Arch isn't.

---

### Post by Pogeymanz on 2008-03-24
So, take Opera web browser for example:

Is that package also optimized for i686? How is that possible without the source code? Did the Arch devs ask Opera nicely to make a 686 optimized package?

---

### Post by jdhore on 2008-03-24
> **EmosSuck777 said:**
> So, take Opera web browser for example:

Is that package also optimized for i686? How is that possible without the source code? Did the Arch devs ask Opera nicely to make a 686 optimized package?

I believe the packages that don't offer the source are just optimized however upstream optimizes them...but really, out of all the thousands of packages, i can really only think of like 5 things that would fit into that category: Skype, Opera, Adobe Flash, Sun Java and W32Codecs

---

