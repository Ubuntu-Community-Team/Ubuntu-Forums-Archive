---
title: "Error Following Dapper IVTV How To"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by pmurnane on 2006-12-29
Hi All:

I'm trying to get my Hauppauge WinTV PVR-250 working with Dapper 6.06.1.  I've looked around the forums and have googled a few things but haven't been able to find a fix for an error I'm getting following the How To at [https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper) .  Everything works fine until I get to this part:

```
sudo m-a a-i ivtv0.4
```

and the package build (I think) fails.  Here's the first error I found in the module-assistant log file viewer:

/usr/bin/make KVER=2.6.15-27-686 KDIR=/usr/src/linux HP_FWLOAD=1
DEBIAN_MAKE_KPKG=1
make[2]: Entering directory `/usr/src/modules/ivtv0.4'
created ivtv-svnversion.h
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ivtv0.4 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-27-686'[COLOR="Black"][/COLOR]
  CC [M]  /usr/src/modules/ivtv0.4/cx25840-core.o
In file included from /usr/src/modules/ivtv0.4/cx25840-core.c:31:
[COLOR="Red"]/usr/src/modules/ivtv0.4/ivtv-compat.h:87:32: error:
../utils/videodev2.h: No such file or directory[/COLOR]
/usr/src/modules/ivtv0.4/ivtv-compat.h:88:31: error:
../utils/videodev.h: No such file or directory
In file included from /usr/src/modules/ivtv0.4/cx25840-core.c:40:
/usr/src/modules/ivtv0.4/cx25840.h:79: error: syntax error before
&#8216;cx25840_get_v4lstd&#8217;

Here's my kernel info:

```
$ uname -ar
Linux cyclops 2.6.15-27-686 #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006 i686 GNU/Linux
```

Any Advice?

Thanks,
--Phil

PS: I spent about 30 hours getting Fedora Core 6 loaded and Atheros & ATI Radeon drivers running.  I got that far with Dapper in 3 hours -- much better!  Thanks for the distro!

---

### Post by superm1 on 2006-12-29
Okay, i'm wondering if this is a bug with a newer version of the packaging.

Can you try an older ivtv version, grab the debs for your arch here:
[http://people.atrpms.net/~mlimonciello/ivtv_testing/ivtv0.4-source_0.4.5-1_all.deb](http://people.atrpms.net/~mlimonciello/ivtv_testing/ivtv0.4-source_0.4.5-1_all.deb)
[http://people.atrpms.net/~mlimonciello/ivtv_testing/ivtv0.4-utils_0.4.5-1_i386.deb](http://people.atrpms.net/~mlimonciello/ivtv_testing/ivtv0.4-utils_0.4.5-1_i386.deb)

[]("http://dl.ivtvdriver.org/ubuntu/dists/dapper/ivtv/ivtv0.4-utils_0.4.5-1_i386.deb") Install those two debs, and try to rebuild.  If this works, i'll have to sort this out in my dapper box once I get back to it in the next week.

---

### Post by pmurnane on 2006-12-29
Superm1:

> Install those two debs, and try to rebuild.

Thanks -- I'll try it and let you know how it goes.

Appreciatively,
--Phil

---

### Post by pmurnane on 2007-01-04
> **superm1 said:**
> Install those two debs, and try to rebuild.  If this works, i'll have to sort this out in my dapper box once I get back to it in the next week.

Superm1:

When I try to install the second package with Gdebi Package Installer, I get an error:
```
Error: Conflicts with the installed package 'ivtv0.4-utils'
```
but then the child window says "Package 'ivtv0.4-utils_0.4.5-1_i386.deb' was installed".  So was there a problem or wasn't there? :-k 

I started with a fresh install of dapper, then followed the howto until this point:
```
sudo apt-get install ivtv0.4-source devscripts ivtv0.4-utils ivtv-firmware
```
Here I only installed 'devscripts', then installed the two packages you referenced in the order listed.

Thanks Again,
--Phil

---

### Post by superm1 on 2007-01-04
> **pmurnane said:**
> Superm1:

When I try to install the second package with Gdebi Package Installer, I get an error:
```
Error: Conflicts with the installed package 'ivtv0.4-utils'
```but then the child window says "Package 'ivtv0.4-utils_0.4.5-1_i386.deb' was installed".  So was there a problem or wasn't there? :-k 

I started with a fresh install of dapper, then followed the howto until this point:
```
sudo apt-get install ivtv0.4-source devscripts ivtv0.4-utils ivtv-firmware
```Here I only installed 'devscripts', then installed the two packages you referenced in the order listed.

Thanks Again,
--Phil
Phil, 

I setup a dapper install in a VM and am running into the same things.  I'll straighten this out and get back to you in a bit with a solution.

Regards,

Mario

---

### Post by superm1 on 2007-01-04
> **superm1 said:**
> Phil, 

I setup a dapper install in a VM and am running into the same things.  I'll straighten this out and get back to you in a bit with a solution.

Regards,

Mario
Phil,

Okay i think i have this resolved now.  I put a new package up at the ivtv download site.  With the changes I had to make, i'm surprised this ever worked before!  So follow these steps to try it.  You shouldn't need to do a full reinstall, I just uninstalled the old packages in my VM:

1) Remove any and all ivtv0.4 packages
```
sudo apt-get remove ivtv0.4-utils ivtv0.4-source
```

2) Remove any old ivtv0.4 building files
```
sudo rm /usr/src/modules/ivtv0.4 -rf
```

3) Update your package list (assuming you have the dl.ivtvdriver.org/ubuntu repository on your list still - if not, add it first)
```
sudo apt-get update
```

4) Install the new ivtv packages.  Note the name changed, so this is a bit different
```
sudo apt-get install ivtv-source ivtv-utils
```

5) Rebuild the modules per the bulid steps in the wiki page:
```
sudo m-a update,prepare
sudo m-a a-i ivtv
sudo depmod -a
```

---

### Post by pmurnane on 2007-01-05
superm1:

Works great!  In step 4 I had to add ivtv-firmware to the list of modules to install, but other than that it worked like a charm.  It even captured the audio over the PCI bus.  I saw you updated the howto as well -- [COLOR="Green"]you da man![/COLOR]

Now onward to mythtv.

Many Thanks for Your Help,
--Phil

---

### Post by superm1 on 2007-01-05
> **pmurnane said:**
> superm1:

Works great!  In step 4 I had to add ivtv-firmware to the list of modules to install, but other than that it worked like a charm.  It even captured the audio over the PCI bus.  I saw you updated the howto as well -- [COLOR=Green]you da man![/COLOR]

Now onward to mythtv.

Many Thanks for Your Help,
--Phil
Very good, glad we got this going :)

---

