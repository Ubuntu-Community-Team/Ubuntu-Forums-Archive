---
title: "Resolution Issue"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by ABCgang on 2007-12-30
I attempted to change my screen resolution via the "sudo dpkg-reconfigure xserver-xorg" command and now have a black screen that has a small light blue box that states:

[B]out of range
set monitor to:
1024x768 @ 60hz[/B]

My problem is I can't figure out how to return to the terminal to re-set the resolution, much less anything else as it's stuck on this page.  I have turned off the computer, but the same screen continues to pop-up.

Any ideas on how to return to the home page?  Thanks

---

### Post by LaRoza on 2007-12-30
Can you boot into recover mode?

Can you see grub?

---

### Post by ABCgang on 2007-12-30
Thanks for the speedy response LaRoza.

**Can you boot into recover mode?**

Not quite sure where to do this? 

**Can you see grub? **

When Ubuntu starts up, I briefly see GRUB mentioned, then it proceeds with the loading, starting, checking phase of logging on.  Once it's finished with that, the blue box ops-up again.

---

### Post by rahimveron on 2007-12-30
The recovery mode is the 2nd option in the Grub Menu while booting like this line```
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
```

---

### Post by LaRoza on 2007-12-30
> **ABCgang said:**
> Thanks for the speedy response LaRoza.

**Can you boot into recover mode?**

Not quite sure where to do this? 

**Can you see grub? **

When Ubuntu starts up, I briefly see GRUB mentioned, then it proceeds with the loading, starting, checking phase of logging on.  Once it's finished with that, the blue box ops-up again.

Press Esc when you see the message. Then chose the recovery option.

Log in and run:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by ABCgang on 2007-12-30
**rahimveron,**
Thanks, I found my way into recovery mode with your directions.

**LaRoza,**
I typed in "sudo dpkg-reconfigure -phigh xserver-xorg" and it went thru the motions of checking the system.  In the end it stated "xsever-org" is not installed and that the command was not found.  :confused:

Right now it's a black screen blinking for a command.  :)  Any further ideas?

---

### Post by LaRoza on 2007-12-30
server, not sever, and xorg, not org.

If it is a type in your post (and not in the command)

```

sudo apt-get install ubuntu-desktop

```

However, I think you just mistyped the command.

---

### Post by ABCgang on 2007-12-30
Thanks to both LaRoza and rahimveron for your help.

I decided to type in "sudo dpkg-reconfigure xserver-xorg" at that last command prompt and it took me back to where I could change my resolution to meet the requirements of my monitor.  It's up and running now with your help.

Thanks again for the speedy assistance.  Wes

---

### Post by LaRoza on 2007-12-30
> **ABCgang said:**
> Thanks to both LaRoza and rahimveron for your help.

I decided to type in "sudo dpkg-reconfigure xserver-xorg" at that last command prompt and it took me back to where I could change my resolution to meet the requirements of my monitor.  It's up and running now with your help.

Thanks again for the speedy assistance.  Wes

No problem :)

Typos are easily, especially with that command.

---

