---
title: "apt command for kernel upgrade"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by wardjame on 2006-06-17
Hi All,
I just ran my breezy to dapper dist-upgrade per the instructions and everything seemed to go fine.  Now I would like to bring the kernel up to date with dapper but I am running this machine command line only.  

Can someone post the apt-get commands to upgrade my kernel correctly?  Is there a command line auto-updater I should be running?

Thanks in advance.

---

### Post by x64Jimbo on 2006-06-17
If you run 
sudo apt-cache search linux
you should be able to find a listing of all the kernels you can download and install. 
Just be sure you apt-get update first.

---

### Post by wardjame on 2006-06-17
Sorry I'm still a little confused.  Looking at that list it looks like just linux-686 would be my best but it says I already have that installed.  I assumed I would have to do some combination of sources, headers, images for 2.6.15-25.  Am I wrong about that?

---

### Post by wardjame on 2006-06-17
Ok.  Maybe I need to provide more detail or post this in a different forum.  Specifically I would like to upgrade my box to the 2.6.15-25 kernel from the 2.6.12.x kernel breezy gave me.  I assume when I run apt-get install linux-686 it looks for the latest .x version of my current kernel and not the kernel upgrade.

Assuming I want to use the linux-686 kernels what apt-get commands do I need to issue to get the 2.6.15-25 kernel installed?

Thanks.

---

### Post by 5-HT on 2006-06-17
[quote=wardjame]Ok.  Maybe I need to provide more detail or post this in a different forum.  Specifically I would like to upgrade my box to the 2.6.15-25 kernel from the 2.6.12.x kernel breezy gave me.  I assume when I run apt-get install linux-686 it looks for the latest .x version of my current kernel and not the kernel upgrade.

Assuming I want to use the linux-686 kernels what apt-get commands do I need to issue to get the 2.6.15-25 kernel installed?

Thanks.[/quote] 
The linux-686 package will *always* depend on the latest kernel available in the repos.
For Dapper, these kernels should all be of the 2.6.15 line.

If you only have 2.6.12 kernels installed, one possibility is that your upgrade to Dapper did not go perfectly.

If linux-686 is installed and a 2.6.15 kernel is not available, there could be a problem with your sources.list not pointing to the proper (Dapper) repositories. 

How did you upgrade to Dapper?
Could you post your /etc/apt/sources.list?
Can you post the output of 'lsb_release -a'?

[quote=wardjame]Looking at that list it looks like just linux-686 would be my best but it says I already have that installed.I assumed I would have to do some combination of sources, headers, images for 2.6.15-25 [/quote] 
linux-686 depends on the most recent binary kernel (linux-image) and restricted-modules. 
Even with linux-686 installed, the sources and headers will need to be installed separately.

---

### Post by wardjame on 2006-06-22
I'm an idiot.  I just needed to reboot to get it to load the new kernel.  Thanks for all the help.

---

