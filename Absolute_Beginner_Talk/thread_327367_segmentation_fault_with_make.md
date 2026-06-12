---
title: "segmentation fault with make"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by frozndevl on 2006-12-29
I am attempting to install wxGDK, it's a requirement for an application. I can run the ./configure just fine, but when I attempt to run the 'make' I get a segmentation fault. I'm so new to this I don't even know what information is needed to help remedy this. 

All I can say is that I am running 6.10 desktop through VMware Server.

---

### Post by angkor on 2006-12-29
Can you post the exact error message?

---

### Post by frozndevl on 2006-12-29
Here is the output on the initial 'make' command and a 'make --debug' command.

```
todd@todd-desktop:~/wxGTK-2.8.0$ make
Segmentation fault
todd@todd-desktop:~/wxGTK-2.8.0$ make --debug
GNU Make version 3.75, by Richard Stallman and Roland McGrath.
Copyright (C) 1988, 89, 90, 91, 92, 93, 94, 95, 96
        Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

Report bugs to <bug-gnu-utils@prep.ai.mit.edu>.

Reading makefiles...
Reading makefile `Makefile'...
Segmentation fault
todd@todd-desktop:~/wxGTK-2.8.0$ 

```

---

### Post by angkor on 2006-12-29
Strange bug. Don't know how to fix that. But there are .debs available for the wxGTK version you want to install.

[From here:]("http://www.wxwidgets.org/downloads/#latest_stable") 

```
Binaries

    * wxGTK Ubuntu packages for 2.8.0 are available. To use them please add

          deb http://apt.tt-solutions.com/ubuntu/ dapper main

      (or edgy instead of dapper if you use that release) to your /etc/apt/sources.list file and add the public key used for signing wxWidgets packages to the list of keys trusted by apt using the command

          curl http://www.tt-solutions.com/vz/key.asc | apt-key add -

      and run apt-get update. You can then use
      apt-cache search --names-only wx\*2.8 command to see the available packages.

      Please notice that Ubuntu packages are only currently available for Dapper x86 and Edgy amd64 architectures.

```

You could try installing a dapper .deb to see if it works.

You can see or download the available packages [here]("http://apt.tt-solutions.com/ubuntu/dists/dapper/main/binary-i386/").

Download the package and double click to install.

---

### Post by frozndevl on 2006-12-29
I have already given that a try. And when attempting to test out the install as per the install.txt of my application, it doesn't work.

> If wxGTK is correctly installed on your system, you should be able to execute the command wx-config from any directory:
athropos@ruby$ wx-config --list

Default config is gtk2-unicode-release-2.6
Default config will be used for output
Alternate matches:
  gtk2-unicode-debug-2.6

> todd@todd-desktop:/etc$ wx-config --list
bash: wx-config: command not found
todd@todd-desktop:/etc$ 


---

