---
title: "3D drivers are used...but they arent installed.."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-11-01
Hello,
    I upgraded to Gutsy about a week ago. I got everything working fine. I started to get my ATI drivers working and thought I was fine as I got this:

desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT
OpenGL version string: 2.0.6747 (8.40.4)

Everything seemed fine. I continued to install some games and can to the conclusion that I was not using my 3D drivers! When I start Steam I get missing DRI errors. Also, Alien Arena  acts like I do not have drivers as well. Also, I am using compiz and everything is fine there. Do I have 3D drivers, but no direct rendering? Help.

Also, when I try to start up Catalyst Control center I get that ATI Drivers are not installed or not configured correctly. But I thought I did..

---

### Post by Maestro23 on 2007-11-01
How did you install your current driver?

Also what is the output of:

> glxinfo | grep direct

If it says no, then you don't have Direct Rendering.

---

### Post by toasty_ghosty on 2007-11-01
I used Envy to install my current drivers. And no I do not have direct rendering...

---

### Post by Maestro23 on 2007-11-01
> **toasty_ghosty said:**
> I used Envy to install my current drivers. And no I do not have direct rendering...

Do you have anything checked under Restricted Drivers.

System>>Admins>>Restricted Drivers Manager

---

### Post by toasty_ghosty on 2007-11-01
Yes. I have restricted drivers in use. I still cannot access my Catalyst control center though.

---

