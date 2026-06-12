---
title: "Java reverting to GCJ"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by dcminter on 2008-02-26
This is probably (certainly?) me doing something dumb, but it's very irritating, so help will be much appreciated.

I'm using Kubuntu as my development environment and I'm a Java bod. I'm running Tomcat 5.5 and I've used update-alternatives to set my preferred JVM to Java 6.

However...

Every time I do an update or install with synaptic or the apt tools, I get my JVM reverted to the GCJ stuff. Since that doesn't have some of the features that I need for my web apps, when I next restart Tomcat they start falling over.

Is there a way to prevent this from happening? Each time it does it I have to go back in and do "update-alternatives --config java" and while it's not the end of the world I'm getting a bit fed up with it. Plus it usually takes me a few minutes of frenzied debugging to realise that it's not my latest idiot change to the code that's actually causing the problem.

Basically I'm hoping there's a "Do NOT alter my preferred JVM _ever_" bit that I can set.

Thanks,
Dave.

---

### Post by luisromangz on 2008-02-26
Can't you simply uninstall gcj? It will remove some programs, like eclipse, but a "virgin" (without the gcj stuff) Eclipse is faster anyways...

---

### Post by dcminter on 2008-02-26
Actually I tried that, but if I remember correctly it got reinstalled when I installed some other package with a Java dependency. It would be almost as annoying to have to keep uninstalling it. Besides, I'd rather like to keep it around so that I know what does and doesn't run ok against GCJ.

---

