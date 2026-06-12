---
title: "updating Java fails, even after trying to update installer"
date: 2014-09-01
forum: Any Other OS
---

### Post by ppgrande on 2014-09-01
hello, I know thats going to be a very basic question, but got stucked and do not know how to proceed

I try to update java in a virtual-machine with ubuntu, and as I run 

**sudo apt-get install default-jdk**

I get plenty of 

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.2-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.2-1_all.deb)  404  Not Found [IP: 91.189.92.200 80]

sure it looks like apkget is not update, but as I run 

**sudo apt-get update**

it seems to not update completly, as several lines like this one apear


Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages                                       
  404  Not Found [IP: 91.189.91.14 80]

while the virtualMachine has perfect (or seems) access to internet


what I am doing wrong ?

---

### Post by nerdtron on 2014-09-01
> Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages                                       
  404  Not Found [IP: 91.189.91.14 80] 

Is this ubuntu version 12.10? This is no longer supported and repositories are closed for this version. Please upgrade (reinstall) to a newer version.

---

### Post by ppgrande on 2014-09-03
> **nerdtron said:**
> Is this ubuntu version 12.10? This is no longer supported and repositories are closed for this version. Please upgrade (reinstall) to a newer version.

I believe to be very new ubuntu
just downloaded from [http://www.traffictool.net/vmware/mint14t.html](http://www.traffictool.net/vmware/mint14t.html)

on terminal:
[INDENT][SIZE=2]user@MintVM ~ $ lsb_release -a[/SIZE][/INDENT]
[INDENT][SIZE=2]No LSB modules are available.[/SIZE][/INDENT]
[INDENT][SIZE=2]Distributor ID:	LinuxMint[/SIZE][/INDENT]
[INDENT][SIZE=2]Description:	Linux Mint 14 Nadia[/SIZE][/INDENT]
[INDENT][SIZE=2]Release:	14[/SIZE][/INDENT]
[INDENT][SIZE=2]Codename:	nadia[/SIZE][/INDENT]

---

### Post by sandyd on 2014-09-03
**Moved to Other Operating Sytems and Projects**

---

### Post by nerdtron on 2014-09-03
> **ppgrande said:**
> I believe to be very new ubuntu
just downloaded from [http://www.traffictool.net/vmware/mint14t.html](http://www.traffictool.net/vmware/mint14t.html)

on terminal:[INDENT][SIZE=2]user@MintVM ~ $ lsb_release -a[/SIZE][/INDENT]
[INDENT][SIZE=2]No LSB modules are available.[/SIZE][/INDENT]
[INDENT][SIZE=2]Distributor ID:    LinuxMint[/SIZE][/INDENT]
[INDENT][SIZE=2]Description:    Linux Mint 14 Nadia[/SIZE][/INDENT]
[INDENT][SIZE=2]Release:    14[/SIZE][/INDENT]
[INDENT][SIZE=2]Codename:    nadia[/SIZE][/INDENT]

Mint 14 is based on Ubuntu 12.10 which is no longer supported.
Linux Mint's current version is now Mint 17.
Please download a new version.

Donwload link:
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

All are Linux Mint 17, with just different desktop environments.

---

### Post by ppgrande on 2014-09-04
Thanks for the respose

why should somebody think that Mint 14 is not on Ubuntu 14 ??

thanks a lot !!

---

### Post by coffeecat on 2014-09-04
> **ppgrande said:**
> 
why should somebody think that Mint 14 is not on Ubuntu 14 ??


Because it isn't. Linux Mint may be derived from Ubuntu but it is not Ubuntu. Neither is it one of the recognised family of Ubuntu "flavours". 

[http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives)

You are welcome to ask Linux Mint questions, but in the correct section, which is here.

---

### Post by nerdtron on 2014-09-04
> **ppgrande said:**
> Thanks for the respose

why should somebody think that Mint 14 is not on Ubuntu 14 ??

thanks a lot !!

Because Mint numbers it releases increamentally (13, 14, 15, 16, 17) while Ubuntu numbers it releases using Year and Month of release (12.04, 12.10, 13.04, 13.10, 14.04).

Somebody who uses Linux Mint (or any operating system in general) should at least read about what version they are installing. See the bottom entry here [http://www.linuxmint.com/rel_nadia_whatsnew.php](http://www.linuxmint.com/rel_nadia_whatsnew.php)
Clearly it says Ubuntu 12.10, which is END-OF-LIFE, no longer supported.

---

