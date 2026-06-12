---
title: "VMware problem - it worked - now it doesnt"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by HyperX on 2006-01-11
I get the following error when running vmware config (vmware worked, but on the newest kernel it doesn't - if i load in previous kernel, i can get it working again)
---start
Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "make" program on your machine.  Please make sure it is installed.
Do you want to specify the location of this program by hand?
[yes]
--end

Can someone tell me what to do? How do I get make on my machine... please...

---

### Post by MartinG on 2006-01-11
make is part of the build-essential package, so ...```
sudo apt-get install build-essential
```You may next get a complaint about gcc versions, *in which case* you will also need to install gcc-3.4, and then enter ```
export CC=gcc-3.4
```before running vmware-config.pl.

---

### Post by HyperX on 2006-01-11
OK I installed the essentials, and you are right, I got the gcc complaint. So I used the export CC command. It all seemed fine, but then I got this:


In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]         

Help?? I feel I am so close, yet so far away....

---

### Post by MartinG on 2006-01-11
Oops, I overlooked that (or assumed too much :( )  You also need to install the kernel headers that match your running kernel, as the message implies.

The one-step way is to do```
sudo apt-get install linux-headers-`uname -r`
```If you're not familiar with this, the command <uname -r> tells you your kernel version (try it), and the use of the back-ticks transfers the result into the apt-get line; alternatively, you can use synaptic (search for "linux-headers", and be sure to pick the correct package for the running kernel).

Once done you'll need to run "export CC=gcc-3.4" again before the vmware configuration, as it's not "sticky".

---

### Post by HyperX on 2006-01-11
Thanks! That did it! Got VMware working again!!

---

