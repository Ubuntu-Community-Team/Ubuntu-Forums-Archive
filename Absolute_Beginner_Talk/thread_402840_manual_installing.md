---
title: "manual installing"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-04-06
I am new to ubuntu and have had little trouble using synaptic installations.  I am now trying to get some obscure installations that are not in synaptic.  I want to set up cross-compilers for ARM targets.  Unfortunately the directions I followed on gnuarm.com have not worked.  I get error "arm-gcc-elf not found" when I try to compile arm code.   I just deleted the directory where all the installed code went.  Does this really get rid of the failed installation?  I noticed when gcc was compiled, it was doing things to all the .c code files I had, code that has nothing to do with gcc installation.  I am really confused by installing arm gcc from source.

Is there some kind standard way to install things or is each installer different?  Should I precede installation commands with 'sudo' because or else I wont have permission to write in /usr?  Why does some code go in /usr/bin and other code goes in /usr/share and other code goes in /usr/lib and other code goes into /usr/its_own_directory?  And still other stuff will install off of my home directory?  Is there a standard place like in windows it is 'program files' and very few programs actually deviate from that standard.

Thanks
outer_space

Thanks,
outer_space

---

### Post by zvacet on 2007-04-06
Do you have all repositories open? If you don´t here is how to do it
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
Synaptic is easy to use.Click on search>type name of program.When synaptic find it click on box in the left and select **mark for installation**.If you want to install some program that is not in synaptic and you can not find deb file on the web you need to compile,and to beable to do it compilers are needed.
```
sudo aptitude install build-essential
```
Parallel to program files may be usr/bin .

---

