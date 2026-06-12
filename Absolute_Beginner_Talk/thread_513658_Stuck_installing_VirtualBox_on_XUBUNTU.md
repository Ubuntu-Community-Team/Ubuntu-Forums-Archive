---
title: "Stuck installing VirtualBox on XUBUNTU"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by marmaj on 2007-07-30
Hello all!

I am running into a silly problem trying to install VirtualBox on XUBUNTU 7.04 - when it gets to displaying the license terms, I can not say "Yes" to accept the license and continue with the installation.

I use the following command to to start the installation:

sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb

The installation starts OK, but then I get stuck on the screen with the license info - help, please?

Best regards,

-mm-

---

### Post by bodhi.zazen on 2007-07-30
LO: :lolflag:

On that screen use the tab key to select "OK" and the enter key to proceed ...

---

### Post by marmaj on 2007-07-30
> **bodhi.zazen said:**
> LO: :lolflag:

On that screen use the tab key to select "OK" and the enter key to proceed ...

That worked - thanks!

but now I am running into another installation problem, here is what I got in the terminal widow where I tried to install VirtualBox:

dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not installed.
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
[B]
Yet the manual for VirtualBox states:[/B]

Most Linux distributions can be set up simply by installing the right packages.
Normally, these will be the GNU compiler (GCC), GNU Make (make) and pack-
ages containing header files for your kernel. The version numbers of the header
file packages must be the same as that of the kernel you are using.
   – In newer Debian and Ubuntu releases, you must install the right version of
     the linux-headers and if it exists the linux-kbuild package. Current
     Ubuntu releases should have the right packages installed by default.

So I am a little lost...help anyone?

Best regards...

-mm-

---

### Post by bodhi.zazen on 2007-07-30
Open a terminal, type :

```
sudo apt-get install -f
```

This will install the dependencies.

Then re-install Virtualbox

FYI : There is a repository for virtualbox :

[http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host](http://doc.gwos.org/index.php/VirtualBox#Ubuntu_Host)

---

