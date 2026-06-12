---
title: "&quot;Windows&quot; Key on Mac Keyboard?"
date: 2010-05-19
forum: Apple Hardware Users
---

### Post by o_swas on 2010-05-19
Hello,

I'm running Ubuntu 10.04 on my Mac Pro using Parallels.  Is there a way to map a key on the Mac keyboard to the "Context" key that's commonly found on Windows keyboards?

When using a computer using the standard "Windows" keyboard, I often use the "Context" key to simulate the right-click of a mouse to bring up a context menu.  Using this I rarely have to use the mouse.  On the Windows keyboard, the keys to the right of the space bar are Alt, Win, Context, Ctrl.

I want to emulate the Context key when using the Mac keyboard.  To the right of the space bar on the Mac keyboard are Command, Option, and Control.  I want to map the Option button that's on the ride side of the space bar to the Conext key on a Windows keyboard.

How can I do this?  I know Linux supports the Context key as I use it all the time when using Linux and a Windows keyboard.

Thank you!!!!

-Ryan

---

### Post by linuxopjemac on 2010-05-19
xmodmap

---

### Post by o_swas on 2010-05-19
xmodmap?  Could you please elaborate?

---

### Post by linuxopjemac on 2010-05-19
[http://www.xfree86.org/4.2.0/xmodmap.1.html](http://www.xfree86.org/4.2.0/xmodmap.1.html)

use xev to find out key code and assign it with xmodmap

[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

---

### Post by 2cute4u on 2010-05-19
I use vmware fusion, it lets you remap the keybaord for your virtual machine in the vmware preferences.   Maybe parallells has a similar feature.  did you try reading the documentation or googleing: parallels keyboard remap?

---

