---
title: "Uninstall JRE java"
date: 2005-06-10
forum: Apple PPC Users
---

### Post by mikelegurra on 2005-06-10
hi,

i installed JRE following the instructions given at ubuntuguide ([http://powerpc.ubuntuguide.org/#jre)](http://powerpc.ubuntuguide.org/#jre)).

after that all my mozilla based browsers crash when i try to access some sites.
i know this is a newbie question because i'm a newbie ( ;-) ). can someone help ?

as i don't really use java, how do i uninstall it ??

thanks for any help.

---

### Post by bored2k on 2005-06-10
sudo rm -rf /usr/java
sudo rm -rf -fs /usr/java/IBMJava2-ppc-142/jre/bin/java
sudo rm -rf /usr/java/IBMJava2-ppc-142/jre/bin/javaw

---

### Post by mikelegurra on 2005-06-10
thanks.

i got a 'rm: invalid option -- s' on the second line. i removed the s flag and it worked.
i hope everything is ok now...

---

### Post by bored2k on 2005-06-10
[QUOTE=mikelegurra]thanks.

i got a 'rm: invalid option -- s' on the second line. i removed the s flag and it worked.
i hope everything is ok now...[/QUOTE]
 Yes it was a mistake. It's sudo rm -rf

---

