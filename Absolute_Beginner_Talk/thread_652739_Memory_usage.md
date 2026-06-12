---
title: "Memory usage"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-12-29
Hello
I tried to check how much memory is used and from my 1024 mb it says the following:

         
I used the "free" command and the output is:

```
 total       used       free     shared    buffers     cached
Mem:       1034440     468916     565524          0      13556     276604
-/+ buffers/cache:     178756     855684
Swap:       522072          0     522072

```

But the system monitor says 180 MB are used

Which one shall I trust.

What can I do to free my memory? I mean my windows uses about 200mb and linux uses 170 and people claim it can run on old and slow machines. I mean I am just using it for the internet and the terminal right now. So what programs can I get rid of that run in the background (like evolution which I just removed from my system)

---

### Post by reverseninja on 2007-12-29
I would suggest this article for cleaning up unneeded services:

[http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php")

---

### Post by Hallvor on 2007-12-29
180 MB is what is actually in use. The rest is used for disk cache and is essentially free. RAM is wasted if it is not used.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by kishorebudha on 2007-12-29
> **KOTAPAKA said:**
> Hello
I tried to check how much memory is used and from my 1024 mb it says the following:

         
I used the "free" command and the output is:

```
 total       used       free     shared    buffers     cached
Mem:       1034440     468916     565524          0      13556     276604
[COLOR="Red"]**-/+ buffers/cache:     178756     855684**[/COLOR]
Swap:       522072          0     522072

```

But the system monitor says 180 MB are used



The line beginning with -/+ buffers/cache is what your system is actually using. So 178 MB is the actual usage while the rest 866 MB is being used for buffers and cache. Your swap is intact, thus the memory usage is good at the moment.

See this article: [http://www.ibm.com/developerworks/linux/library/l-linux-memory.html](http://www.ibm.com/developerworks/linux/library/l-linux-memory.html)

---

