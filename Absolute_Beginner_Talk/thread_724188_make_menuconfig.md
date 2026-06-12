---
title: "make menuconfig"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-14
I have a rather naive question. I installed ubuntu using a CD. I need to do make menuconfig/xconfig, but I cannot find the source! There is no /usr/src/linux directory. :confused: Where do I do it?

Thanks

---

### Post by glennric on 2008-03-14
Are you trying to compile the linux kernel?  What source code do you want to use?  You can get the vanilla kernel source code form the linux kernel archives.  Or you can get the source code for the ubuntu kernel from the repositories.

Why do you need to run make menuconfig?  What is your objective?

---

### Post by seepage87 on 2008-03-14
why do you need to do this?

---

### Post by medha on 2008-03-14
I need to enable block level tracing, in the config. I have the ubuntu server 2.6.22-14 version installed.

---

### Post by glennric on 2008-03-14
It is not as simple as just running "make menuconfig" and enabling that option in the kernel.  You then have to recompile the entire kernel and install the new kernel version.  There are tutorials on how to do this.  Search the forums and the community documentation if you really want to do this.  It is not easy, and certainly not recommended for someone with little experience in linux.

---

### Post by medha on 2008-03-14
Thanks for the advice glenric, though that doesnt answer my question, which is  "where" to do it, not "how" to do it.

---

### Post by shad0w_walker on 2008-03-14
It was mentioned earlier you can download the kernel source from the repos.

---

### Post by glennric on 2008-03-14
What do you mean "where" to do it?

---

### Post by mali2297 on 2008-03-14
[Link]("https://help.ubuntu.com/community/Kernel/Compile")

---

