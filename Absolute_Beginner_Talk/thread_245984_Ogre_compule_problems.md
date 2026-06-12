---
title: "Ogre compule problems"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by 916 on 2006-08-28
I recently transferred from Windows to Ubuntu and, to be honest, I was astonished. That is why I wanted to make the OGRE engine work on this brand new system. I downloaded the archive, Installed CG toolkit from NVidia and am trying to build the engine. Whe I try to ```
./condigure
``` it, everything runs smooth. Then I make it. It's ok too. But when I make install (I tried to clean the make, too!), after a half an hour of the setup, it goes like:
```
../../../RenderSystems/GL/src/atifs/src/.libs/libatifs.a(ATI_FS_GLGpuProgram.o):(.gnu.linkonce.d._ZTVN4Ogre19ATI_FS_GLGpuProgramE[vtable for Ogre::ATI_FS_GLGpuProgram]+0x94): undefined reference to `Ogre::GpuProgram::getLanguage() const'
collect2: ld returned 1 exit status
libtool: install: error: relink `RenderSystem_GL.la' with the above command before installing it
make[5]: *** [install-pkglibLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/zarea/Work/ogrenew/RenderSystems/GL/src'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/zarea/Work/ogrenew/RenderSystems/GL/src'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/zarea/Work/ogrenew/RenderSystems/GL/src'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/zarea/Work/ogrenew/RenderSystems/GL'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/zarea/Work/ogrenew/RenderSystems'
make: *** [install-recursive] Error 1

``` ](*,) 


Could ypu please help me solve this thing? I'm really new to ubuntu so maybe I missed something? Thank you.

added:

Oh, and sorry for the topic name, it's 2 a.m. now so I don't really see the keyboard. :(

---

