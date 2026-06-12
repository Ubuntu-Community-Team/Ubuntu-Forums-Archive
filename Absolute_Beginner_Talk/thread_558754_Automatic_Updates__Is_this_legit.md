---
title: "Automatic Updates:  Is this legit?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by BertP on 2007-09-24
I found this install request on my machine this morning:

app-install-Data-Commercial
Application Installer (data files for commercial applications)
From Version 7.2 to 7.3 (Size 30 KB)

I know this might sound paranoid but I am suspicious that the automatic installer would need this update  on a stable release,  Is this legit?

I am very new to Ubuntu and Linux  and so I haven't yet grown accustom to the update system, but it does strike me that the automatic update system would be a natural target for a hacker to exploit

---

### Post by por100pre1 on 2007-09-24
Those are data files for commercial applications shown in Add/Remove. It is legit. BTW, Do you have the Canonical repository in sources.list?

---

### Post by master_kernel on 2007-09-24
They're legit. Don't worry.

---

### Post by BertP on 2007-09-24
Thanks for the reassurance guys.


> **por100pre1 said:**
>   BTW, Do you have the Canonical repository in sources.list?

yes,  I have all checked except the  Source Code repository.

---

### Post by por100pre1 on 2007-09-24
> **BertP said:**
> Thanks for the reassurance guys.

yes,  I have all checked except the  Source Code repository.

I mean this one:

```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

It has Real Player, Opera and some other supported commercial software. Try it if you want. :)

---

### Post by BertP on 2007-09-25
Thanks!

---

### Post by hyper_ch on 2007-09-25
The update/repository system works like this:

You add trusted repositories to your sources.list and you import the GPG key files to authenticate them.

So when updates arrive it will be only from those repositories and if something is fishy, like some DNS rerouting to another server, the GPG key will tell you it's unauthenticated...

So basically what you download is all good - however there might be a chance that there was a breakin at the repository and that there were packages altered by hackers... this could happen but I haven't heard of it so...

---

