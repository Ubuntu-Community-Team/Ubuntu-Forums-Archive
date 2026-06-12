---
title: "[SOLVED] Are there any package managers?"
date: 2007-09-04
forum: BSD
---

### Post by Majorix on 2007-09-04
Are there any package managers for BSD systems? Or do BSD users compile everything from source? Or what is the deal?

Is any company working on a BSD with a package manager?

Why I am asking this is that I have a spare PC to experiment with and I want to try a BSD system.

---

### Post by mips on 2007-09-04
No need to compile from source if you dont want to, some even reccomend that you DONT compile from source.

You can use pkg_add from the cli to install packages. similair to apt-get

I have used a GUI frontend to that before but cannot remember what it was called.

If BSD is new to you then I would suggest trying the latest PC-BSD 1.4RC or whatever is newer, very close to release date.

---

### Post by Majorix on 2007-09-04
OK, pkg_add, I will remember that.

Is pkg_add available under FreeBSD 6.2 and is it any good for starters? I also looked at OpenBSD but their site was awfully and quickly done, so I thought that would how their distro would be too.

Finally, is PCBSD a good choice or should I stick with FreeBSD?

---

### Post by mips on 2007-09-04
> **Majorix said:**
> OK, pkg_add, I will remember that.

Is pkg_add available under FreeBSD 6.2 and is it any good for starters? I also looked at OpenBSD but their site was awfully and quickly done, so I thought that would how their distro would be too.

Finally, is PCBSD a good choice or should I stick with FreeBSD?

pkg_add is available for all of the BSD versions and yes I would say it is pretty good.

Nothing wrong with the OpenBSD website, it's just not flashy but it is well laid out and their online docs are very good, same goes for other bsds. OBSD is very anal about their security and code auditing and has a lot of respect.

PCBSD is based on FreeBSD 6.2. The thing is PCBSD makes the whole process easier for the end user, the underlying system is still freebsd and all the documentation for freebsd applies in pcbsd. PCBSD also added the PBI package manager to simplify things even further.

I would recommend PCBSD to you for now.

---

### Post by Majorix on 2007-09-04
I see, thanks a lot for your replies.

I will install PCBSD (downloading now) on that spare HDD I mentioned.

Marking the thread SOLVED doesn't work with me, if any mod seeing this thread could mark this SOLVED for me I would be grateful.

---

### Post by mips on 2007-09-05
> **Majorix said:**
> 
I will install PCBSD (downloading now) on that spare HDD I mentioned.
.


I really think that you are going to like PCBSD ;)

---

### Post by theonlyrealperson on 2007-09-05
> **mips said:**
> I really think that you are going to like PCBSD ;)

I agree. They've put a lot of work into that, and it shows. I love "rolling my own" FreeBSD, but installing PC-BSD is the next best thing.

---

### Post by igknighted on 2007-09-06
It's a little late, but I personally think that DesktopBSD is a better way to jump into BSD.  Like PC-BSD, it is basically FreeBSD 6.2.  Like PC-BSD there are holes in the packages distributed (no office suite in either for example).  Overall, I just feel like DesktopBSD has better package tools and a more professional interface.  Plus the liveCD is great.  But both are great choices.

---

### Post by Sunnz on 2007-09-13
> **igknighted said:**
> It's a little late, but I personally think that DesktopBSD is a better way to jump into BSD.  Like PC-BSD, it is basically FreeBSD 6.2.  Like PC-BSD there are holes in the packages distributed (no office suite in either for example).  Overall, I just feel like DesktopBSD has better package tools and a more professional interface.  Plus the liveCD is great.  But both are great choices.
Oh nice I tried FreeBSD for a while then jumped to OpenBSD for just about everything but now considering going back to FreeBSD for my Desktop.

So DesktopBSD is one step closer to FreeBSD than PCBSD? Like, everything is essentially done in the FreeBSD way instead of have new sub-systems??

---

### Post by mips on 2007-09-13
> **Sunnz said:**
> 
So DesktopBSD is one step closer to FreeBSD than PCBSD? Like, everything is essentially done in the FreeBSD way instead of have new sub-systems??

I actually think PCBSD is more polished but I have not tried the latest version od DBSD. For some odd reason I dont like PBI in PCBSD but that does not stop you from using the normal FBSD package manager.

---

### Post by altariel on 2007-09-18
well, you also have the nifty sysinstall feature :) 
- which you might have encounterd during install ... 

if you run **sysinstall** - **configure** computer - **add packages** you can select packages you want to install and they will be installed including any dependencies! :)

---

