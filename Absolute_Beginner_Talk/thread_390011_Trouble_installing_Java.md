---
title: "Trouble installing Java"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Torahteen on 2007-03-21
Hello, I just installed java on one of my ubuntu computers (dapper), and everything worked fine. Now, I'm on another ubuntu computer (also dapper), but when I do "sudo aptitude install sun-java6-jre sun-java6-plugin", I'm told that it couldn't find those packages. I just did the exact same thing on another computer just 20 minutes ago. What's up? I replaced the sources.list with the sources list that's on the Ubuntu Guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories"). Any help is GREATLY appreciated. I know you guys won't let me down :P

---

### Post by an.echte.trilingue on 2007-03-21
Did you remember to sudo aptitude update?

---

### Post by bruce89 on 2007-03-21
Java 1.6 is in the backports repository, you will have to enable it.

> **Torahteen said:**
> I replaced the sources.list with the sources list that's on the Ubuntu Guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories").

The sources.list here is for Edgy, that would bugger up (technical term) any Dapper installation.  Don't copy and paste sources.lists from sites, as they may mess stuff up.

---

### Post by Torahteen on 2007-03-23
Ok, thanks for that bruce, where is a good sources.list for dapper?

---

### Post by zvacet on 2007-03-23
[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

---

### Post by zvacet on 2007-03-23
[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")

Or you can downloaded it with Automatix.


Sorry for double post.

---

