---
title: "Changed Video driver - now locks on bootup with flashing underscore"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by moallen on 2007-07-19
Hi there,

I am an absolute beginner to Ubuntu although I am actually using Kubuntu 7.04.  All was going well with the exception of the screen resolution.  I was playing around and found something in system settings where it looked like I could select the correct monitor that I am using.

Unfortunately the test button did not seem to work so I did something wild - just applied the changes.  It said I would have to restart which I did, but now it locks up.

Basically, I see the Kubuntu page loader, but it doesn't rotate (which I think it did earlier).  After a while, it then gives me a blank screen with a flashing underscore in the top left of the screen.  I can type in text, but it doesn't do anything - i.e. no commands are accepted.

I have tried doing a repair system using the install disk, but the problem still occurs.  I am not sure if I am doing the process correctly.

Any advice would be greatly appreciated.

Thanks

Mo

---

### Post by swisscow on 2007-07-19
When you boot up you get an option at GRUB to press a key - do that, choose the recovery/safe/ text option - sorry can't remember what it is.

This should boot you to a command line

At the command line login as normal

then type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If it doesn't do anything type

 ```
cd /etc/X11
```

(note the capital letters in X11) then repeat the earlier command.

This will allow you to run through and choose correct options (it may do it automatically) for your video card and monitor etc.

then reboot as normal and see what happens

Hope this helps

---

### Post by moallen on 2007-07-19
Hi Swisscow,

You is the dude.  That worked.

Thanks for your help

Mo

---

### Post by swisscow on 2007-07-19
Excellent news, glad to help

---

