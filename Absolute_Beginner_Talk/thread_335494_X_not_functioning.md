---
title: "X not functioning"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-10
Yesterday I installed the NVIDIA driver for my new computer, and everything worked perfectly after I rebooted.  After having rebooted a second time, however, X fails to launch, and I am left with the following error:

API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version.  

I find it strange that after rebooting the system once everything operated very smoothly, but now disaster!  Any help on how to solve this problem would be much appreciated!  

Thanks

---

### Post by oscar78 on 2007-01-10
Additional errors...

Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details.
***Aborting***
Screen(s) found, but none have a usable configuration.

---

### Post by thenetduck on 2007-01-10
My suggestion would be to run the reconfigure after rebooting in recovery mode. This should let you auto config your monitor and graphics card again. I can't remember or find the command to do this at the moment and im better with ATI (my downfall). If all else fails, try going through the installation steps again using recovery mode. It sounds like if you can "re configure" it will do it for you. Ill post when I find the command to do this for a Nvidia graphics card. I hope this helps some. 

 The Net Duck

---

### Post by oscar78 on 2007-01-10
Thanks.  I found another post that might also help me with my problems:

[http://www.linuxquestions.org/questions/showthread.php?t=456855](http://www.linuxquestions.org/questions/showthread.php?t=456855)

There they suggest to edit sources.list, remove the old drivers and install them again with apt-get .


Please let me know if you get anywhere with your suggestion!

Thanks

---

### Post by oscar78 on 2007-01-10
> **thenetduck said:**
> My suggestion would be to run the reconfigure after rebooting in recovery mode. This should let you auto config your monitor and graphics card again. I can't remember or find the command to do this at the moment and im better with ATI (my downfall). If all else fails, try going through the installation steps again using recovery mode. It sounds like if you can "re configure" it will do it for you. Ill post when I find the command to do this for a Nvidia graphics card. I hope this helps some. 

 The Net Duck

what exactly would I have to reconfigure?

---

### Post by bodhi.zazen on 2007-01-10
If you are still having difficulty, try envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by oscar78 on 2007-01-10
Thanks,

I think I'll try that.  However, I have a few problems: 

1.  I have already installed the NVIDIA driver I need.  Would I need to uninstall it first and then run the python script you suggested?  

2.  I need to download everything from the terminal.  How can I retrieve this script from the url you suggested in the terminal?

---

### Post by oscar78 on 2007-01-10
> **bodhi.zazen said:**
> If you are still having difficulty, try envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy worked perfectly!  My X problems are solved (at least for now).  Thanks everyone!

---

### Post by bodhi.zazen on 2007-01-10
> **oscar78 said:**
> Envy worked perfectly!  My X problems are solved (at least for now).  Thanks everyone!

8)

---

