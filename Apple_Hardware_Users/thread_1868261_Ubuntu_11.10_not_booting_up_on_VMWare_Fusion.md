---
title: "Ubuntu 11.10 not booting up on VMWare Fusion"
date: 2011-10-24
forum: Apple Hardware Users
---

### Post by pegah on 2011-10-24
I am an absolute beginner with Linux. I was using Ubuntu 11.04 with no problems on a virtual machine (VM Ware Fusion) on my Mac OSX 10.6. Then I was prompted by the update manager to upgrade to Ubuntu 11.10. I did so, and it seemed to be working fine at first. But after my battery died, and I reconnected the power, Ubuntu wouldn't boot up. 
So, now when I turn on VMWare, and try to start up Ubuntu, first it says: "Waiting for Network Configurations". After a couple of minutes, it says: "Waiting up to 60 more seconds for network configurations". After another minute in that state, it says: "Booting up without full network configurations". Then there is just a black screen and nothing else. Nothing happens afterwards.
Can anyone help me with how to get Ubuntu to boot up?

Thanks,
Pegah

---

### Post by fmlogue on 2011-10-26
I'm glad to here that I am not the only person having this problem.  I was afraid it was because I was still using Fusion 3 while running Lion.  A solution would be nice.  As it was, I was able to go back to 11.04.

---

### Post by tony_olivieri on 2011-10-27
I am also having this problem. I am a linux newbie @.@, so maybe I did something wrong. 
Running on a  Macbook pro, OS Lion 10.71, quad core i7.
VMware fusion V4 (also tried with V3).
Ubuntu 11.10, I've tried both 32 and 64 bit.

The weird thing is, I can log in under "guest" but not as admin. Logging in as guest does not allow me to change any settings though. 
I was able to log into the Admin account the first time I installed Ubuntu (from the initial command prompt window). But now when I try to log in (with the right password of course) VMware resizes my window, black screen appears, then flashes some text, and stuff. So  tries to load up Ubuntu, but then it just goes right back to the log in menu screen. Also In the log in screen, I can only shutdown Ubuntu through Fusion software, the Ubuntu shutdown option just doesn't work....

I'm going to try some older versions of Ubuntu for now, but it would be nice if the newest version could be used..

Cheers,

---

### Post by conundrumx on 2011-10-27
> **pegah said:**
> I am an absolute beginner with Linux. I was using Ubuntu 11.04 with no problems on a virtual machine (VM Ware Fusion) on my Mac OSX 10.6. Then I was prompted by the update manager to upgrade to Ubuntu 11.10. I did so, and it seemed to be working fine at first. But after my battery died, and I reconnected the power, Ubuntu wouldn't boot up. 
So, now when I turn on VMWare, and try to start up Ubuntu, first it says: "Waiting for Network Configurations". After a couple of minutes, it says: "Waiting up to 60 more seconds for network configurations". After another minute in that state, it says: "Booting up without full network configurations". Then there is just a black screen and nothing else. Nothing happens afterwards.
Can anyone help me with how to get Ubuntu to boot up?

Thanks,
Pegah

Sounds like a problem with GRUB, the VM's BIOS can't find anything to boot.  You might try booting off an Ubuntu ISO and take a look at your disk.  If your data all seems to be there try looking up instructions for fixing GRUB.

> **fmlogue said:**
> I'm glad to here that I am not the only person having this problem.  I was afraid it was because I was still using Fusion 3 while running Lion.  A solution would be nice.  As it was, I was able to go back to 11.04.

Fusion 3 works fine on Lion, so that's not the cause of your issues.

> **tony_olivieri said:**
> I am also having this problem. I am a linux newbie @.@, so maybe I did something wrong. 
Running on a  Macbook pro, OS Lion 10.71, quad core i7.
VMware fusion V4 (also tried with V3).
Ubuntu 11.10, I've tried both 32 and 64 bit.

The weird thing is, I can log in under "guest" but not as admin. Logging in as guest does not allow me to change any settings though. 
I was able to log into the Admin account the first time I installed Ubuntu (from the initial command prompt window). But now when I try to log in (with the right password of course) VMware resizes my window, black screen appears, then flashes some text, and stuff. So  tries to load up Ubuntu, but then it just goes right back to the log in menu screen. Also In the log in screen, I can only shutdown Ubuntu through Fusion software, the Ubuntu shutdown option just doesn't work....

I'm going to try some older versions of Ubuntu for now, but it would be nice if the newest version could be used..

Cheers,

This sounds like a problem with your X configuration.  Try switching to "Ubuntu (safe mode)" along the bottom of your screen after selecting your user account.


Regarding **all** of the problems you guys are encountering, it's not uncommon for a newer release of any software to have some bugs, and VMware sometimes has to issue fixes of their own to be more compatible with new OS versions.

---

### Post by tony_olivieri on 2011-10-29
Hi guys,

I am finally able to boot up both 32 and 64 bit Ubuntu 11.10 on VMware Fusion V4. I did 2 things differently with these installs, but i'm not entirely sure which was causing the problem.

First change, my initial passwords were very short, 4 characters. So with the new install I increased that to more then 12 characters (the guest account w/out password was working fine before). So I am suspecting this was the cause.
But the second thing that I'm NOT doing, that I did before with every install, regards all the updates. I have yet to download and install ALL the updates. I'm installing one at a time. If I encounter this problem again due to an update, I'll post back.

Hope this helps the few people having this problem.

Cheers,
Tony

---

