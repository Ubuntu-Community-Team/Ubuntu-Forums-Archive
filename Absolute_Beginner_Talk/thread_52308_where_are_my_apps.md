---
title: "where are my apps?"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-27
hi there very new to ubuntu, but i am making progress slowly.
ok i have downloaded and installed some apps through synaptic manager. they downloaded and installed but where are they?. first one i tried was ace of penguins because i thought it would be quick to download and easy to find under games after installation but i can't find it anywhere, how do i start it?

---

### Post by Sam on 2005-07-27
All programs are not installed on the same directory. You can find them in /usr/share, /opt, but there are libraries in /lib or /usr/lib, then the executables can be found on /bin, etc...

To have a list of all installed files of a package, goto Synaptic, Properties of the package, Installed Files.

Or use the locate command:```
$ locate <pattern>
```

---

### Post by porsher_puddles on 2005-07-27
ty for that i got the general idea now i have found the things i was looking for

---

