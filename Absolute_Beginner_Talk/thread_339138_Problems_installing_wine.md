---
title: "Problems installing wine"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by CT Husky on 2007-01-15
Hi. Total newbie here.  Put together a new machine recently, and am determined to keep it Windows-free.  A challenge for me, since I don't know that much about computers.  But I'm learning!

Got Ubuntu 6.06 up and running several days ago, and things are going well (i.e., I am fumbling through).  

But now I have a problem: I have tried to install Wine, both through the terminal and Automatix, and I get this message:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2007-01-15
Not sure here, but try (in a terminal)

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install wine

With that said, it is easier to convert to Linux native software then install and configure wine ...

What is it you need to run in wine ?

---

### Post by CT Husky on 2007-01-15
Thanks for the advice.  I'll try it.

As to why wine, I was looking to install ies4linux (found at:  [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)), in the hope that then my young kids could play games found at IE-only sites such as disney.com.

Thanks again.

---

### Post by CT Husky on 2007-01-15
Epilogue:

I think the problem is solved.  The issue seems to have been that in an earlier terminal during my attempt to download ies4linux, I typed:


 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe

and:

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

But, since I am running Dapper, not Edgy, this resulted in the above error.

Doh!

Thanks for the help.

---

