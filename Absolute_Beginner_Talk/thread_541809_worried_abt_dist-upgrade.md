---
title: "worried abt dist-upgrade"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by jsdill on 2007-09-03
Folks...I installed Ubuntu some months ago and have had no issue with upgrades til linux-image-server which has been "kept back."

I understand that this might be because of "system changing results"  and that a "sudo aptitude dist-upgrade" may be necessary.

I am concerned that the dist-upgrade may cause issues. What are thoughts abt the dist-upgrade? I do not wish to cause the server issues not existing at this time.

Thanks for any advice offered.

...Jordan

---

### Post by Kobalt on 2007-09-03
*sudo aptitude dist-upgrade* is a safe command line as long as you don't add exotic repositories to your sources.list. If you haven't, you can trust Aptitude.
To learn more ```
man aptitude
```

---

### Post by Anicka on 2007-09-03
If your worried about what would happen, do a simulation: ```
aptitude -s dist-upgrade
``` The flag -s means simulation, no downloads, no install, no nothing, just checking what would happen if... If you don't like the result of the simulation, don't do the real upgrade.

---

### Post by insane_alien on 2007-09-03
you can always try installing the packages manually. like doing sudo aptitude <paste the packages that were kept back here>.

sometimes that works.

---

### Post by jsdill on 2007-09-06
> **Anicka said:**
> If your worried about what would happen, do a simulation: ```
aptitude -s dist-upgrade
``` The flag -s means simulation, no downloads, no install, no nothing, just checking what would happen if... If you don't like the result of the simulation, don't do the real upgrade.

Thanks all for your responses...am going to give the simulation a shot.

...Jordan

---

### Post by jsdill on 2007-09-06
> **jsdill said:**
> Thanks all for your responses...am going to give the simulation a shot.

...Jordan


Folks...I just googled on aptitude -s dist-upgrade and nothing turned up. Am curious as to why?

This seems to be a valuable command.

...Jordan

---

### Post by jsdill on 2007-09-06
> **jsdill said:**
> Folks...I just googled on aptitude -s dist-upgrade and nothing turned up. Am curious as to why?


No matter! I see it is thoroughly addressed in the man pages.

...Jordan

---

### Post by jsdill on 2007-09-07
> **jsdill said:**
> Thanks all for your responses...am going to give the simulation a shot.

...Jordan

Folks...very much appreciate the help so far.

Please confirm for me (based on the following simulation return) that it looks like I'd have no issue with an upgrade from dapper drake:

aptitude -s dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  linux-image-2.6.15-29-server 
The following NEW packages will be installed:
  linux-image-2.6.15-29-server 
The following packages will be upgraded:
  linux-image-server 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.2MB of archives. After unpacking 67.6MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

...Jordan

---

### Post by 5-HT on 2007-09-07
> **jsdill said:**
> 
Please confirm for me (based on the following simulation return) that it looks like I'd have no issue with an upgrade from dapper drake:


It'll just bring in a new kernel and update the metapackage for it. As to whether the kernel will work perfectly however.....(well they are tested prior to being unleased, and you can always just boot back into the old one if need be).
cheers,

---

### Post by Anicka on 2007-09-08
> **jsdill said:**
> Folks...very much appreciate the help so far.

Please confirm for me (based on the following simulation return) that it looks like I'd have no issue with an upgrade from dapper drake:

aptitude -s dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  linux-image-2.6.15-29-server 
The following NEW packages will be installed:
  linux-image-2.6.15-29-server 
The following packages will be upgraded:
  linux-image-server 
1 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.2MB of archives. After unpacking 67.6MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

...Jordan

If you had said yes, the simulation would have said something like: "Would downlod/remove/install packages" Nothing bad can happen, you're not even root.

---

### Post by jsdill on 2007-09-08
> **Anicka said:**
> If you had said yes, the simulation would have said something like: "Would downlod/remove/install packages" Nothing bad can happen, you're not even root.

Thanks...had wondered abt that.

As to root, well, the fact that I am root (excluded that from my paste) is why I am moving so slowly.

Appreciate your advice.

...Jordan

---

