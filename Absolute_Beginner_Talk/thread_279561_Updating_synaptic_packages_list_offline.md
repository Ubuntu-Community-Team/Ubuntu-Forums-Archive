---
title: "Updating synaptic packages list offline"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ilGaspa on 2006-10-18
Hello everyone :)

I've installed ubuntu on a machine without internet connection, so I'm having a tough time downloading dependancies from packages.ubuntu.com and installing them manually. 

I know that is possible to use synaptic to generate a list/script of the dependancies of the applications you mark for install, and this would be great... I could mark, for example, gnucash, generate the script and download all packages from another pc with internet connection...

The problem is that, before doing so, i must refresh synaptic package list on the pc without internet connection, and I don't know how to do so!

Anyone knows a way to
1 download packages list from the repositories manually
2 put them in the correct apt/synaptic folder
3 refresh the synaptic lists using the downloaded ones

this way, gnucash will show up in the universe repository, I'll be able to mark it and to choose "create download script" (i don't remember the name, but this option is in the first synaptic menu)

Thanks :)

PS My ubuntu release is dapper

---

### Post by ReaderRat on 2006-10-18
Repositories - All You Need To Know
          [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Repositories - Adding Extra:
          [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

Repository (Open & Edit List of Repos)
          ```
gedit /etc/apt/sources.list
```

---

### Post by uthpalawe on 2006-11-29
I am also having this same problem. I looked at the resources listed but found no way. If you solved your problem pls let me know  how

---

### Post by CatKiller on 2006-11-29
I believe that the package list gets stored at /var/lib/apt/lists, although I don't really know enough about how repositories work to tell you how that would be useful.

Potentially, and this is definitely speculative, you could download the Packages.gz from the repositories and manually extract it to the appropriately named file in that directory.

---

### Post by rpradeep on 2006-11-30
[http://ubuntuforums.org/showthread.php?t=34113&highlight=sources+list](http://ubuntuforums.org/showthread.php?t=34113&highlight=sources+list)

---

### Post by uthpalawe on 2006-11-30
I think the article explains how to get around this. I got a bunch  of very useful answers for my questions and the community is very helpful. I wonder when I will be able to answer some questions here so I can give something too. It is Ubuntu all about.

---

