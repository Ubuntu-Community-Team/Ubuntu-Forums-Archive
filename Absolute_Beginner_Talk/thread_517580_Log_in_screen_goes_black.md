---
title: "Log in screen goes black"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Bogdon6 on 2007-08-04
When I boot the computer, there are no display problem until the login screen.  When Ubuntu brings up the login screen the monitor goes black, as if the login screen it outside of the monitor's display range.  If I type in my login and password, Ubuntu continues with no problems whatsoever and the display works perfectly.   

Does anyone have any advice?  

Thanks

---

### Post by NT4usB on 2007-08-04
Advise #1:
Post your system specs (intel/amd. video card, etc.), the version of Ubuntu you're running, and what you recently changed, installed, removed, or otherwise messed with, when you post a problem.

Sounds like the xserver got borked.
Easy to fix, if that's the problem. 
Search for dpkg-reconfigure xserver-xorg.
[xserver]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=a6&q=site%3Aubuntuforums.org+%22black+screen%22+dpkg-reconfigure+xserver-xorg&btnG=Search")

---

### Post by Bogdon6 on 2007-11-11
This problem was resolved by upgrading to Gutsy. Now it works like a champ.

---

