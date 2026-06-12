---
title: "Building minimal Linux Distribution"
date: 2015-01-16
forum: Any Other OS
---

### Post by tofiffe on 2015-01-16
So for my assignment I chose building a custom linux distro, which is supposed to be smaller than 10mb, and the only thing it absolutely needs is working 'ls' command, so I've started researching and I've found these tutorials:

[https://sites.google.com/site/4utils/articles/minimal_linux_system/minimal-linux-system-from-scratch](https://sites.google.com/site/4utils/articles/minimal_linux_system/minimal-linux-system-from-scratch)
[https://agentoss.wordpress.com/2011/02/27/how-to-create-a-very-small-linux-system-using-buildroot/](https://agentoss.wordpress.com/2011/02/27/how-to-create-a-very-small-linux-system-using-buildroot/)

folowing the first one, I thought it was pretty easy and I've gotten up to the last thing to do: test it, but when running the test.img in qemu-system-i386 the kernel didn't startup, so I've tried using the grub commands to run it, but it ultimately reached a crashpoint.

Desperate and not knowing what was wrong I've searched for a different tutorial and I've found the second one listed. Again as before the procedure was easy to follow and I've manged to complete the build as before, but again when using "qemu-system-i386 -kernel path/to/kernel" it stops at this screen, which I persume is some kind of a crash: 
[IMG]http://i.imgur.com/MA7awKs.png[/IMG]

I've folowed the tutorials to the letter, some things have moved, but I managed to find them. I'm really desperate about what I'm doing wrong and it seems I'm unable to find out how to fix these errors...

Is is the qemu command? since just using qemu lists packages in which it is installed I was using qemu-system-i386...

---

### Post by Elfy on 2015-01-16
*Thread moved to **Any Other OS**.*

---

### Post by tgalati4 on 2015-01-16
It's forum policy not to assist (too much) with homework assignments.  Tiny Core linux meets the 10 MB size.  I would spend some time looking at how it was built.

[http://distro.ibiblio.org/tinycorelinux/](http://distro.ibiblio.org/tinycorelinux/)

Using a vitual environment to build such an OS confounds the problems you are likely to have.  The guide in the first post used Fedora7 as the build environment.  Are you using Fedora7?

The second tutorial uses Ubuntu 10.10.  Are you using 10.10 as your build environment?

Because of the major changes in the kernel with each new version of Ubuntu or Fedora, the build environment for a given tutorial is only good for that specific version.  TinyCore uses a relatively recent build environment.

---

### Post by tofiffe on 2015-01-17
I know most forums have the "don't do someone's homework" policy, but the error I'm getting on qemu seems to appear on more than one version of the build - even when choosing different styles, also it appears when following the first one, the numbers are different here and there, but I can't seem to find any more information on it...

---

### Post by tgalati4 on 2015-01-17
What base operating system are you using?  Is your hardware 32-bit or 64-bit?  The error looks like a kernel panic, which could be caused by a 32-bit/64-bit mismatch or something else.

---

### Post by tofiffe on 2015-01-17
I'm using Xubuntu 14.04 64bit inside a virtual machine

---

### Post by tgalati4 on 2015-01-17
The vm you are trying to spin up is i386 which is 32-bit.  Perhaps you are missing the 32-bit libraries.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by tofiffe on 2015-01-18
I remember installing the 32-bit compilers and libraries, since it at one point wouldn't compile, also I had some assembly code written in 16-bit that was able to boot in i386 qemu, so I'm guessing this isn't the cause, is there any way qemu could output the errors in an external file, or perhaps allow me to scroll higher to find more information about it?

---

### Post by tgalati4 on 2015-01-18
```
apt-cache policy ia32-libs
```

Try running the 64-bit qemu and see if you get the same errors:  [http://askubuntu.com/questions/138140/how-do-i-install-qemu](http://askubuntu.com/questions/138140/how-do-i-install-qemu)

To increase scrollback, there is a setting in *terminal* that allows you to increase the scrollback buffer:  Edit==>Profile Preferences==>Scrollback.

---

### Post by tofiffe on 2015-01-18
The error using 64 bit qemu seems to be the same, the apt-cache command results in:

> ia32-libs:
  Installed: (none)
  Candidate: (none)
  Version overview: (nothing here)


---

