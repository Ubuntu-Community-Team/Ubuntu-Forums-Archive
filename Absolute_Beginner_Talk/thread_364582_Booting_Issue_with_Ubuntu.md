---
title: "Booting Issue with Ubuntu"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Ovid on 2007-02-18
I'm having problems with booting Ubuntu. I installed it yesterday and worked just fine. I think I booted 3 times yesterday and never had any problems. I shutdown and go to sleep and get up in the morning and now it won't boot. I chose ubuntu at the operating system screen as the operating system i want to boot. The loading screen comes up and once it gets to 100% it goes black. It acts as if it's trying to go to the login screen, but it doesn't. My specs are 1.80ghz x64, 1 gig ram, and nvidia 6600 gt. I don't see how it would be my video card because didn't have any problems before. Thanks for any help.

---

### Post by taurus on 2007-02-18
I bet it's X.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```
If you are not sure about an answer, just use a default and perhaps pick **vesa** driver until you get X running again.  Then, reinstall nvidia driver for your graphic card.

---

### Post by Ovid on 2007-02-18
Thanks a bunch, that fixed it.

---

### Post by Ovid on 2007-02-19
Well, I thought it was fixed, but I have the same problem again after waking up this morning. I entered the command "dpkg-reconfigure xerver-xorg" and it says unrecognized command.

---

### Post by taurus on 2007-02-19
> **Ovid said:**
> Well, I thought it was fixed, but I have the same problem again after waking up this morning. I entered the command "dpkg-reconfigure **xerver**-xorg" and it says unrecognized command.

It should be

```
dpkg-reconfigure xserver-xorg
```
And why do you have to run it again since it fixed the problem before?

---

### Post by Ovid on 2007-02-19
yeah i entered it in without the "" and it said unrecognized.. I didn't have to enter that command last time. All I did was put in my Live CD and booted that up. Restarted my computer without the CD and it loaded up fine..tried that again and didn't get the same result

---

### Post by taurus on 2007-02-19
Look at my previous post again especially the word that I have highlighted from your post.

---

### Post by Ovid on 2007-02-19
Yeah that was just a typo in this forum, but i typed that in correctly in the command line and i double checked on that like 5 times. Would the command not being recognized have anything to do with me using gnome or edgy whatever?

And is there anything i should be typing before i put in that code? Should the command be starting off like this     grub> dpkg-reconfigure xserver-xorg

---

