---
title: "Aiiee...Problems Installing RealPlayer. D:"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by DM was on fire! on 2007-08-29
> ashleigh1992@ubuntu:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

[b]The following packages have unmet dependencies:
  realplayer: Depends: xlibs but it is not installable
E: Broken packages[/b]


The following is the output I get from the command I typed above.
That's happened to me before, and I fixed it, but I don't remember how. 

Help, please?

---

### Post by sanderella on 2007-08-29
I wonder if its because you are 

1. running dapper, which wasn't set up to install Realplayer easily or

2. you haven't got universe and multiverse installed.

I'm just a newbie, but these are the common problems:confused:

---

### Post by DM was on fire! on 2007-08-29
I have commercial installed, and that's where RealPlayer and Opera are stored.
I'll check and see if Multiverse and Universe are there, however.

For some reason, I'm wanting to think I actually got it installed by installing MPlayer. XD

EDIT - Yep, they're there. They're the second ones in my Repository list.

EDIT II - I got it. :) It was under Realplay rather then Realplayer.

---

