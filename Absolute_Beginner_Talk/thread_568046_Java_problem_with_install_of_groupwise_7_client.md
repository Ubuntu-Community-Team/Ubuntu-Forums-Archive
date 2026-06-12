---
title: "Java problem with install of groupwise 7 client"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by TalioGladius on 2007-10-05
I've followed this how to word for word...

[http://ubuntuforums.org/showthread.php?t=147278](http://ubuntuforums.org/showthread.php?t=147278)

I'm getting this error when trying to run the client from the terminal

$ ./groupwise.sh
ecxxxxc@ITS-76524:/opt/novell/groupwise/client/bin$ /opt/novell/groupwise/client/bin/groupwise-bin: error while loading shared libraries: libjvm.so: cannot open shared object file: No such file or directory



any ideas? I can't find libjvm.so or whatever directory it's talking about...

---

### Post by TalioGladius on 2007-10-05
bump

---

### Post by apoth on 2008-02-18
Check what's in /opt/novell/groupwise/client/jre

You've probably just linked it to the wrong place. Something like this should resolve it:

```

sudo aptitude install sun-java6-jdk
sudo rm -rf /opt/novell/groupwise/client/jre
sudo ln -sf /usr/lib/jvm/java-6-sun/jre /opt/novell/groupwise/client/jre
```

---

