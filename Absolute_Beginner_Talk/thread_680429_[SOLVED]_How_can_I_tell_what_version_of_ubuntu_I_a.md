---
title: "[SOLVED] How can I tell what version of ubuntu I am using?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by einherier on 2008-01-27
I bet this question has been asked before, but I will be danged if i can find it in the forum...

sorry....

thanks in advance.

---

### Post by Presto123 on 2008-01-27
It is not a problem ;)

Simply go into your System/Administration menu and find the System Monitor. If it doesn't show up right away, click on the "System" tab.

---

### Post by Udaho on 2008-01-27
Click on System > Administration > System Monitor.

---

### Post by steveneddy on 2008-01-27
System --> About Ubuntu

---

### Post by einherier on 2008-01-27
Thanks

---

### Post by gtdaqua on 2008-01-27
Or open terminal and type:

```

lsb_release -a

```

and if you want to know kernel version, processor and other info, type:

```

uname -a

```

---

### Post by steveneddy on 2008-01-27
> **gtdaqua said:**
> Or open terminal and type:

```

lsb_release -a

```

and if you want to know kernel version, processor and other info, type:

```

uname -a

```

Cool - I had forgotten about that one.

---

### Post by gtdaqua on 2008-01-27
sorry to hijack this,

but I have always wanted to know the architecture running using a proper command.

for e.g. typing 'uname -a' give this:
```

Linux PCNAME 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

```

Now the kernel ends with '-386', meaning a 32-bit version. Is there any other command to reveal archtiecture?

---

### Post by steveneddy on 2008-01-27
> **gtdaqua said:**
> sorry to hijack this,

but I have always wanted to know the architecture running using a proper command.

for e.g. typing 'uname -a' give this:
```

Linux PCNAME 2.6.22-14-386 #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux

```

Now the kernel ends with '-386', meaning a 32-bit version. Is there any other command to reveal archtiecture?

In your uname -a, the i686 reveals the 32 bit arch, while on my 64 bit machine it looks like this

```

2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 **x86_64** GNU/Linux


```

is the 64 bit stuff.

---

### Post by flyingtiger on 2008-02-06
uname -all or the shorthand version uname -a in a term window will give the information that you seek. 

Knowledge has no age boundaries -- my quote --

---

