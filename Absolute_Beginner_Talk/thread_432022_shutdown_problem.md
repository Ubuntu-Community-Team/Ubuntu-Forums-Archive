---
title: "shutdown problem"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by patnshan on 2007-05-03
One of my Ubuntu machines (the one with the slow processor) is working perfectly but it will not shutdown correctly.  I have to push the power button to shut it down.  I click on the top right icon, select shut down.  It looks like it will, as on the other machine.  Then it hangs on the ubuntu screen.  If it matters, the bar with the orange fill in is empty when it happens.  I did a search and saw reference to shutdown, but most of them are about absent options, no button, etc.  I have everything there, it just doesn't finish shutting down.  This is reproducible, as it happens everytime. 
What could be causing this?  It's no big deal, but I want it to completely power off like it should without using the power button.
Thanks,
Pat

---

### Post by jargoman on 2007-05-04
you can shutdown from the terminal with

$ sudo su
(enter your password)
$ shutdown now

---

### Post by Duck2006 on 2007-05-04
What type of video card do you have?

---

### Post by patnshan on 2007-05-04
> **Duck2006 said:**
> What type of video card do you have?

It is an old P3 compaq deskpro machine, not sure.  I'll have to check.  

Pat

---

### Post by patnshan on 2007-05-04
> **jargoman said:**
> you can shutdown from the terminal with

$ sudo su
(enter your password)
$ shutdown now

I can try that, but I'd think it is likely to do the same thing.  Doesn't this command do the same thing as clicking shutdown in the menu?  If not, I'll try it.  It hangs after clicking that shutdown command.

Pat

---

