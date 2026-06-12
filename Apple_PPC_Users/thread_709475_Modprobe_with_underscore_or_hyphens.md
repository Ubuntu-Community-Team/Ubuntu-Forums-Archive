---
title: "Modprobe with underscore or hyphens ???"
date: 2008-02-27
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-27
Ack!  Now I'm confused.  I've been trying to follow the PowerPC Known issues faq that uses hyphens instead of underscores:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

However, when I do
```
lsmod | grep ide_core
```

it shows up, and ide-core does not.

Have I been tearing my hair out with funky hyphens when I should have been using **underscores** all along?

---

### Post by jeffus_il on 2008-02-27
Both will work. that is with modprobe/rmmod but grep will see the difference.

---

### Post by stream303 on 2008-02-27
Looks like I need to learn how to use the thanks button better. :)

Whew!  I often referred others to this document and was about to go into hiding.

---

