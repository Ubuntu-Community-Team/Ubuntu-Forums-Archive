---
title: "Kernel from ubuntu CD"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by RJQ on 2007-05-03
Hi all:

I was wondering if it is possible to compile a Kernel from a Ubuntu CD, that is if the resources needed for this task are available inside the CD folders, any thoughts? thanks.

---

### Post by Seisen on 2007-05-03
I am not sure but I know that you at least need to download the kernel from [www.kernel.org]("www.kernel.org")
Here is a link on how to build a new kernel.
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master%20kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master%20kernel")

---

### Post by Jazztux on 2007-05-03
Hi,
I never tried this. I think it's possible, otherwise in the Live CD there aren't all the apps and libraries you need to do that. You have to download the source code of the kernel you want to compile. Next you have to install make, gcc, automake with Synaptic. You can try to untar the code to a directory, go there with the terminal and type:

```
make xconfig
```

Maybe you need other libraries. If you'll give a try, plese post you result. ;)

---

### Post by RJQ on 2007-05-03
Hey Guys thanks for the info

My idea is to skip the downloading the "kernel source" (dial up here) knowing that i have the rest of the "tools" for compilation, i though that may be the source staff can be subtracted from the live CD?? any suggestion? thanks.

---

### Post by Jazztux on 2007-05-03
Kernel source is not on the LiveCD. Otherwise you can try to search it in Synaptic...
But, if you want to build the source of LiveCD kernel, why do you not copy the compiled LiveCD kernel?

---

### Post by mcduck on 2007-05-03
I believe that the build-essentials package (that includes all tools needed for compiling) is on the CD, at least on the Alternate CD. But most likely kernel source is not there so you'll have to download it. Anyway, if yu want to make compiling easier you may want to use the kernel source from Ubuntu repositories, depending on what you wish to accomplish by compiling your own kernel.

---

