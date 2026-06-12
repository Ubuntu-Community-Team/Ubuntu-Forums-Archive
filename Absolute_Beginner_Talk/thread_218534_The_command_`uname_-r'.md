---
title: "The command `uname -r'"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by LCC on 2006-07-18
Hi, I am pretty new to linux and there was a command line using uname wich I have to put something instead but I dont know what, is that the linux version or the user, and one more what is the super user? thanks for any hel

---

### Post by starscalling on 2006-07-18
from:
man uname
UNAME(1)                         User Commands                        UNAME(1)

NAME
       uname - print system information

SYNOPSIS
       uname [OPTION]...

DESCRIPTION
       Print certain system information.  With no OPTION, same as -s.

       -a, --all
              print  all  information,  in the following order, except omit -p
              and -i if unknown:

       -s, --kernel-name
              print the kernel name

       -n, --nodename
              print the network node hostname

       -r, --kernel-release
              print the kernel release

       -v, --kernel-version
              print the kernel version

       -m, --machine
              print the machine hardware name

       -p, --processor
              print the processor type or "unknown"

       -i, --hardware-platform
              print the hardware platform or "unknown"

       -o, --operating-system
              print the operating system

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

---

### Post by Ragazzo on 2006-07-18
> **LCC said:**
> Hi, I am pretty new to linux and there was a command line using uname wich I have to put something instead but I dont know what, is that the linux version or the user, and one more what is the super user? thanks for any hel

I don't know if it's a typo in the title but the command is `uname -r`, both are backticks. Super user is not restricted by file permissions and such. You use it with the "sudo" command. Like "sudo rm somefile" would remove somefile if you couldn't do that with your ordinary user.

---

### Post by LCC on 2006-07-18
Thanks

---

