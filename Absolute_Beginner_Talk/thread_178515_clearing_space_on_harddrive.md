---
title: "clearing space on harddrive?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-05-17
i need to clear about a gig of files for something im downloading. Any advice? like common files or folders that i can empty or live without?
Thanks

---

### Post by bluevoodoo1 on 2006-05-17
you can try...

sudo apt-get clean
and
sudo apt-get autoclean

from man apt-get...
> clean  
clean clears out  the  local  repository  of  retrieved  package
              files.   It   removes   everything   but   the  lock  file  from
              /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/.
              When  APT is used as a dselect(8 ) method, clean is run automati-
              cally. Those who do not use dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.

       autoclean
              Like  clean,  autoclean  clears  out the local repository of re-
              trieved package files. The difference is that  it  only  removes
              package  files that can no longer be downloaded, and are largely
              useless. This allows a cache to be maintained over a long period
              without  it  growing  out  of  control. The configuration option
              APT::Clean-Installed will prevent installed packages from  being
              erased if it is set to off.


---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=jinxjinx]i need to clear about a gig of files for something im downloading. Any advice? like common files or folders that i can empty or live without?
Thanks[/QUOTE]
Try [ this tutorial.](http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+files) It shows a few ways to clean up some unneeded files.

---

