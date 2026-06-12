---
title: "Linux from scratch"
date: 2011-10-21
forum: Any Other OS
---

### Post by andyzammy on 2011-10-21
Hi,

I'm looking to build me a LFS. However, with the recent outage of kernel.org I'm unable to find the required packages from the site. Does anybody know where I could get them from? I'd like to get the exact version numbers listed in the latest stable book, so I can do it "by the book" heh.

Thanks,

Andy

---

### Post by kaldor on 2011-10-21
Github :)

[https://github.com/torvalds/linux](https://github.com/torvalds/linux)

---

### Post by JDShu on 2011-10-21
kernel.org has been back up for a while now.

---

### Post by andyzammy on 2011-10-21
I can get the kernel just fine (module init too), but it looks like that's the only thing kernel.org hosts now. 

[http://www.linuxfromscratch.org/lfs/view/stable/chapter03/packages.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter03/packages.html)

This is a list of all required packages. I can get the kernel and module init just fine but the rest that live at this domain return 404. I googled the packages appended with :kernel.org but the top hit was LFS - also the only contents now of [http://kernel.org/pub/linux/utils/](http://kernel.org/pub/linux/utils/) is kernel module init tools.

Can anybody help me find the rest of the kernel.org packages (and patches) please?

---

### Post by JDShu on 2011-10-21
search google for "linux/utils/kbd" for a list of mirrors.

Now, I don't know what the latest status of kbd is, there is likely a reason for its disappearance from the main repo.

---

### Post by andyzammy on 2011-10-22
> **JDShu said:**
> search google for "linux/utils/kbd" for a list of mirrors.

Now, I don't know what the latest status of kbd is, there is likely a reason for its disappearance from the main repo.

thanks for the tip. manually navigating the list of mirror sites on kernel.org is utterly useless.

Thank you for the responses :)

---

### Post by sffvba[e0rt on 2011-10-22
*Thread moved to **Other OS/Distro Talk**.*


404

---

