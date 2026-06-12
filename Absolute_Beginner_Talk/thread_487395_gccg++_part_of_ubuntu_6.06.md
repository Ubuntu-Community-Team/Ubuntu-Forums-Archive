---
title: "gcc/g++ part of ubuntu 6.06?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by davinci_guy on 2007-06-29
Hi everyone,

I'm a newbie to Linux and SW in general, so please be gentle.  I come from the HW world (and i come in peace) and trying to become more familiar to Linux, the tools, applications, the different distributions, etc.  I was wondering if gcc, g++ as well GNU make are part of the Ubuntu distribution?  If not, i'm assuming i need to go to gnu.gcc.org to download?  Is there an archived thread that talks about how to build the tools?  Eventually, i'll need to build the cross compile tools, but baby steps for now.   Like i said, i'm a newbie and i'm still trying to get my head out of the microsoft world.  Many thanks!

---

### Post by kakalaky on 2007-06-29
Ru the following in a terminal to install them.

```
sudo apt-get install build-essential
```

---

### Post by PaulFr on 2007-06-29
I believe it does - but there are a couple of ways to check.

1. In the GUI, use System -> Administration to start the Synaptic Package Manager and there search for gcc. Any packages which have their check box 'checked' are already installed.
2. In a terminal, run **aptitude search gcc** to show you all packages that are associated with gcc. Any package that shows up with an **i** as the first character is an installed package.

To see more details of any installed package,
1. In the GUI select the row of the package, right click and select Properties menu - this brings up a dialog containing details.
2. In the terminal, run **aptitude show <package_name>** (BTW, <package_name> has to be exact.

Hope this helps, and welcome to Ubuntu :-)

---

