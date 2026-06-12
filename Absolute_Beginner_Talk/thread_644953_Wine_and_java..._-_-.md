---
title: "Wine and java... -_-"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-19
I have a little bit of an issue.

I have a program that I want to run under wine....but when I execute it, it thinks for a second....then gives me an error that "J2SE 1.4 or higher is not installed"   



what do I do? is it a wine library im missing?

---

### Post by Inxsible on 2007-12-19
> **B34ST1Y said:**
> I have a little bit of an issue.

I have a program that I want to run under wine....but when I execute it, it thinks for a second....then gives me an error that "J2SE 1.4 or higher is not installed"   

what do I do? is it a wine library im missing?Do you have Java installed in your Windows environment?

What application are you trying to run? if its a windows app, you need to have Java installed in your Wine enviroment. Your local Java under Linux won't work.

---

### Post by bump_ on 2007-12-19
I am not sure if Wine uses the Java you have installed under Ubuntu, but I am going to assume it does.

Do you have a higher version of java installed? If not, they can be installed from the repositories through Synaptic.

If you have installed a more recent version, and you are still getting the error, the more recent version is probably not your default. You can fix this by typing

```
sudo  update-alternatives --config java
```

and choose the one you installed from the list

---

### Post by B34ST1Y on 2007-12-19
how am I supposed to install java into wine ? ?

---

### Post by popch on 2007-12-19
I have not tested that, but I would presume that you download JRE for windows and run it as a Windows app. That should install JRE.

On the other hand, I should think that if it's a Java application anyway, it ought to be executable under Linux without Wine.

After all, it's Sun's argument for using Java: that Java programs are executable in a wide range of operating systems without any changes at all.

Perhaps some of the more experienced members know what to do in order to run a Java app which has been packaged for Windows.

---

