---
title: "Will not boot! &quot;Openpic: exit&quot;"
date: 2005-04-09
forum: Apple PPC Users
---

### Post by eBeL on 2005-04-09
I am having trouble getting linux to boot.  It was working flawlessly earlier today and then I booted back into mac os x.  I have booted back and forth several times.  This time around, I was not able to boot back into linux.  It hangs on "openpic: exit"

I am not too linux savvy.  Help please!

---

### Post by humanity_to_others on 2005-04-09
[http://ubuntuforums.org/showthread.php?p=107513](http://ubuntuforums.org/showthread.php?p=107513)

---

### Post by eBeL on 2005-04-09
[QUOTE=humanity_to_others][http://ubuntuforums.org/showthread.php?p=107513](http://ubuntuforums.org/showthread.php?p=107513)[/QUOTE]
 I have read that topic and it really doesn't help me.

---

### Post by staticdisaster on 2005-04-09
I remember getting bit by this bug on the last ubuntu release. I fixed it by adding noapic as a boot arguement. Apparently if I warm boot then it freezes, but cold booting should boot into linux everytime.

---

### Post by eBeL on 2005-04-10
[QUOTE=staticdisaster]I remember getting bit by this bug on the last ubuntu release. I fixed it by adding noapic as a boot arguement. Apparently if I warm boot then it freezes, but cold booting should boot into linux everytime.[/QUOTE]
 Excellent observation.

About 1/10 times it will boot right after warm botting, but cold booting will be nearly every time.

---

### Post by eBeL on 2005-04-11
It seems this is not entirly true I guess, Today i have had to attempt to boot it several times to work.  This is really annoying, and if there is no fix then as good as this distro is, I will have to find something else. :?

---

### Post by Len on 2005-04-12
Well, you could try to compile your own smp kernel. You can get the sources from Synaptic ;-).

---

### Post by eBeL on 2005-04-13
[QUOTE=Len]Well, you could try to compile your own smp kernel. You can get the sources from Synaptic ;-).[/QUOTE]
 I would rather find something else :P

---

