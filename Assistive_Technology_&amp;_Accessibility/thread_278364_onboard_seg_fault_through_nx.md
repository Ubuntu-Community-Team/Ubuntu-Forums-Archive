---
title: "onboard seg fault through nx"
date: 2006-10-16
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-16
Hello,

I have a remote celeronbox with onboard on it. 

When I launch onboard on the desktop forwarded with vnc, there is no problem. 

However when I launch onboard on the desktop forwarded with nx from nomachine, nothing happens: onboard does not appear. So I tried launching it in the terminal, and I get the following: 
```
 
frafu@UbuntuDesktop:~$ onboard
Error getting keyboard geometry info.
Segmentation fault (core dumped)
frafu@UbuntuDesktop:~$ onboard &
[1] 19420
frafu@UbuntuDesktop:~$ Error getting keyboard geometry info.
Segmentation fault (core dumped)

[1]+  Exit 139                onboard
frafum@UbuntuDesktop:~$ 

``` 

This problem already was present in dapper; yesterday I upgraded to edgy and the problem is still there. 

In this forum, there is another thread that might be related. [Here it is.]("http://ubuntuforums.org/showthread.php?t=270457") 

If I can do anything to narrow down the problem, don't hesitate to ask. 

frafu

---

### Post by t0rtois3 on 2006-10-17
The problem is when onboard tries to get your keyboard layout from the xserver.  NX runs the xserver in an odd way in order to work.  A possible work around would be to run onboard on the machine locally or over vnc, open the settings dialog and click personalise layout.  onboard then creates a new layout identical to your current one.  Select that and then run onboard in NX.

Onboard reads the layout from a file this way and shouldn't try to ask the xserver for it.  

There might be other problems though.  I'll try and test and hopefully debug it some time.

---

### Post by frafu on 2006-10-17
Hello, 

Thanks for the workaround: I copied the layout with vnc as you suggested and now onboard starts up also in nx. 

frafu

---

