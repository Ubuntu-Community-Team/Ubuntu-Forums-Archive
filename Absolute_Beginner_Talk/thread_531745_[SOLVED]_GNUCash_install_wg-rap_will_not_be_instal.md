---
title: "[SOLVED] GNUCash install: wg-rap will not be installed"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by rahimveron on 2007-08-21
hi guys
i wanted to install GNUCash from Add/Remove but i got an error and was told to install it through Synaptic. I did that but there the error was that "g-wrap will not be installed".
I guess g-wrap is the dependencies of gnucash. So i searched for g-wrap and selected it but it shows another dependencies error.
"g-wrap: Depends: libgwrap-runtime0-dev but it is not going to be installed"

I am running Fiesty Fawn with latest Gutsy kernel
Plz help

PS: Sorry for the title typo, it should be g-wrap and not gw-rap.

---

### Post by Ek0nomik on 2007-08-21
Accessories/Terminal:

```
sudo apt-get install gnucash
```

If you get an error, please copy and paste your terminal output into a code box in a reply to this thread.

---

### Post by rahimveron on 2007-08-22
Here is the result of  sudo apt-get install gnucash
```
sudo apt-get install gnucash
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnucash: Depends: g-wrap but it is not going to be installed
E: Broken packages

```

---

### Post by Ek0nomik on 2007-08-22
That's quite the interesting error.

Could you post your sources file?

```
cat /etc/apt/sources.list
```

---

### Post by rahimveron on 2007-08-23
sudo cat /etc/apt/sources.list

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

#deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free 

```

---

### Post by rahimveron on 2007-08-25
COme on guys help me

---

### Post by rahimveron on 2007-08-28
Guys help me please

---

### Post by rahimveron on 2007-08-28
Plz dont ignore me. I need a solution to this dependencies problems

---

### Post by rahimveron on 2007-08-30
Ok after getting ignored i did this and this is what i get:
```
sudo aptitude install gnucash
```

```
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  g-wrap gnucash-common guile-1.6 guile-1.6-dev guile-1.6-slib guile-g-wrap 
  guile-library libcrypt-ssleay-perl libdate-manip-perl libffi4-dev 
  libfinance-quote-perl libgtkhtml3.8-15 libgwrap-runtime0 
  libgwrap-runtime0-dev libhtml-tableextract-perl libncurses5-dev 
  libreadline5-dev linux-libc-dev psfontmgr slib 
The following packages have been kept back:
  libwrap0 
The following NEW packages will be installed:
  g-wrap gnucash gnucash-common guile-1.6 guile-1.6-dev guile-1.6-slib 
  guile-g-wrap guile-library libcrypt-ssleay-perl libdate-manip-perl 
  libffi4-dev libfinance-quote-perl libgtkhtml3.8-15 libgwrap-runtime0 
  libgwrap-runtime0-dev libhtml-tableextract-perl libncurses5-dev 
  libreadline5-dev linux-libc-dev psfontmgr slib 
0 packages upgraded, 22 newly installed, 0 to remove and 1 not upgraded.
Need to get 9853kB/13.5MB of archives. After unpacking 57.2MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6.1-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-headers-2.6.22-9-generic
openoffice.org-base
openoffice.org-calc
openoffice.org-core01
openoffice.org-core02
openoffice.org-core04u
openoffice.org-core05
openoffice.org-core05u
openoffice.org-core09
openoffice.org-core10
openoffice.org-gnome-integration
openoffice.org-graphicfilter
openoffice.org-impress
openoffice.org-kde-integration
openoffice.org-math
openoffice.org-onlineupdate
openoffice.org-pyuno
openoffice.org-testtool
openoffice.org-writer

Downgrade the following packages:
libc6 [2.6.1-0ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]
libc6-i686 [2.6.1-0ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]

```

---

### Post by rahimveron on 2007-09-13
OK solved it: I just downgraded the following packages through Synaptic:
libc6 [2.6.1-0ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]
libc6-i686 [2.6.1-0ubuntu1 (now) -> 2.5-0ubuntu14 (feisty)]
and uninstalled openoffice.org 2.2 completely.
Then i installed GNUCash and then re-installed Oo.org.

One gripe nobody here told me about the downgrade option.

---

