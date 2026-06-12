---
title: "Building on a Mac"
date: 2008-01-30
forum: Apple Intel Users
---

### Post by jknotzke on 2008-01-30
Dumb question here.. I am a developer on a OSS project and we also create binaries for Mac OSX Intel.. If I purchase a Mac Mini and I dual boot it (OSX/Ubuntu), when I boot into Ubuntu, the binary that I build, including static libs, etc, will they run on a i386 box ?

   Thanks

   J

---

### Post by cyberdork33 on 2008-01-30
> **jknotzke said:**
> Dumb question here.. I am a developer on a OSS project and we also create binaries for Mac OSX Intel.. If I purchase a Mac Mini and I dual boot it (OSX/Ubuntu), when I boot into Ubuntu, the binary that I build, including static libs, etc, will they run on a i386 box ?Of course it depends on the specific compiler flags you are using, but if you build a generic i386 binary in Ubuntu, it should run in any i386 Ubuntu installation (that has all the required dependencies). A sure fire example of the truth to this is the fact that the Macs use the same x86 repos as everyone else for software installs. i.e. an Intel Mac is a x86 box.

---

### Post by jknotzke on 2008-01-30
Ok excellent. Thanks for the replies. I think I have myself a little solution to having to support both environments.

   Now I just have to find the money for the mac mini. ;-)

  J

---

