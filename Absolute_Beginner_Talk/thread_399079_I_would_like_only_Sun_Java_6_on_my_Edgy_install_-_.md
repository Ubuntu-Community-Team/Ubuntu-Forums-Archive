---
title: "I would like only Sun Java 6 on my Edgy install - how to?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by cjl2301 on 2007-04-01
Ok I've actually got Java 5 and the default gnu java on my install right now.  I didn't have any problems getting 5.

However, I do a lot of Java and I really only want the latest sun java install (6.01) on my box.  I don't want to fiddle with switching alternatives, links and such.

Is there an easy way to just blow away everything java related and just install Sun Java 6?

Please keep in mind that I do a lot of Java and I'm afraid of breaking my install so that nothing works...  :(

---

### Post by zvacet on 2007-04-02
Download newset Java from repositories and after that you can delete every previous version of Java.

---

### Post by cjl2301 on 2007-04-02
Hmm... well actually Java 6 does not seem to be in the repositories...  I guess what I'm really asking is: How do I totally remove all the previous versions?  Should I just use the package manager?  If so - what packages am I looking for for the gnu stuff?

---

### Post by jvc26 on 2007-04-02
Isnt sun java6 available in sun-java6-jre and sun-java6-jdk packages on edgy now?
Il

---

### Post by cjl2301 on 2007-04-02
I have all the checkboxes checked in the "Software Sources" dialog in the Synaptic Package Manager and I don't see "sun-java-6" as an available package.

Is there some other packages to enable?

---

### Post by Maestro23 on 2007-04-02
> **cjl2301 said:**
> I have all the checkboxes checked in the "Software Sources" dialog in the Synaptic Package Manager and I don't see "sun-java-6" as an available package.

Is there some other packages to enable?

If all your  repositories are enabled it should be there.  Open up synaptic and search "java6".

Double check your repo's: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cjl2301 on 2007-04-03
Ok I dont understand what I'm missing...

Here is what my repos look like:

[http://img227.imageshack.us/img227/1054/screenshotsoftwaresourcjs0.jpg](http://img227.imageshack.us/img227/1054/screenshotsoftwaresourcjs0.jpg)

and here is what I get when I search for "sun-":

[http://img369.imageshack.us/img369/3097/screenshotsynapticpackasd0.jpg](http://img369.imageshack.us/img369/3097/screenshotsynapticpackasd0.jpg)


I have of course hit "reload" several times.

Do I have to add a "third party" repo?  Or is this package just not available for Edgy?

---

### Post by zvacet on 2007-04-03
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

I downloaded it from Edgy repos so you can do it too

---

### Post by johnny4north on 2007-04-03
I believe that i might found a possible solution at this link- [http://www.ubuntu-forum.de/thread.php?threadid=15763](http://www.ubuntu-forum.de/thread.php?threadid=15763)  Read the part that is in english.  good luck.  i will check back later.

---

