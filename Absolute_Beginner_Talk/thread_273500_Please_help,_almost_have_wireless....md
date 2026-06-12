---
title: "Please help, almost have wireless..."
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by DavidPM on 2006-10-08
Hi All,

I've been following steps outlined in a HOWTO on setting up my USB wireless device.

However I'm having trouble with the basic things that these HOWTOs tend to over look.

The HOWTO says, go to 'nidswrapper' folder and do this:

sudo make uninstall
make
sudo make install

but I get this...


sudo make uninstall:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1

make:

make -C driver
make[1]: Entering directory `/home/david/Desktop/ndiswrapper-files/ndiswrapper-1.21/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/david/Desktop/ndiswrapper-files/ndiswrapper-1.21/driver'
make: *** [all] Error 2

sudo make install:

make -C driver install
make[1]: Entering directory `/home/david/Desktop/ndiswrapper-files/ndiswrapper-1.21/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/david/Desktop/ndiswrapper-files/ndiswrapper-1.21/driver'
make: *** [install] Error 2


Does anyone know how I get round this?

Many thanks

---

### Post by dmizer on 2006-10-08
can you please link to the howto you were following?

---

### Post by DavidPM on 2006-10-08
> **dmizer said:**
> can you please link to the howto you were following?

I would do but the forums are being so slow it will take ages to find again - I have a print out. It's from Java Jake!

I suspect it's something to do with the Linux-headers but I downloaded them, installed them and still the same errors.

It seems like lots of things rely on lots of other things and I don't have a clue what to do!

Is it possible you can tell from the errors what's wrong?

In the HOWTO it asked me to install cpp gcc build-essential linux-headers which I believe I have now..

Many thanks

---

### Post by dmizer on 2006-10-08
okay ... how about some specifics about your usb adapter?

manufacture name, model name/number, any version numbers if applicable ...

---

