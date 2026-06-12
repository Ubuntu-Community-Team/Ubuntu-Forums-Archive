---
title: "Sleep don't work with external mouse"
date: 2005-10-04
forum: Apple PPC Users
---

### Post by open_flax on 2005-10-04
Hello 
i see that when i use a external mouse a sleep don't work infact when resume my ibook i see a black screen. Have you a solution?
thacks

---

### Post by craks on 2005-10-04
[QUOTE=open_flax]Hello 
i see that when i use a external mouse a sleep don't work infact when resume my ibook i see a black screen. Have you a solution?
thacks[/QUOTE]
update the kernel, and most time you will get fine, but still some time will cause kernel panic.
note:if the external mouse doesn't work after resume, you can just run the following command:
sudo modprobe -r ehci_hcd

---

