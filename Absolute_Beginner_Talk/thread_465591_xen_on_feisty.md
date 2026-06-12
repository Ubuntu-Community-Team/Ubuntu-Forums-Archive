---
title: "xen on feisty"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by m_atif on 2007-06-05
Hi, I think i have installed xen 3.0.3 on my dell optiplex 745 system. Now once i try to install guest os using xen-tools, I am getting error 
E: Failed getting release file http:// <what ever address of mirror i give>>

I have checked all the mirrors that i have tried, they all have release files. I tried to install fiesty, dapper. 

I don't think this is a xen problem as i have searched their forums. I believe that this is mainly  due to my incompetency :(

can anyone enlighten me what can be the cause of this error?

---

### Post by arkham on 2007-06-06
first off, I generally use the manual method because it is more flexible in terms of what you can install but I see the attraction in things like xen-tools....

How have you got your /etc/xen-tools/xen-tools.conf set up?

Some things to check:

debootstrap=1
mirror=http://us.archive.ubuntu.com/ubuntu/
dist=dapper

oh, and make sure debootstrap is installed.....even try testing it on a temp directory like this:

```
debootstrap dapper /my/temp/folder http://us.archive.ubuntu.com/ubuntu/
```

feisty is not supported as yet by xen-tool, one of the reasons I do it myself....

---

### Post by m_atif on 2007-06-22
Sorry, I went away for a while (actually 1 week)

anyways, the same problem persists. I can install using the exactly same process on other machine. I think it is more of a hardware problem. I am using EM6400 dual core processor. The same thing works with AMD Opteron 250's (but they do not support hardware virtualization). :(

---

