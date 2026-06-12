---
title: "Xcode on Ubuntu?"
date: 2010-11-22
forum: Apple Hardware Users
---

### Post by Xplat on 2010-11-22
Hi, I am looking for a way to run Xcode on ubuntu.

Ubuntu says it is a Java Class.

I need Xcode to compile a mac os x application for a friend, but I don't have a mac.

Does anyone know of a way to compile mac applications on ubuntu, have them work on a mac, and not use a mac at all to build it?

I also need to build it for a PPC computer on an intel computer.

---

### Post by smoors on 2010-11-23
Hi,

XCode does not run on Linux and it is definitely not a java class. What kind of program to you want to compile for OS X?

---

### Post by Xplat on 2010-11-23
I want to compile an Xcode project. Since I can't read what the files are to compile, I need to use the project.

The files are in Obj-C format.

---

### Post by smoors on 2010-11-24
If the files rely on a Mac OS X framework, i would say that there is no chance to compile them on linux for Mac OS X. And if you don't own a mac, you don't have a chance to test your results at all... I would say that this makes it really impossible..

---

### Post by Xplat on 2010-11-27
> **smoors said:**
> If the files rely on a Mac OS X framework, i would say that there is no chance to compile them on linux for Mac OS X. And if you don't own a mac, you don't have a chance to test your results at all... I would say that this makes it really impossible..

Is there a port of Cocoa framework?

---

### Post by augustuen on 2011-02-28
No, there is no Cocoa port to Ubuntu. But, if this is an application that is meant to be runned on Ubuntu (there is no way you are going to compile a Mac OS X application using Ubuntu), then I recommend that you manually port the application (using a framework that works with Ubuntu). The lost similar thing to Xcode that I can think of that is compatible with Ubuntu is QT Creator. 

And why does your friend need you to compile this application anyway?

---

