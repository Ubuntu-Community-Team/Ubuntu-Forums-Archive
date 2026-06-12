---
title: "clock"
date: 2008-03-20
forum: Apple PPC Users
---

### Post by LinuxRT on 2008-03-20
I just put Ubuntu Gutsy Live CD onto it my ibook G4, booted with 'live video=ofonly' to install it.

 After booting from the Gutsy live CD, Ubuntu's default desktop session pops up a dialog that reads:

"The computer clock appears to be wrong" ... Ignore / Adjust the Clock.

 However, selecting either ignore or adjust fails: You get a dialog that says:

"The configuration could not be loaded
 You are not allowed to access the system configuration.
    [close]"

Any hints on how to or this is a bug?

Thanks a lot really need your help!

RT

---

### Post by LinuxRT on 2008-03-20
I forgot to mention that when I click close, the computer will just stay there doing nothing. 

Thanks, RT

---

### Post by slacka-vt on 2008-03-21
this is totally normal.
you shouldn't have access to the system clock as a "live session user"
you should, however, set the clock using what ever OS is installed on the Hard Drive
or after installing Ubuntu from the live cd, you will have permission to set the system clock.

~S

---

### Post by slacka-vt on 2008-03-21
woops. . . 
i forgot to address you initial question

when you get the dialog box that says:
"The configuration could not be loaded
You are not allowed to access the system configuration.
[close]"

you may have to hit the [tab] key to select "close"
before hitting return.

the mouse isn't going to work, so you can't click on it

~s

---

