---
title: "installing fltk on 7.10"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by J-Rob on 2008-03-17
Hey  there,

I have recently just got Ubuntu 7.10. I am trying to install fltk however I get the 

configure: error: Configure could not find required X11 libraries

error. I have had a look at the other forums, which generally say the solution is to install xorg from the package manager. However, I have checked the package manager and it's already there. Also, fltk is not available in my package manager. Any advice would be great! :)

---

### Post by thewho? on 2008-03-18
You need the xlibs-dev package.  sudo apt-get install xlibs-dev should do it.

---

