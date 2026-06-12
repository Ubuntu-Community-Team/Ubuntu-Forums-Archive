---
title: "Installing software using dpkg causes problems later?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-01-07
Hello All

I'm using Xubuntu 6.06 on a lowish spec laptop.

I used the information at

[http://ubuntuforums.org/showthread.php?t=318865](http://ubuntuforums.org/showthread.php?t=318865)

to install the latest OpenOffice by converting the RPMs to DEBs using alien and then running dpkg -i on the resulting debs. It works and I get OpenOffice 2.1, having previously installed OpenOffice from the repository and uninstalled it using Synaptic as suggested in the thread above.

When I then decided to install gnuplot (a command line package that draws mathematical graphs), I was rewarded with the following....

```
keith@cygnus:~$ sudo aptitude install gnuplot
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  bsh libcurl3 libhsqldb-java libicu34 libjaxp1.2-java libjline-java
  libmdbtools libservlet2.3-java libstlport4.6c2 libxalan2-java
  libxerces2-java libxmlsec1-nss libxmlsec1-openssl libxt-java
  openoffice.org-base openoffice.org-calc openoffice.org-draw
  openoffice.org-impress openoffice.org-math openoffice.org-writer
The following NEW packages will be automatically installed:
  gnuplot-nox gnuplot-x11 libgd2-noxpm
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following NEW packages will be installed:
  gnuplot gnuplot-nox gnuplot-x11 libgd2-noxpm
0 packages upgraded, 4 newly installed, 20 to remove and 2 not upgraded.
Need to get 1073kB of archives. After unpacking 62.1MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://security.ubuntu.com dapper-security/main libgd2-noxpm 2.0.33-2ubuntu5.1 [192kB]
Get:2 http://archive.ubuntu.com dapper/universe gnuplot-nox 4.0.0-2.1 [701kB]
Get:3 http://archive.ubuntu.com dapper/universe gnuplot-x11 4.0.0-2.1 [178kB]
Get:4 http://archive.ubuntu.com dapper/universe gnuplot 4.0.0-2.1 [1388B]
Fetched 1073kB in 2s (429kB/s)
(Reading database ... 95157 files and directories currently installed.)
Removing bsh ...
Removing libcurl3 ...
Removing libhsqldb-java ...
Removing libicu34 ...
Removing libxalan2-java ...
Removing libxerces2-java ...
Removing libjaxp1.2-java ...
Removing libjline-java ...
Removing libmdbtools ...
Removing libservlet2.3-java ...
Removing libstlport4.6c2 ...
Removing libxmlsec1-nss ...
Removing libxmlsec1-openssl ...
Removing libxt-java ...
Removing openoffice.org-base ...
Removing openoffice.org-calc ...
Removing openoffice.org-draw ...
Removing openoffice.org-impress ...
Removing openoffice.org-math ...
Removing openoffice.org-writer ...
Selecting previously deselected package libgd2-noxpm.
(Reading database ... 94655 files and directories currently installed.)
Unpacking libgd2-noxpm (from .../libgd2-noxpm_2.0.33-2ubuntu5.1_i386.deb) ...
Selecting previously deselected package gnuplot-nox.
Unpacking gnuplot-nox (from .../gnuplot-nox_4.0.0-2.1_i386.deb) ...
Selecting previously deselected package gnuplot-x11.
Unpacking gnuplot-x11 (from .../gnuplot-x11_4.0.0-2.1_i386.deb) ...
Selecting previously deselected package gnuplot.
Unpacking gnuplot (from .../gnuplot_4.0.0-2.1_all.deb) ...
Setting up libgd2-noxpm (2.0.33-2ubuntu5.1) ...
Setting up gnuplot-nox (4.0.0-2.1) ...

Setting up gnuplot-x11 (4.0.0-2.1) ...
Setting up gnuplot (4.0.0-2.1) ...

```

I then re-installed Open Office from the debs and all seems well. Am I going to have to remove and re-install OpenOffice 2.1 each time I want to add new software? Is there a way of telling aptitude or synaptic/apt-get to ignore OpenOffice 2.1?

Thanks

---

### Post by troymcdavis on 2007-02-05
This might not be the most convenient solution, but you could try building it from source. If that doesn't work, you could try building from source, turning it into a deb with checkinstall, and then installing it. Let me know if you have any questions/successes/problems.

---

### Post by keithpeter on 2007-02-08
Hello troymcdavis

I had thought of this, as software built from source often runs from your home directory and does not change the system

How on earth would I start to build OpenOffice? What lib-dev packages would I need?

---

### Post by Pugwash on 2007-03-29
> **keithpeter said:**
> Hello All

I'm using Xubuntu 6.06 on a lowish spec laptop.

I used the information at

[http://ubuntuforums.org/showthread.php?t=318865](http://ubuntuforums.org/showthread.php?t=318865)

to install the latest OpenOffice by converting the RPMs to DEBs using alien and then running dpkg -i on the resulting debs. It works and I get OpenOffice 2.1, having previously installed OpenOffice from the repository and uninstalled it using Synaptic as suggested in the thread above.

When I then decided to install gnuplot (a command line package that draws mathematical graphs), I was rewarded with the following....

```
keith@cygnus:~$ sudo aptitude install gnuplot
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  bsh libcurl3 libhsqldb-java libicu34 libjaxp1.2-java libjline-java
  libmdbtools libservlet2.3-java libstlport4.6c2 libxalan2-java
  libxerces2-java libxmlsec1-nss libxmlsec1-openssl libxt-java
  openoffice.org-base openoffice.org-calc openoffice.org-draw
  openoffice.org-impress openoffice.org-math openoffice.org-writer
The following NEW packages will be automatically installed:
  gnuplot-nox gnuplot-x11 libgd2-noxpm
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following NEW packages will be installed:
  gnuplot gnuplot-nox gnuplot-x11 libgd2-noxpm
0 packages upgraded, 4 newly installed, 20 to remove and 2 not upgraded.
Need to get 1073kB of archives. After unpacking 62.1MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://security.ubuntu.com dapper-security/main libgd2-noxpm 2.0.33-2ubuntu5.1 [192kB]
Get:2 http://archive.ubuntu.com dapper/universe gnuplot-nox 4.0.0-2.1 [701kB]
Get:3 http://archive.ubuntu.com dapper/universe gnuplot-x11 4.0.0-2.1 [178kB]
Get:4 http://archive.ubuntu.com dapper/universe gnuplot 4.0.0-2.1 [1388B]
Fetched 1073kB in 2s (429kB/s)
(Reading database ... 95157 files and directories currently installed.)
Removing bsh ...
Removing libcurl3 ...
Removing libhsqldb-java ...
Removing libicu34 ...
Removing libxalan2-java ...
Removing libxerces2-java ...
Removing libjaxp1.2-java ...
Removing libjline-java ...
Removing libmdbtools ...
Removing libservlet2.3-java ...
Removing libstlport4.6c2 ...
Removing libxmlsec1-nss ...
Removing libxmlsec1-openssl ...
Removing libxt-java ...
Removing openoffice.org-base ...
Removing openoffice.org-calc ...
Removing openoffice.org-draw ...
Removing openoffice.org-impress ...
Removing openoffice.org-math ...
Removing openoffice.org-writer ...
Selecting previously deselected package libgd2-noxpm.
(Reading database ... 94655 files and directories currently installed.)
Unpacking libgd2-noxpm (from .../libgd2-noxpm_2.0.33-2ubuntu5.1_i386.deb) ...
Selecting previously deselected package gnuplot-nox.
Unpacking gnuplot-nox (from .../gnuplot-nox_4.0.0-2.1_i386.deb) ...
Selecting previously deselected package gnuplot-x11.
Unpacking gnuplot-x11 (from .../gnuplot-x11_4.0.0-2.1_i386.deb) ...
Selecting previously deselected package gnuplot.
Unpacking gnuplot (from .../gnuplot_4.0.0-2.1_all.deb) ...
Setting up libgd2-noxpm (2.0.33-2ubuntu5.1) ...
Setting up gnuplot-nox (4.0.0-2.1) ...

Setting up gnuplot-x11 (4.0.0-2.1) ...
Setting up gnuplot (4.0.0-2.1) ...

```

I then re-installed Open Office from the debs and all seems well. Am I going to have to remove and re-install OpenOffice 2.1 each time I want to add new software? Is there a way of telling aptitude or synaptic/apt-get to ignore OpenOffice 2.1?

Thanks

I'm having the exact same problem on xubuntu on my parent's computer. Anybody solved this yet?

---

