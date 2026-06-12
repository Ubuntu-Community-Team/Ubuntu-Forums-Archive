---
title: "how to install nvidia nforce audio drivers?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by justizz on 2005-12-03
I have Ubuntu 5.04.
Im trying to make America's Army 2.5.0 to work, but it doesnt have sounds. I guess problem is on drivers.

So, I downloaded drivers from [www.nvidia.com](www.nvidia.com).
First,
It printed error and said something about kernel source. I used [that]("http://ubuntuforums.org/showthread.php?t=70905").

Now it says

```
  ERROR:
         If you are using a Linux 2.4 kernel, please make sure
         you either have configured kernel sources matching your
         kernel or the correct set of kernel headers installed
         on your system.

         If you are using a Linux 2.6 kernel, please make sure
         you have configured kernel sources matching your kernel
         installed on your system. If you specified a separate
         output directory using either the "KBUILD_OUTPUT" or
         the "O" KBUILD parameter, make sure to specify this
         directory with the SYSOUT environment variable or with
         the appropriate nvidia-installer command line option.

```

i don't have any idea how to make drivers work :(

---

### Post by justizz on 2005-12-03
when i start americas army from terminal it prints just before AA starts 
"open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0"."

---

