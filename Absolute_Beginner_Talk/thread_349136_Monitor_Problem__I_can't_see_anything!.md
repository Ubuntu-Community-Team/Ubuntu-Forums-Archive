---
title: "Monitor Problem:  I can't see anything!"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by JCSaint on 2007-01-29
Okay, after not getting my Ubuntu cd to work, I found the Windows installer and was able to use that.  I selected ubuntu from the menu and I assume it booted but instead of seeing a desktop, my monitor displayed an error message.  "Out of range/ 60 hz/ 65 hz"  (I think those were the numbers.  This is similar to the error message I get when I try to change the resolution above 1024 x 768 with XP.

So, I'm guessing I need to install a driver?  How can I do that if I can't see anything?  Should I try to hook up another monitor to install the driver for the one I want to use?  Or am I having some other weirdo problem?

---

### Post by Happy_Man on 2007-01-29
It's not a driver issue; rather, it's a problem with your xorg.conf file. In case you don't know, xorg.conf is a file that contains instructions for all your input/output devices, like, monitor, keyboard, etc. The refresh problem stems from the fact that your xorg.conf registered the wrong refresh rates for your monitor, and so now your monitor won't be displaying much. ;) If you can't see anything, not even a little flashing cursor, you're better off installing off the cd. The problem with the installer is that it's still WAAAY in beta, so you can't trust it. ISOs are tried and true methods. Why don't you just post your cd issues here? I'm sure I or someone else would be able to help you fix it.

---

