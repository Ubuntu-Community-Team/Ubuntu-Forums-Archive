---
title: "KeyWi OS"
date: 2018-12-04
forum: Any Other OS
---

### Post by k9r4n on 2018-12-04
Hey!

I'm slightly new to Linux, but I want to design my own distro, and get it up and running. I've already drawn out some mock-up designs, but I have no idea on the actual development process for the Distro. I've looked at Linux from Scratch, but I'm finding it difficult to understand the process. So, I tried looking for the source code for Ubuntu, to change up the GUI, packages, resources and apps, but found out that Ubuntu is just the collection of packages. All I really want to do for now is the design, and I'll get to the features later on, like support for ARM devices.

Lastly, does anyone know if I can get native support for .exe or .apk files in the system? That's one thing I need to try and get. 

Thanks for any support that anyone can give!

k9r4n

---

### Post by QIII on 2018-12-04
Hello!

Other than some general hints, what you asked for may be beyond the scope of a Forum like this.  But there are many guides for what you want to do, including [this]("https://fosspost.org/tutorials/create-linux-distribution-based-on-ubuntu"), which I got from Google with the following search terms:

```
how to build your own ubuntu-based distro
```

I'm sure some helpful people will be along to give you some high-level guidance.

If you are talking about Windows executables, you will likely not get them to work natively, unless they are written in C# and you can make use of Mono's APIs.  Windows .exes are written for Windows.  Linux is an entirely different beast.

*Some* Windows programs can be beaten into submission by using Wine, but nothing is guaranteed and many programs simply will not work.

Best wishes!

---

### Post by k9r4n on 2018-12-05
Thanks so much! Will have a look into the guide now. Thanks for trying!

k9r4n

---

