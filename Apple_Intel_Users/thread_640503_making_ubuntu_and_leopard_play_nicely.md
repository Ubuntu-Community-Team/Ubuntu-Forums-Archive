---
title: "making ubuntu and leopard play nicely?"
date: 2007-12-14
forum: Apple Intel Users
---

### Post by excalibur313 on 2007-12-14
I have leopard and I just installed ubuntu on a separate partition. Does anyone know of a way to make the two play nicely with each other? I only have one account on each but I would like to be able to access stuff from my users folder on leopard from ubuntu and vice versa. Ideally, it would be amazing if I could figure out a way to keep them synchronized so i could have a more uniform experience. What do you all think? What is the best way to explore into uncharted territory with ubuntu while still keeping os x close at hand?
Thanks!
Stephen

---

### Post by cyberdork33 on 2007-12-14
> **excalibur313 said:**
> I have leopard and I just installed ubuntu on a separate partition. Does anyone know of a way to make the two play nicely with each other? I only have one account on each but I would like to be able to access stuff from my users folder on leopard from ubuntu and vice versa. Ideally, it would be amazing if I could figure out a way to keep them synchronized so i could have a more uniform experience. What do you all think? What is the best way to explore into uncharted territory with ubuntu while still keeping os x close at hand?
Thanks!
Stephen

the easiest way would likely be to create another partition for sharing data, but you can access the OSX files in Ubuntu, and the Ubuntu files in OSX though.

You will run into issues, such as the fact that your userid and groupid is different in osx and ubuntu, so, as far as your OS is concerned, they are different users (even with the same login). linux can read the permissions of the hfs+ filesystem on the OSX side, and thus, you get locked out of things that are "owned" by your osx user. You can change the permissions in OSX and not have an issue. Additionally, if you require write access to your files, then you have to make sure to disable journaling:
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

To access your linux partition in OSX, use the dev version of this tool: [http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)

---

