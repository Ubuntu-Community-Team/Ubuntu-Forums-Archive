---
title: "How do I install unrar-free so I can use Ark"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by johnthemong on 2007-11-06
I recently changed distro from kubuntu 7.04 to ubuntu 7.10. I had been using ark as my archive manager with not problems under the old system and for some reason I can't seem to use it now. When I go to unwrap a rar archive I get this message up.

The utility unrar-free is not in your PATH.
Please install it or contact your system administrator.

Can anybody explain how I go about installing this?

---

### Post by Fixman on 2007-11-06
```
sudo apt-get install unrar-free
```

---

### Post by johnthemong on 2007-11-06
Thanks. It seems like i've managed to install that ok. However, I'm still having problems unwrapping this archive. Basically I'm getting an error report from Ark though I can't seem to copy it into here. It says plenty but the main word seems to be Failed. I've tried on a couple of rar archives and had the same problem. 

I also install 7 zip though this doesn't seem to be showing up in my applications list so I can't figure how to try that. 

Any help appreciated.

---

### Post by santiagoward2000 on 2007-11-06
> **johnthemong said:**
> Thanks. It seems like i've managed to install that ok. However, I'm still having problems unwrapping this archive. Basically I'm getting an error report from Ark though I can't seem to copy it into here. It says plenty but the main word seems to be Failed. I've tried on a couple of rar archives and had the same problem. 

I also install 7 zip though this doesn't seem to be showing up in my applications list so I can't figure how to try that. 

Any help appreciated.

What does it say exactly? If it says something about not having permission, maybe you need to run it as sudo to copy the file to that particular path.

---

### Post by johnthemong on 2007-11-06
> **santiagoward2000 said:**
> What does it say exactly? If it says something about not having permission, maybe you need to run it as sudo to copy the file to that particular path.

No, it's not mentioning permissions, just saying that it has failed.

---

### Post by qpieus on 2007-11-06
Install unrar, not unrar-free:```
sudo apt-get install unrar
```
unrar-free can't extract v3 rar files, maybe that's why you're getting errors?
unrar is the "real" unrar from the rarsoft company.

This is from LinuxApp Finder:

unrar-free
Description
Unrar can extract files from .rar archives. Can't handle some archives in the RAR 3.0 format, only the non-free "unrar" package can do that.

---

### Post by tubasoldier on 2007-11-06
the real unrar from the rarsoft company is available in the [MediBuntu]("http://www.medibuntu.org") repositories

---

### Post by johnthemong on 2007-11-07
That's sorted it. Thanks folks. All working fine now.

---

