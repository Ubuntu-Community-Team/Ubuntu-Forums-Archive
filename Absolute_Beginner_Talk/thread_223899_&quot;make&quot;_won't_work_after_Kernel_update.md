---
title: "&quot;make&quot; won't work after Kernel update"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by f_s on 2006-07-27
Hi

I installed all available updates incl. Kernel update x.26. Now "make" doesn't work anymore, giving several errors.

How do I have to update "make" to get it to work with the new kernel?


regards

F

---

### Post by OpsVentus on 2006-07-27
Hello F,

Make sure you got "build-essential" installed.
If it still gives error, please list them here.

Cheers,
Bart.

---

### Post by f_s on 2006-07-27
Hey Bart

"make" worked splendid before the kernel update; seems like with the new kernel there are e.g. some missing directories; do I have to reinstall the build-essentials after a kernel upgrade?

Regards

F

---

### Post by philippe_carlo on 2006-07-27
Post the errors, please!

---

### Post by OpsVentus on 2006-07-27
F,
you can try to reinstall build-essential.
If it's still not working, post the errors.

Cheers,
Bart.

---

### Post by f_s on 2006-07-27
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/RT73_Linux_STA_Drv1.0.3.6/Modu le modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Schluss.
make: *** [all] Fehler 2

---

### Post by moma on 2006-07-27
Try this:

Install kernel-headers
$ sudo apt-get install --reinstall linux-headers-$(uname -r)

// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")


BTW: Why do you run 386 kernel?
A 686 kernel (linux-image-2.6.15-26-686) will get more out of the iron and be slightly faster -- but only if you have a good 686 compatible cpu/machine. Pentium II or better I think.

$ uname -r

---

### Post by f_s on 2006-07-27
686/386 kernel? hm actually don't know. running on PIII with 866Mhz. Simply installed Ubunut from live CD, never got asked to use another kernel. Is that something for experienced users? I'm just glad the system is still working after compiling and installing the ra73 driver.
At least I see no option in the boot menu to use a 686 kernel
But right, it's in fact slower than XP. Still fast enough for me 

Regards

F

---

### Post by moma on 2006-07-27
You got the driver compiled. Well done.

Yes, Ubuntu always installs 386 kernel and that's a good default choice.
I run 2.6.15-26-k7 because it (the K7) is optimized for this box's AMD Athlon CPU.

Anyway, if you're happy with 386, don't change anything.

More about this issue here:
[http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")

---

