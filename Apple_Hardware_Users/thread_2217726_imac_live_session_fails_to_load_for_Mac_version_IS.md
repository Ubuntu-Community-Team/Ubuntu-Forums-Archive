---
title: "imac live session fails to load for Mac version ISO."
date: 2014-04-18
forum: Apple Hardware Users
---

### Post by 300Z on 2014-04-18
I have a mid 2011 27 imac and I can't get it to load the Mac specific version of Ubuntu, I downloaded the Ubuntu for mac ISO and created a bootable USB thumb drive but it will not show up at the boot selection so I thought I might have had a bad ISO so I re-downloaded and started over but had the same results, then I tried just the regular Ubuntu ISO and it loads up just fine, so what's going on with the Mac specific version? :confused::confused::confused:

---

### Post by bapoumba on 2014-04-18
Moved to Apple Users.

---

### Post by 300Z on 2014-04-18
Nobody ever seen this issue? :(

---

### Post by bapoumba on 2014-04-19
Quite sorry, I have macs for work, and I am not to install Ubuntu on them.. I do not have one of my own that I could be playing with. That said, here are a few threads, although older, that may be of some use :

[http://ubuntuforums.org/showthread.php?t=2144172](http://ubuntuforums.org/showthread.php?t=2144172)
[http://ubuntuforums.org/showthread.php?t=2015238](http://ubuntuforums.org/showthread.php?t=2015238)
[http://ubuntuforums.org/showthread.php?t=2001755](http://ubuntuforums.org/showthread.php?t=2001755)
[http://ubuntuforums.org/showthread.php?t=1972982](http://ubuntuforums.org/showthread.php?t=1972982)

[https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac)

---

### Post by 300Z on 2014-04-19
Thank you for your input, I have read most of those threads and I'm ready to install but I'm just wondering if I should try to get the mac specific ISO to work or just go ahead and install it using the regular Ubuntu ISO? :confused: What else is in the mac ISO?

---

### Post by bapoumba on 2014-04-19
> **300Z said:**
> Thank you for your input, I have read most of those threads and I'm ready to install but I'm just wondering if I should try to get the mac specific ISO to work or just go ahead and install it using the regular Ubuntu ISO? :confused: What else is in the mac ISO?

I think it has to do with booting, Macs do not appear to boot uefi mode properly :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633983](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633983)

But it now appears Trusty works :
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894)

So I may be you'll have to try the regular version and comment on the bug reports if you cannot boot it. That would mean that the Mac ISO will have to continue to be offered.

---

### Post by este.el.paz on 2014-04-19
> **300Z said:**
> I have a mid 2011 27 imac and I can't get it to load the Mac specific version of Ubuntu, I downloaded the Ubuntu for mac ISO and created a bootable USB thumb drive but it will not show up at the boot selection so I thought I might have had a bad ISO so I re-downloaded and started over but had the same results, then I tried just the regular Ubuntu ISO and it loads up just fine, so what's going on with the Mac specific version? :confused::confused::confused:

@300Z:

I think you are asking the wrong question . . . for any of the Intel macs the version is not different, you would just be picking 32 bit or probably for you it would be the 64 bit "amd" . . . version.  The only "specific for apple" .iso should be for "ppc" . . . and would not work on your mac.  Yesterday I downloaded the Xubun 14.04 64bit amd iso, burned it to DVD and I'm booted up in my '10 MBPro . . . no problem.  I'm certain if I took the Lubun 14.04 for ppc iso DVD and tried to boot it on this laptop . . . it would not work.

That said, there is some difference on getting Ubun to boot on Mac, and usually that is a "dual boot" set up, unless you run it in virtual app; for dual booting you need "rEFInd" installed before your OSX partition . . . .

e.e.p.

---

### Post by 300Z on 2014-04-19
> **este.el.paz said:**
> @300Z:

I think you are asking the wrong question . . . for any of the Intel macs the version is not different, you would just be picking 32 bit or probably for you it would be the 64 bit "amd" . . . version.  The only "specific for apple" .iso should be for "ppc" . . . and would not work on your mac.  Yesterday I downloaded the Xubun 14.04 64bit amd iso, burned it to DVD and I'm booted up in my '10 MBPro . . . no problem.  I'm certain if I took the Lubun 14.04 for ppc iso DVD and tried to boot it on this laptop . . . it would not work.

That said, there is some difference on getting Ubun to boot on Mac, and usually that is a "dual boot" set up, unless you run it in virtual app; for dual booting you need "rEFInd" installed before your OSX partition . . . .

e.e.p.
From the download page on the drop down menu on choose your flavour there's an option for the [64-bit Mac (AMD64)]("http://www.ubuntu.com/download/desktop") and that's the one I downloaded, as far as I'm aware that's not for the PPC platform.

---

### Post by este.el.paz on 2014-04-19
> **300Z said:**
> From the download page on the drop down menu on choose your flavour there's an option for the [64-bit Mac (AMD64)]("http://www.ubuntu.com/download/desktop") and that's the one I downloaded, as far as I'm aware that's not for the PPC platform.


You are correct, interesting, because like I said, yesterday I just downloaded the Xubun flavor and saw nothing different for Mac . . . main thing is, did you get something to work?  If so, you are a winner in linux-land . . . .

e.e.p.

---

### Post by 300Z on 2014-04-19
I haven't got the Mac version to work but I can boot the regular version every time and everything seems to work, the only weird thing is the audio doesn't sound the same, I think Apple uses some sort of frequency response equalization on OSX, but the weird part is that it also sounds different on the line out that goes to my amplifier. :(
I haven't tried to install it yet as I haven't had much free time these past few days but I'll probably do it later today.

---

### Post by este.el.paz on 2014-04-19
Sound does seem to be one of the items addressed in the FAQ . . . it doesn't take too long to do an install . . . but it does take some time to tweak the system to get it working . . . .  Possibly there is the "upgrade the system" in the Ubuntu software manager??  Haven't tried that one myself because right now I'm in LM16 on my linux partition . . . or, other option I'm thinking about is to change the sources list to "trusty" and then run "sudo apt-get update && dist-upgrade" . . . something like that, and see how that goes.  Since you already are running a 'buntu flavor it might not be too hard to try either one of those ways rather than a fresh install??  Don't know; as you can see I have been wrong many times in my life, and of course linux is prime hunting ground for proving me wrong over and over . . . .

Main thing is, enjoy the process . . . .

e.e.p.

---

