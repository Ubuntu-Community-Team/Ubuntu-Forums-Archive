---
title: "updating java enviorment"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by yoavbenarie on 2006-05-24
hey
I am working a lot on java tools' but the default version in the ubuntu is 1.4,
i downloaded the new version 1.5 but can't manage putting it in the PATH,
from any place in the terminal it still execute the 1.4 version.

what should i do to change the version globaly?
thanks yoav

---

### Post by mlind on 2006-05-24
See [this]("https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e") wiki entry.

Don't forget to do *sudo update-alternatives --config java* after installing jdk in java-package way.

---

### Post by yoavbenarie on 2006-05-24
thanks 
but it gives me 3 alternatives that none of them is ofcourse not the path to the new version, the ones it gives me i can't change.
can i add new path to this list?

---

### Post by mlind on 2006-05-24
if you installed jre/jdk using the java-package (fakeroot) method, then Sun's jvm
should be on the list.

If you're going to install it some other way, then you should use update-alternatives
script with --install parameter. see update-alternatives --help for reference.

---

