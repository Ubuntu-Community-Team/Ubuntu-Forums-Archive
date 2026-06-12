---
title: "Limewire not working"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2006-08-19
Hi,
I just installed Limewire on 6.06.1 following the instructions on the "Ubuntu Desktop Guide"; downloaded LimeWireLinux.rpm, converted it to deb using 'alien' and then double-clicked and pressed install.  Everything worked fine with no error messages.  I even found the Limewire icon in the Applications>internet menu but when clicked nothing happens!!!

---

### Post by Perfect Storm on 2006-08-19
Looks like you havn't install java 1.5

---

### Post by taurus on 2006-08-19
If you click something and nothing happens, better to run it again from a terminal (Applications -> Accessories -> Terminal) to see exactly what the error message is...

```
limewire
```

---

### Post by rck_hitokiri on 2006-08-19
try to install java as said above you can get it on applications > add/remove programs then click the commercial releases box , then download java. cheers

---

### Post by SteelCore on 2006-08-19
I've checked Synaptic.  Both sun-java5-plugin and sun-java5-jre are installed.  Do I still need sun-java5-jdk?

---

### Post by fakie_flip on 2006-08-19
> **SteelCore said:**
> I've checked Synaptic.  Both sun-java5-plugin and sun-java5-jre are installed.  Do I still need sun-java5-jdk?

NO, JDK is java's developement kit. I doubt you are a java programmer, so you do not need it. You need to tell Ubuntu to which java to use otherwise it will use the gnu java that is not made by Sun. Follow the directions here.

[https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

---

### Post by SteelCore on 2006-08-19
> **fakie_flip said:**
> NO, JDK is java's developement kit. I doubt you are a java programmer, so you do not need it. You need to tell Ubuntu to which java to use otherwise it will use the gnu java that is not made by Sun. Follow the directions here.

[https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b)

YES that worked perfectly.  Thank you very much.

---

### Post by rowanparker on 2006-08-19
You should try Frostwire, it's Limewire without the ads.

---

### Post by pneaveill on 2006-08-19
Was working on similar issues with limewire and found this post. I followed it and it worked. 

Thanks for the time, energy and patience in helping each of us.

P.S. Frostwire does appear to be much faster replacement for limewire (which is about to removed)

---

### Post by fakie_flip on 2006-08-20
You need to do the same thing with Java to get frostwire working. No problem. Many people have helped me, and I should give back to the community too.

---

