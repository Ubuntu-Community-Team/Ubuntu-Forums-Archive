---
title: "Help please! Pulling hair out."
date: 2014-07-19
forum: Any Other OS
---

### Post by taff2 on 2014-07-19
Ok, so make a long story shorter: I installed Mint 17 on an older Dell 1150 Inspiron laptop that had XP on it (like everyone else - right?) It runs ok and has internet through an Ethernet cable. But the wireless is not working. I thought I'd make sure everything is updated before i try and solve the wireless issue. When i try and update I get "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. And I also get "_cache->open() failed, please report."

I tried running dpkg etc. both without and with sudo preceding it and problem no different (it will only run with sudo preceding the command. There is simple a Ton of info (too much) about this in the forums to narrow it down to what the next step for me should be (I spent an hour trying to figure which post most resembled my problem).

I can run a script and post if someone could remind me of how to properly.

Thanks - almost hairless

---

### Post by sisco311 on 2014-07-19
Moved to the **Other OS/Distro Support** forum.

---

### Post by slooksterpsv on 2014-07-19
What does the output of:

sudo dpkg --configure -a

Produce?
What about:

sudo apt-get install -f

We need a bit more information.

If you need to post a long script, put it in code tags in "Go Advanced" when replying to the post, or you can paste it to pastebin

---

### Post by taff2 on 2014-07-19
This is sudo dpkg......
When i try and run other i get i should run sudo dpkg......

```

taffb@taffb-Inspiron-1150 ~ $ sudo dpkg--configure -a 
[sudo] password for taffb: 
Setting up bcmwl-kernel-source(6.30.223.141+bdcom-0ubuntu2) ... 
Removing old bcmwl-6.30.223.141+bdcomDKMS files... 


-------- Uninstall Beginning -------- 
Module:  bcmwl 
Version: 6.30.223.141+bdcom 
Kernel:  3.13.0-24-generic (i686) 
------------------------------------- 


Status: Before uninstall, this moduleversion was ACTIVE on this kernel. 


wl.ko: 
 - Uninstallation 
   - Deleting from:/lib/modules/3.13.0-24-generic/updates/ 
 - Original module 
   - No original module was found forthis module on this kernel. 
   - Use the dkms install command toreinstall any previous module version. 


depmod.............. 


DKMS: uninstall completed. 


------------------------------ 
Deleting module version:6.30.223.141+bdcom 
completely from the DKMS tree. 
------------------------------ 
Done. 
Loading new bcmwl-6.30.223.141+bdcomDKMS files... 
First Installation: checking allkernels... 
Building only for 3.13.0-24-generic 
Building for architecture i686 
Building initial module for3.13.0-24-generic 
Done. 


wl: 
Running module version sanity check. 
 - Original module 
   - No original module exists withinthis kernel 
 - Installation 
   - Installing to/lib/modules/3.13.0-24-generic/updates/ 


depmod..... 


DKMS: install completed. 
Segmentation fault  

```

---

