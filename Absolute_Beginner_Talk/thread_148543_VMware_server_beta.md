---
title: "VMware server beta"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by gaby PR on 2006-03-22
Somebody here that have installed VMware server bete in Ubuntu 5.10.  I already downloaded and descompressed the file.  But I dont know how to install it.  Any help will be appreciated.

---

### Post by jmcwb on 2006-03-25
have a look at [http://ubuntuforums.org/showthread.php?t=141194&highlight=vmware+server](http://ubuntuforums.org/showthread.php?t=141194&highlight=vmware+server)

---

### Post by gaby PR on 2006-03-25
I followed the instructions of the link you provided.  But the following error show:

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Server cannot work in such configuration. Please either recompile your kernel
with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl with
CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by gaby PR on 2006-03-26
[QUOTE=gaby PR]I followed the instructions of the link you provided.  But the following error show:

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Server cannot work in such configuration. Please either recompile your kernel
with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl with
CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/QUOTE]
need this

---

