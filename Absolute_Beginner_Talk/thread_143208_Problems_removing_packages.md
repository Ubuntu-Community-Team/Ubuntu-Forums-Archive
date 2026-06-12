---
title: "Problems removing packages"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by garthoid on 2006-03-12
Hi,

I appear to have some phantom packages that are listed as installed but I cannot remove them (either with synaptic or apt-get) because I get folder does not exist errors.

Below is an attempt to remove zope-backtalk (there are other zope packages) using apt-get. There error is the same if I use synaptic.

Any ideas? 

root@owl:~ # apt-get remove zope-backtalk
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  zope-backtalk
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
11 not fully installed or removed.
Need to get 0B of archives.
After unpacking 426kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 85104 files and directories currently installed.)
Removing zope-backtalk ...
dzhandle prerm-product: product directory doesn't exist: `/usr/share/zope/Produc
ts/BackTalk'
dpkg: error processing zope-backtalk (--remove):
 subprocess pre-removal script returned error exit status 1
dzhandle postinst-product: product directory doesn't exist: `/usr/share/zope/Pro
ducts/BackTalk'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zope-backtalk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Mustard on 2006-03-12
Did you delete any folders or files manually before attempting to remove with apt-get?  I'm just wondering where they went to.

---

### Post by garthoid on 2006-03-12
No. I did not remove packages manually.

I did attempt a remove of Zope 2.7 with Synaptic at one stage and this I think is were my problems began.

Would a reinstall help?

G

---

### Post by knalle on 2006-03-12
try

```
sudo dpkg --list|grep zope
``` and see if its listed as **rc** or something

if so, try ```
sudo dpkg --purge zope-backtalk
```

---

### Post by garthoid on 2006-03-12
1. dpkg --list | grep backtalk

root@owl:/etc # dpkg --list|grep zope | grep backtalk
**rF**  zope-backtalk                          0.3-5ubuntu1                       A
document annotation, editing, and producti

2. dpkg --purge zope-backtalk

root@owl:/etc # dpkg --purge zope-backtalk
(Reading database ... 87541 files and directories currently installed.)
Removing zope-backtalk ...
dzhandle prerm-product: product directory doesn't exist: `/usr/share/zope/Products/BackTalk'
dpkg: error processing zope-backtalk (--purge):
 subprocess pre-removal script returned error exit status 1
dzhandle postinst-product: product directory doesn't exist: `/usr/share/zope/Products/BackTalk'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zope-backtalk

---

### Post by garthoid on 2006-03-12
So far the best way I have found to dig myself out of this is to install the complaining packages on another box, tar up the /usr/share/zope/<packagename> folder, copy it to the complaining install, and extract it. 

Then I can remove the phantom package.

---

### Post by Mustard on 2006-03-12
[QUOTE=garthoid]So far the best way I have found to dig myself out of this is to install the complaining packages on another box, tar up the /usr/share/zope/<packagename> folder, copy it to the complaining install, and extract it. 

Then I can remove the phantom package.[/QUOTE]

That's a very creative solution. :)  I take it it worked?

---

### Post by garthoid on 2006-03-12
[QUOTE=Mustard]That's a very creative solution. :)  I take it it worked?[/QUOTE]
Yes. As crappy as it was it did work. Not sure why I got into the muddle in the first place since I did not manually remove 7 zope based product packages.

If anyone has a more elegant solution I am all ears.

---

