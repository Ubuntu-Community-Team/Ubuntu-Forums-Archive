---
title: "nvidia geforce go 6150... issues"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by secretsquirrel13 on 2008-03-15
I just installed Ubuntu Gutsy yesterday (first time using ubuntu, no real idea what I am doing).  While playing around with video drivers, something went wrong and now the screen is all garbled.

How can I go back to whatever driver it was using, even the generic one would get me to a usable desktop that I can work from.

Also, I cant boot into recovery mode.  It keeps hanging at different points in the boot process (tried three times)

Any help would be much appreciated.

---

### Post by chips24 on 2008-03-15
i have the same graphics card, you must have done somthing really messy to mess that up. check out your restricted drivers manager.

there is a way to change the driver manually, i will get back to yo on that.

---

### Post by Mogurijin on 2008-03-15
Can you boot at all into Ubuntu? If so, try CTRL+ALT+Backspace and you'll get to a command prompt. Log in and try

```
sudo dkpg-reconfigure xserver-xorg
```

You should be able to reset stuff from there. Try and see if you can select the "Vesa" driver, which is the default.

I hope that was all right :-k

---

### Post by chips24 on 2008-03-15
do you need to install your graphics card?
what kind of computer do you have?
can you be more specific?

---

### Post by secretsquirrel13 on 2008-03-17
Mogurijin:
I will have to try that command.  Thanks.

edit: when I booted, I had to hit ctrl+alt+f2 (not T) to get to the command prompt.  i got some kind of invalid command after trying that command.  Are we working with different versions?  Is the syntax correct?

chips:
I have an HP dv6451us laptop.  I just want to find a driver that will support 1280x800 resolution (native) and 3d effects (I want some eye candy).

---

### Post by secretsquirrel13 on 2008-03-17
Got the command to work (it was "sudo dpkg ...") and now my video works again!  Thanks everybody.

Now I just have to figure out how to get a correct driver in there...

---

