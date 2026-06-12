---
title: "LTS Question"
date: 2008-12-08
forum: Apple Hardware Users
---

### Post by dan2 on 2008-12-08
I have a PowerMac G4 Cube running Dapper (6.06).  I am using it as a server, but it has been so long since I set it up, I've forgotten whether I'm actually running a server or desktop distribution.

A few questions:
1) How can I determine whether I'm running the Desktop or Server version?  I tried 'uname -a' and got this response:

Linux cube 2.6.15-52-powerpc #1 Wed Oct 22 18:51:07 UTC 2008 ppc GNU/Linux

My boxes running 8.04 say either "-server" or "-generic" after the architecture for the server and desktop versions, respectively, but 6.06 doesn't say anything.

2) If I'm not running the server version, what are my options when support runs out for the desktop version in July 2009?  Will the server packages (e.g. apache, mysql) that I'm running continue to be updated?  What about the kernel -- am I out of luck?

3) Is there any way to switch over to the server kernel so I can continue to get support past July 2009?

---

### Post by stream303 on 2008-12-08
> **dan2 said:**
> 
1) How can I determine whether I'm running the Desktop or Server version?  I tried 'uname -a' and got this response:

Linux cube 2.6.15-52-powerpc #1 Wed Oct 22 18:51:07 UTC 2008 ppc GNU/Linux

You raise some really interesting questions.  I took a look at the packages list, and see that there doesn't seem to be a "server" kernel for ppc, even though you may have installed the "server" version.  I wonder if they are the same or just some tweaks to sysctls?

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

> 2) If I'm not running the server version, what are my options when support runs out for the desktop version in July 2009?  Will the server packages (e.g. apache, mysql) that I'm running continue to be updated?  What about the kernel -- am I out of luck?

I have wondered about that myself.  If your needs aren't that critical, perhaps just try to hang in there and see what happens.  Although PPC is community-supported these days, and there are even Jaunty Jackalope testing images being made for ppc, I wouldn't bet the farm that they don't just drop the whole thing come July.  You just can't tell these days.  Everyone has been screaming that the Ubuntu ppc sky is falling for years, but you never know.

> 3) Is there any way to switch over to the server kernel so I can continue to get support past July 2009?

I think the best move if you want longer term support for the server is to look into the parent distro.  Debian 4.0r5 "stable" (Etch-n-half) might be the best option.  Everything you've learned here is applicable for the most part.

Even though Debian Lenny is about to go stable at some near future point (ahem.), the previous stable versions get support for a year or even longer sometimes.

I would think that all your server configs should be very similar.  If you are running a gui, definitely write or copy down your existing /etc/X11/xorg.conf, and also /etc/yaboot.conf for reference.

Putting the server on Debian Etch 4.0r5 is only a checkbox away during installation.  Perhaps grab the latest "stable" for powerpc, and see how it goes:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

Not to mention the fact that you have the option of running kernel 2.6.24 with this special release of Etch.

Things are coming to a head now that Dapper's is reaching EOL, and that later releases sometimes have show-stopper installation bugs that can leave one wondering if Ubuntu's ppc server offerings are worth the risk - even though we know that the community does it's best.

Maybe some of the server guys can get more specific - as long as they are tuned to the unique needs / marketing of the ppc port.

---

### Post by dan2 on 2008-12-08
Thanks for the reply.

My understanding is that, while PPC versions after 6.10 are community supported, Dapper PPC is still officially supported by Canonical.  I think they committed themselves through 2011 for the PPC Server version of Dapper.

My PPC server does a few mission critical things, though nothing I couldn't take off of it if I had to.  I just kind of enjoy having a G4 Cube sitting in the corner of my office as a server.  Maybe that makes me weird.  :)  I enjoy the double takes it generates when I have visitors.

I do have some sensitive info on there, so I want to make sure it has all of the current patches, and I would prefer to have official Canonical patches.  If I was using Etch, that would be one thing, but the Ubuntu community and the Debian community are different animals, if you know what I mean.

---

### Post by stream303 on 2008-12-08
> **dan2 said:**
> I think they committed themselves through 2011 for the PPC Server version of Dapper.

I would think so, but I've never spoken to an actual commercial customer for Dapper ppc.

> If I was using Etch, that would be one thing, but the Ubuntu community and the Debian community are different animals, if you know what I mean.

Sure do.  Just cut through the cheerleading / fud on both sides and follow your own path. :)

You've got a very valid concern which interests me, so If I discover anything, I'll be sure to post...

---

