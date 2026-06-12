---
title: "kernel 2.6.24.2 gave me more suspend in mactel santarosa!"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by aztechclan on 2008-02-22
I decided to upgrade Gusty to a 2.6.24.2 kernel from kernel.org. So if you had a working stock gusty with restricted drivers and madwifi trunk, this will work pretty easy.  I pastebin'd my kernel config for anyone who would like to not hit enter so much. [http://pastebin.com/f1688d8ea](http://pastebin.com/f1688d8ea) :)  Is anyone else running this kernel on mactel santarosa + gusty ?  

Step 1) follow all the great advise on the ubuntu wiki + santarosa pages (even the bash script to control your fans, it's been working great)

Step2)  download and compile the kernel 2.6.24.2 from kernel.org, copy the pastebin file into /usr/src/linux-2.6.24.2/.config .

Step3)  install the kernel+header pkgs you got from make-kpkg, download NVIDIA drivers from nvidia.com and USE SPECIFICALLY VERSION NVIDIA-Linux-x86-100.14.19-pkg1.run !  The latest version will have issues with dual monitor and EDIDs, this version works better I think.

Step4)  reboot, go into console mode (CTRL+ALT+F1).  Stop gdm (sudo /etc/init.d/gdm stop).  setup the "SYSSRC=/usr/src/linux-2.6.24.2" environment variable for the nvidia installer to find your source.  Chmod +x the NVIDIA driver and run it.

Step5)  modprobe the nvidia module and start gdm (or reboot).

Step6)  download the madwifi source from subversion (the very latest) and install.

Yep that's about it.  IF this is useful to anyone maybe I'll go into more detail.  In a hurry 2day and so far this kernel is great except for the madwifi seems a tad unstable..  Suspend is now working awesome though! and that was my original goal of the upgrade.

---

### Post by cyberdork33 on 2008-02-22
This is for a Macbook Pro I assume.

You could also just get Hardy's kernel...
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by aztechclan on 2008-02-22
I considered that but was scared away by the mixing of packages from hardy.  I want to keep gusty the way it is, but run a later kernel.  What version of NVIDIA restricted driver does that method install?  Either way, this is the way I've done it in the past and it makes more sense to me.  Give make-kpkg some love.

---

### Post by cyberdork33 on 2008-02-22
> **aztechclan said:**
> I considered that but was scared away by the mixing of packages from hardy.  I want to keep gusty the way it is, but run a later kernel.  What version of NVIDIA restricted driver does that method install?  Either way, this is the way I've done it in the past and it makes more sense to me.  Give make-kpkg some love.You don't have to upgrade your system... It just pulls the kernel and related packages... kernel-headers, etc. I am not sure what the nvidia driver version in the hardy repository is. but you can just install it with envy or manually as you did.

---

### Post by aztechclan on 2008-02-22
WARNING about Envy though, it did not have the option to use the right NVIDIA driver. The latest driver will work fine unless you want Dual display, then you get bitten by the EDID bug.  Gusty uses an older version also (100.14.19), and it works well in all aspects.  Envy's legacy options for Manual install were not the right version either (too bad cause I do like Envy's packaging ways).

Anyway, I'm loving the Macbook Pro SantaRosa (3rd gen).  I've been a linux+NVIDIA fan for a long time and it was the only thing keeping me from a MacBookPro (was ATI chipset in 1st and 2nd gen).

---

### Post by rob_peer on 2008-02-22
great!
i have a SR MBP!

---

