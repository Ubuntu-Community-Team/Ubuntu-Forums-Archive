---
title: "Install my VFD"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Duffasaurus on 2007-10-18
So, Ubuntu hates me, and I can't install in command line (there really should be a better tutorial about how to install tgz files) So, I need to install this: [http://venky.ws/projects/imon/#standalone](http://venky.ws/projects/imon/#standalone)    (standalone driver at bottom of page) to get my VFD working. Could anyone just give me some instructions on how to go about doing this?

---

### Post by llamakc on 2007-10-18
You need to satisfy the prerequisites. You can do that by opening a Terminal

APPLICATIONS | ACCESSORIES | TERMINAL

and typing:

sudo apt-get install linux-headers-`uname -r`

Next, download the source for the imon vfd kernel driver (module).

When you get that part done, cd to /usr/src

cd /usr/src

And let us know when you're ready for the rest.

---

### Post by Duffasaurus on 2007-10-18
> **llamakc said:**
> You need to satisfy the prerequisites. You can do that by opening a Terminal

APPLICATIONS | ACCESSORIES | TERMINAL

and typing:

sudo apt-get install linux-headers-`uname -r`

Next, download the source for the imon vfd kernel driver (module).

When you get that part done, cd to /usr/src

cd /usr/src

And let us know when you're ready for the rest.
Kk, did that. My terminal now reads "alex@alex-desktop:/usr/src$ "

---

### Post by llamakc on 2007-10-18
You should now see a directory in there called linux-headers-`uname -r`.

Run the command:

```

uname -r

```

In the terminal. That's the current running version of the Linux kernel. The linux-headers-* package matches it.

Next, we want to create a symlink.

While still in /usr/src, do:

```

sudo ln -s /usr/src/linux-headers-`uname -r` linux

```

IF you run "ls" you'll see a new file in there. If you run "ls -l linux" you'll see something akin to:

```

ken@llamakc 02:55:51:/usr/src$ ls -l linux
lrwxrwxrwx 1 root src 40 2007-10-18 14:55 linux -> /usr/src/linux-headers-2.6.22-14-generic

```

Good. Now you're ready to procede with the install.

Go to the directory where you have the *.tgz that you downloaded.

Follow the directions on the page you linked to.

[LIST]
[*]Untar the tarball (tar xvzf imon_vfd.tgz)
[*]Enter the imon directory (cd imon)
[*]Compile the module (make -C /usr/src/linux SUBDIRS=$PWD modules)
[*]Install the module (make install)
[*]Load the module (modprobe imon_vfd)[/LIST]The commands you want to type are in the parentheses.

---

### Post by Duffasaurus on 2007-10-18
> **llamakc said:**
> You should now see a directory in there called linux-headers-`uname -r`.

Run the command:

```

uname -r

```

In the terminal. That's the current running version of the Linux kernel. The linux-headers-* package matches it.

Next, we want to create a symlink.

While still in /usr/src, do:

```

sudo ln -s /usr/src/linux-headers-`uname -r` linux

```

IF you run "ls" you'll see a new file in there. If you run "ls -l linux" you'll see something akin to:

```

ken@llamakc 02:55:51:/usr/src$ ls -l linux
lrwxrwxrwx 1 root src 40 2007-10-18 14:55 linux -> /usr/src/linux-headers-2.6.22-14-generic

```

Good. Now you're ready to procede with the install.

Go to the directory where you have the *.tgz that you downloaded.

Follow the directions on the page you linked to.

[LIST]
[*]Untar the tarball (tar xvzf imon_vfd.tgz)
[*]Enter the imon directory (cd imon)
[*]Compile the module (make -C /usr/src/linux SUBDIRS=$PWD modules)
[*]Install the module (make install)
[*]Load the module (modprobe imon_vfd)[/LIST]The commands you want to type are in the parentheses.
I'm telling you people...the CLI refuses to work for me. 

alex@alex-desktop:~/Desktop/imon$ make install
depmod
FATAL: Could not open /lib/modules/2.6.20-16-generic/modules.dep.temp for writing: Permission denied

---

### Post by llamakc on 2007-10-18
No, not at all. Those instructions assume somebody is root. Ubuntu uses sudo to perform administrative "root-like" tasks.

Just type:

sudo make install 

and then

sudo modprobe imon_vfd

You can verify that the module is loaded into the running kernel by viewing the copious output of "lsmod", or grep it for the module you're looking for:

lsmod | grep imon

Should be there, and you didn't even have to reboot!

---

### Post by Duffasaurus on 2007-10-18
> **llamakc said:**
> No, not at all. Those instructions assume somebody is root. Ubuntu uses sudo to perform administrative "root-like" tasks.

Just type:

sudo make install 

and then

sudo modprobe imon_vfd

You can verify that the module is loaded into the running kernel by viewing the copious output of "lsmod", or grep it for the module you're looking for:

lsmod | grep imon

Should be there, and you didn't even have to reboot!
Ok, I think he have another problem I failed to notice: (also, same thing happens when I put sudo before the command)

alex@alex-desktop:~/Desktop/imon$ make -C /usr/src/linux SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/alex/Desktop/imon/imon_vfd.o
Assembler messages:
Fatal error: can't create /home/alex/Desktop/imon/.tmp_imon_vfd.o: Permission denied
/home/alex/Desktop/imon/imon_vfd.c:34:26: error: linux/config.h: No such file or directory
/home/alex/Desktop/imon/imon_vfd.c:43:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/alex/Desktop/imon/imon_vfd.c:147: error: unknown field &#8216;owner&#8217; specified in initializer
/home/alex/Desktop/imon/imon_vfd.c:147: warning: initialization from incompatible pointer type
/home/alex/Desktop/imon/imon_vfd.c:162: error: unknown field &#8216;mode&#8217; specified in initializer
/home/alex/Desktop/imon/imon_vfd.c: In function &#8216;send_packet&#8217;:
/home/alex/Desktop/imon/imon_vfd.c:328: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
make[1]: *** [/home/alex/Desktop/imon/imon_vfd.o] Error 2
make: *** [_module_/home/alex/Desktop/imon] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

---

### Post by llamakc on 2007-10-18
Those instructions aren't friendly.

Try moving the imon directory into /usr/src/linux and re-running the make and make install commands with sudo in front of them.

The module failed to build on my system, btw. 

Is support for this device not native now?

---

### Post by Duffasaurus on 2007-10-18
> **llamakc said:**
> Those instructions aren't friendly.

Try moving the imon directory into /usr/src/linux and re-running the make and make install commands with sudo in front of them.

The module failed to build on my system, btw. 

Is support for this device not native now?
So is this like...Jesus hates us? Or it's simply not possible to install in Ubuntu?

---

### Post by kh4nh on 2007-10-18
wow, People are lighting fast
> **Duffasaurus said:**
> I'm telling you people...the CLI refuses to work for me. 

alex@alex-desktop:~/Desktop/imon$ make install
depmod
FATAL: Could not open /lib/modules/2.6.20-16-generic/modules.dep.temp for writing: Permission denied


try ```
sudo make install
```

---

