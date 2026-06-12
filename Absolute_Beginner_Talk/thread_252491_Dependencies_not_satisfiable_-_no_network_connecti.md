---
title: "Dependencies not satisfiable - no network connection."
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Kuma_Pageworks on 2006-09-06
Hi there.  I posted yesterday about my problems getting ethernet installed.  It turns out that the card was dead, dead, dead.  So now I'm back to trying to get the wireless to work.

I have a card that requires ndiswrapper.  In order to install ndiswrapper, I need to install the build-essential packages and the make package.  In order to do that ... 

You get the idea.  At the point I'm at, build-essential depends on libc6, which in turn depens on linux-kernel-headers, which despite the fact that I've downloaded every single linux-kernel-header-*-i386 in the repository (manually, mind you, walking a writeable CD back and forth to the machine), it's telling me that linux-kernel-headers is unsatisfiable, and therefore everything up the chain won't install.

So now what?  I have no way to connect to the repositories, so I have no way to fix my problem, which demands that I connect to the repositories.

So what's the solution if 'use Synaptic' is out?

---

### Post by Kuma_Pageworks on 2006-09-07
*sigh*

It should really give you the option of installing all of this stuff during the Ubuntu install.  All of these things are in the CD repository, fer chrissakes.

---

### Post by bluefrog on 2006-09-07
ndiswrapper is part of the cdrom so no nedd to build it...

James

---

### Post by benfindlay on 2006-09-07
You should be able to use your setup cd as a repository; boot up with it in, and it should show up as a repository option in Synaptic, just tick the box to enalbe it, then click reload in synaptic.

Stuff like ndiswrapper is on the cd, so you shouldn't have any problems from then on!

Hope this helps!

---

