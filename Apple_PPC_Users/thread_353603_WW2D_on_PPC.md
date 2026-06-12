---
title: "WW2D on PPC?"
date: 2007-02-04
forum: Apple PPC Users
---

### Post by ubuntubrian on 2007-02-04
I tried to install ww2d on my G4 TiBook without success. The WW2D site [http://ww2d.org/home.php](http://ww2d.org/home.php) says that it can be installed and run on ppc linux by downloading the no-arch package and the java libraries required. I haven't found all the java dependencies to be able to install them into the ww2d/lib directory, basically just copying them into the directory. This is because 2 of them are alien converted rpms and I have no idea where there were installed but it wasn't in ww2d/lib. Has anyone gotten this to work? Is anyone interested in getting this free "google earth" alternative to workon Ubuntu PPC?
Thanks

---

### Post by grazie on 2007-02-04
I haven't got WW2D to work as I didn't know about it, but now that I do, I'll certainly be looking at it more closely. The example screenshots don't show much detail though.

---

### Post by ubuntubrian on 2007-02-05
I checked several forums on WW2D and it basically looks like Google Earth as far as the images. Any help is greatly appreciated!

---

### Post by ubuntubrian on 2007-02-05
I've been posting to the WW2D forum at: [http://forum.worldwindcentral.com/showthread.php?p=41425#post41425](http://forum.worldwindcentral.com/showthread.php?p=41425#post41425)

I can continue there and here but I've had a bit more luck since my first post here. WW2D starts and then seg faults.

"java -jar WW2D.jar
WW2D 0.99.88 by Vitaliy Pronkin <pronvit@gmail.com> starting...
TinyLaF v1.3.04
'Default.theme' not found - using YQ default theme.
JVMDG217: Dump Handler is Processing Signal 11 - Please Wait.
JVMDG303: JVM Requesting Java core file
JVMDG304: Java core file written to /home/brianokeefe/ww2d-0.99.88rc1/javacore.20070205.181110.8877.txt
JVMDG215: Dump Handler has Processed Exception Signal 11.
Segmentation fault"

---

### Post by grazie on 2007-02-12
I've not had go with this and I'll probably not bother. The problem is that a binary accelerated graphics driver will almost certainly be essential. As we know, these are not available for linux ppc.

---

