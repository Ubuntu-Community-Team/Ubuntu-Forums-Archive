---
title: "Lowering Java's use of CPU?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by wishpishh on 2005-11-21
When I use heavy Java applications in Ubuntu it often use almost all CPU capacity and it's almost impossible to use any other applications at all during the same time. I know that Java overall reduces performance of the system but it is much worse in Ubuntu than in Windows XP for example. When running 'top' in the terminal, load average is often above 1.0. Is there any way to prevent this, some kind of way to restrict Java's uses of the resources, or something?

I'm new to Linux and Ubuntu, so I'm sorry if the answer is obvious, but I guess the tolerance is quite high in this section of the forum.

---

### Post by 23meg on 2005-11-21
What Java version are you using? If you're using Blackdown try the official Sun release, and vica versa.

---

### Post by mdecler2 on 2007-03-13
I have the same problem, java_vm process is using 90%+ CPU, and I have installed the latest java JRE package from Sun (1.6). I have reported this issue for about a month now, and I have no idea what I should do about it besides dropping Java completely. That, however, would be bogus.

---

### Post by npman on 2007-08-15
I, too, have been running into this.

I have a site using LTSP- one of the clients needs to do outreach in certain chatrooms that use Java- with Firefox (feisty 2.0.0.6), I believe we are on Sun Java 6- latest feisty version.

Inevitably I end up with java_vm processes that gobble huge amounts (>98%) of CPU and the entire system slows.

Is this a Firefox issue, a Feisty issue or a Java problem?

---

