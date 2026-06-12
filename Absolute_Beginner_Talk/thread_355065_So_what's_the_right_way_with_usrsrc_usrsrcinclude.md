---
title: "So what's the right way with /usr/src/ /usr/src/include?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Destruct on 2007-02-06
In ubuntu /usr/include/linux is not symlinked to /usr/src/linux-headers*/include/linux

And i'm reading opinions it actually shouldn't be. But make of some things fails because /usr/include/linux is incomplete and missing files are in /usr/src/linux-headers*/include/linux

For example i tried to make dvb-tools from linuxtv.org  and it failed because of missing compiler.h. So it's fault of certain programs that they don't look in /usr/src/? Or something needs to be done about that? Ofcourse it worked when i temprorarily moved /usr/include/linux away and replaced it with symlink to headers in /usr/src. So what's the right way?

And about compiling custom kernel, isn't it going to get compiled against current kernel headers? Nothing needs to be done to compile it against it's own source tree headers or something like that?

Do i need to keep previous kernel's header's in /usr/src after compiling a new custom one of newer version? Or should they be removed? What about /usr/include?

For example what if i'm going to stand-alone compile some kernel modules later(placed outside of actual kernel source tree), won't they be compiled agains previous kernel header's if it's header's remain unless i somehow tell make process otherwise?

Btw. after i'm done compiling new kernel how do i leave only headers and remove rest of now unnecessary full source?

---

### Post by darrenm on 2007-02-08
Not a big compiler so this is AFAIK...

> **Destruct said:**
> In ubuntu /usr/include/linux is not symlinked to /usr/src/linux-headers*/include/linux

And i'm reading opinions it actually shouldn't be. But make of some things fails because /usr/include/linux is incomplete and missing files are in /usr/src/linux-headers*/include/linux

It's never a problem to symlink directories to places compiler scripts are looking for them. Back in the day I had to do that with everything. Mandrake always had everything in /usr/include and nothing was set up for that. Generally you can do ./configure --PREFIX=/usr/src if its looking in the wrong place. 

> **Destruct said:**
> For example i tried to make dvb-tools from linuxtv.org  and it failed because of missing compiler.h. So it's fault of certain programs that they don't look in /usr/src/? 
Yes, but the accepted thing is to symlink it yourself or use PREFIX. Try ./configure --help to get the options.
> **Destruct said:**
> Or something needs to be done about that? Ofcourse it worked when i temprorarily moved /usr/include/linux away and replaced it with symlink to headers in /usr/src. So what's the right way?

Depends on the distro. Mandriva and I think RH use /usr/include and everyone else uses /usr/src (i think) If you get problems, symlink it.

> **Destruct said:**
> And about compiling custom kernel, isn't it going to get compiled against current kernel headers? Nothing needs to be done to compile it against it's own source tree headers or something like that?

Do i need to keep previous kernel's header's in /usr/src after compiling a new custom one of newer version? Or should they be removed? What about /usr/include?

Not if you don't plan on using the old kernel again. Programs will try to compile using the headers for that kernel so if you run 2.6.19 then you need linux-headers-2.6.19 in /usr/src

> **Destruct said:**
> For example what if i'm going to stand-alone compile some kernel modules later(placed outside of actual kernel source tree), won't they be compiled agains previous kernel header's if it's header's remain unless i somehow tell make process otherwise?

Ummm... I think if you're compiling against the wrong headers you will get an error anyway so you will know.

> **Destruct said:**
> Btw. after i'm done compiling new kernel how do i leave only headers and remove rest of now unnecessary full source?

I think most stuff will look at /usr/src/linux-headers-`uname -r` so won't just use /usr/src/linux if its symlinked against the wrong version for what you're currently booting. But to be sure you need to symlink /usr/src/lnux agains the headers of the main kernel you boot with.

---

