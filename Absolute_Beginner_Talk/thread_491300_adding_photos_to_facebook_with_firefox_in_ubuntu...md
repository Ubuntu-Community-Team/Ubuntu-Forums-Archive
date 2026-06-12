---
title: "adding photos to facebook with firefox in ubuntu..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Incompetnce on 2007-07-03
FF doesn't seem to like the applet thing to add photos to facebook. what to i need to do? i've tried the simpler photo adding thing but t takes forever...

---

### Post by moredhel on 2007-07-03
I have this problem, but for bebo. Dunno what it is though :\

---

### Post by Incompetnce on 2007-07-08
it is strange, because it is the only problem i've come across on FF.  noone has a solution?

---

### Post by shearn89 on 2007-07-08
It might be something to do with java? You could check you've got the various plugins required...?

---

### Post by Depressed Man on 2007-07-22
There's a Java error that pops up when you try to use it. I googled it, and on the sun Java forums there was a thread about it. It's also acknowledged as a bug on the Firefox forum.

I was having problems with it. Well I still am having problems with it. But I set the java to manual (see how to install java in Ubuntu). In one of the steps when I tried it (I was trying to make sure I had the latest) it set the java to manual. After that the error java still pops up but after clicking ok. I can upload pictures to facebook fine with Ubuntu, Firefox, and Java.

---

### Post by sr4794 on 2008-05-18
I fixed this irritating problem by actually checking which java bits and bobs I had installed via synaptic package manager.

I noticed that although I had sun-java6-jre installed, I didn't have sun-java6-plugin.

Once I had installed this component the facebook photo java applet magically worked.

Make sure you have the following installed...

sun-java6-jre
sun-java6-plugin

Pure revision avoidance.

---

### Post by valavanisalex on 2008-05-22
Unfortunately I don't think the sun plugin is available for my amd64 installation yet.  Any other suggestions for ways to fix this?

---

