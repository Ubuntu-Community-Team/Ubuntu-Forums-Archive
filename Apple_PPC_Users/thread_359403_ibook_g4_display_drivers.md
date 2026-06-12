---
title: "ibook g4 display drivers?"
date: 2007-02-11
forum: Apple PPC Users
---

### Post by onx on 2007-02-11
I have an ibook g4 that I recently installed edgy (6.10) on. Supposedly it has a mobility radeon 9200, and I was hoping I might be able to get beryl working on this thing, however first I need to get openGL working (by installing display drivers apparently).

Currently it seems the ATI/AMD website has linux drivers but they don't support PPC... (running 2.6.17-11-powerpc kernel)

When I do :
glxinfo | grep direct 

I get something like this:
```

libGL warning: 3d driver claims not to support visual 0x4b
direct rendering: Yes

```

I take this to mean openGL isn't working out of the box, and thus beryl wont work. Is there anyway to get openGL support on these things? Has anyone been able to get beryl working on an iBook (search of the beryl wiki and forums for "ibook" returned nothing). Are there any opensource drivers that will do the job?

Thanks for any help in advance.

---

### Post by AlphaMack on 2007-02-12
You'll need the ATI proprietary drivers.  Unfortunately, no PPC support as you have already found out.

---

### Post by seebol on 2007-02-12
I have an ibook g4 from july 2004, and it gave me the same warning. I went ahead and installed aiglx+beryl, and the effects could run pretty well. I found it all a bit overwhelming though, and I had trouble at times playing video while beryl was running, so I uninstalled it.

---

### Post by fearevilleet on 2007-02-15
So are you saying it is not possible to install video drivers for an ibook g4? I am just about to install it on mine since osx is starting to get slow, but if it dose not have video support I will just wait for 10.5.

---

### Post by grazie on 2007-02-15
There's drivers, but no ppc accelerated drivers, which means it'll be slow.

---

