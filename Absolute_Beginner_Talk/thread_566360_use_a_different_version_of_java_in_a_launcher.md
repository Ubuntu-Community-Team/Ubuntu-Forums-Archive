---
title: "use a different version of java in a launcher"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2007-10-03
So here's my issue, I'm using sun-java-6 for my default jvm, because it's newer and runs eclipse better.  But i have a teeny little program that I use all the time (iriverter) that requires the free GNU gcj version of java.  I can always just use```
sudo update-alternatives --config java
``` to switch jvms, but i'd prefer to change the java call for iriverter in the launcher with something like a java -version:<gcj?> but I don't know exactly what that version string should be

for some help, I've got a couple outputs ```
<luke@luke-brain:~$> java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

and for sun java:
```
 java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Server VM (build 1.6.0-b105, mixed mode)

```

Any help would be super appreciated.

---

### Post by vikram on 2007-10-04
locate both JREs and try calling java with the full path to the required version.

---

