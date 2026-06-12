---
title: "Problems with Sound Troubleshooting: Requires Kernel Source?"
date: 2011-03-18
forum: Apple Hardware Users
---

### Post by Canvasian on 2011-03-18
Hi! I've been troubleshooting the Audio for my iMac for the past few weeks (ugh) and right now I'm working through this: [http://ubuntuforums.org/showpost.php?p=3697702&postcount=5](http://ubuntuforums.org/showpost.php?p=3697702&postcount=5)

When I use 
[FONT=monospace]
[/FONT]./configure --with-cards=hda-intel 
It tells me: 

```
The file /lib/modules/2.6.35-28-generic/build/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distrubution or use --with-kernel=dir option to specifiy another directory with kernel sources (default is /lib/modules/2.6.35-28-generic/build).
```When I searched for how to get kernel source I got this:
[https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source](https://help.ubuntu.com/community/Kernel/Compile#Get%20the%20kernel%20source)

So I installed git-core and ran:

```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
```and then tried:

```
fakeroot debian/rules clean
```But it told me:

```
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
```SO when that didn't work, I tried this instead: [https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)

But it says that's specifically if you are targeting the PowerPC architecture, which I'm not (I have an Intel iMac)... and I also don't know
the version number of the source I should be trying to get... and am generally clueless and nervous about messing with kernels
while being generally clueless xD I tried to post this stuff here: [http://ubuntuforums.org/showthread.php?t=598725](http://ubuntuforums.org/showthread.php?t=598725)
but for some reason the forums wouldn't let me post there D: So I would really appreciate some help with this! Thanks!

---

### Post by Untitled_No4 on 2011-03-19
Which iMac do you have? What version of Ubuntu (I guess Maverick, since you're trying to get the Maverick kernel)? That post you're following is from 2007 and Ubuntu is nothing like it used to be back then.

Have you had a look here: [https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound) ? All I had to do was to unmute the Front Speak in alsamixer and turn its volume up (iMac 27).

I think there must be an easier solution to your problem then compiling Alsa (and Ubuntu uses PulseAudio nowadays anyway...). Personally I can't help you more than to refer you to that page above, but perhaps if you give more details someone more knowledgeable will come along.

---

