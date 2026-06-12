---
title: "Win puTTY equivalent"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Strider42 on 2007-05-06
Hi,

Can anyone recommend a good Linux equivalent to puTTY?

Thanks in advance.

---

### Post by Scheater5 on 2007-05-06
Well, I'm not entierly sure what puTTY is, but a quick google search seems to indicate SSH may be what you are looking for.  
Also, try [this]("http://linux.softpedia.com/get/System/Networking/PuTTY-347.shtml") site, which is apparently puTTY ported to Linux.

---

### Post by mech7 on 2007-05-06
I saw PUTTY in the Add / Remove so i think it is in the repository.

---

### Post by webdr on 2007-05-06
No need for putty in Linux, just fire off a terminal and use ssh command ;)

If you are more interested in automating and controlling ssh sessions, check out:
[http://sourceforge.net/projects/clusterssh/](http://sourceforge.net/projects/clusterssh/)

---

### Post by steve.horsley on 2007-05-06
Putty is a basic SSH client for Windows. It does a command shell, and can also do TCP forwarding.The Linux equivalent would be to use the command-line SSH client - e.g. open a terminal and type:
**ssh username@hostname**
Use the command **man ssh** for the details.

---

### Post by Strider42 on 2007-05-06
Excellent, thanks all!

Regards
Paul

---

