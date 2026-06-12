---
title: "How to replace IceadTea with Sun Java?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-16
Hi
thank you for reading my post
I have sun java 6 installed in ubuntu and also Ubuntu has installed IcedTea? when i select some packages to install.
Now IcedTea is in the path and when I run java command IcedTea java execute instead of Sun java.
How I can put Sun Java bin in the path?
I know where I installed Sun java, I do not know how to add it to path in  a way that its java command execute instead of IcedTea command.


Thanks

---

### Post by Hospadar on 2008-01-16
It's already in the path, you just need to tell the shell which binary you want to provide "java"

Do a "sudo update-alternatives --config java" and select the sun java

---

### Post by legolas_w on 2008-01-16
What a nice command, Is there any way to add my own java installation to the set of java installation that this command shows?
I have installed java 6 into /opt/java6

Thanks

---

### Post by legolas_w on 2008-01-17
> **legolas_w said:**
> What a nice command, Is there any way to add my own java installation to the set of java installation that this command shows?
I have installed java 6 into /opt/java6

Thanks

Any comment about how I can include my java installation into the list which that command shows?

Thanks

---

