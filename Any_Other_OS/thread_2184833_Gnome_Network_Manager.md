---
title: "Gnome Network Manager"
date: 2013-10-30
forum: Any Other OS
---

### Post by ctjxtvgx on 2013-10-30
I'm trying to follow this step by step procedure to install it on my other computer so it can recognize my wireless adapter and get internet access, however, I am very lost as I can't understand almost all of it. The farthest I got was typing in the "apt-get source NetworkManager.0.9.0.tar.bz2" and that came up with the message E: You must put some "source" URIs in your sources.list. I have no idea what that means. Could someone guide me in what the manual is saying?

[https://projects.gnome.org/NetworkManager/](https://projects.gnome.org/NetworkManager/)
Install Manual:

 The simplest way to compile this package is:


  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.


     Running `configure' might take a while.  While running, it prints
     some messages telling which features it is checking for.


  2. Type `make' to compile the package.


  3. Optionally, type `make check' to run any self-tests that come with
     the package, generally using the just-built uninstalled binaries.


  4. Type `make install' to install the programs and any data files and
     documentation.  When installing into a prefix owned by root, it is
     recommended that the package be configured and built as a regular
     user, and only the `make install' phase executed with root
     privileges.


  5. Optionally, type `make installcheck' to repeat any self-tests, but
     this time using the binaries in their final installed location.
     This target does not install anything.  Running this target as a
     regular user, particularly if the prior `make install' required
     root privileges, verifies that the installation completed
     correctly.


  6. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.


  7. Often, you can also type `make uninstall' to remove the installed
     files again.  In practice, not all packages have tested that
     uninstallation works correctly, even though it is required by the
     GNU Coding Standards.


  8. Some packages, particularly those that use Automake, provide `make
     distcheck', which can by used by developers to test that all other
     targets like `make install' and `make uninstall' work correctly.
     This target is generally not run by end users.

---

### Post by christopher-lees on 2013-11-05
1. The ability to recognise wireless devices and load an appropriate driver, is the job of the kernel. Linux Mint provides the Conman wifi manager; it can use any wifi device, as long as a driver has been loaded in by the kernel. Exactly the same as Network Manager.

In other words, if Conman doesn't show any wifi devices or networks, then Network Manager won't either.

2. What device is it, and what version of Linux Mint? If you use the latest Linux Mint you might automatically get a driver for it. Otherwise you may have to see if there's a driver you can download and compile.

3. If you know you need Network Manager, it is in the Linux Mint repositories, because it uses the same repositories as Ubuntu. Install the "network-manager-gnome" package from the Linux Mint software manager or type "sudo apt-get install network-manager-gnome" into the terminal. Ubuntu 12.04 has Network Manager 0.9.4 so I'm sure a later Ubuntu or a later Linux Mint will have a more recent version.

---

