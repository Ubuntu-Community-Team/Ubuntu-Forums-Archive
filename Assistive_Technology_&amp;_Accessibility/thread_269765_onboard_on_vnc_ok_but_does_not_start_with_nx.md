---
title: "onboard: on vnc ok but does not start with nx"
date: 2006-10-02
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-02
Hello, 

When I forward the ubuntu-session to my macosx using the free edition of nx from nomachine.com, onboard does not start up. However, when I use the vnc server shipped with ubuntu 6.06.1 to forward the session to macosx, onboard does start up. 

I am not sure, but it seems to me that nx does a "X forward"; could this be the reason? 

frafu

---

### Post by t0rtois3 on 2006-10-02
Could you run onboard from a terminal and paste the output into this forum

click applications/accessories/terminal and type onboard

thanks

---

### Post by frafu on 2006-10-02
Here it is; hoping that it helps. 

```
 
frafu@UbuntuDesktop:~$ onboard
Error getting keyboard geometry info.
/usr/bin/onboard: line 5: 12824 Segmentation fault      (core dumped) /usr/share/onboard/run-onboard.py
frafu@UbuntuDesktop:~$

``` 

```
 
frafu@UbuntuDesktop:~$ onboard &
[1] 13006
frafu@UbuntuDesktop:~$ Error getting keyboard geometry info.
/usr/bin/onboard: line 5: 13007 Segmentation fault      (core dumped) /usr/share/onboard/run-onboard.py

[1]+  Exit 139                onboard
frafu@UbuntuDesktop:~$

``` 

frafu

Added later: This [Problem]("http://ubuntuforums.org/showthread.php?p=1576168#post1576168") might be related.

---

