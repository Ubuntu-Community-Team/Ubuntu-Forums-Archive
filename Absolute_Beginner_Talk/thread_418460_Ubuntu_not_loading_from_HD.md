---
title: "Ubuntu not loading from HD"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by fdubru on 2007-04-22
Hello,


I have just downloaded the laster version of Ubuntu (Ubuntu 7.04, Feisty Fawn!

). I tested it from the CD with a Dell Optiplex 320 without problem so I did proceed further with a full installation on the hard drive. Unfortunately, the OS does not load at all. After choosing Ubuntu from the menu, I on gather a back screen.

Any suggestion?

Thanks,
Fred.

---

### Post by SOULRiDER on 2007-04-22
Do you get any errors? Have you tried recovery mode?

---

### Post by taurus on 2007-04-22
See if you can boot into recovery mode from GRUB menu.  Then, try to reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you're not sure about a question, just use the default and use **vesa** as the driver for your graphic card for now.  When done, reboot with

```
shutdown -r now
```

---

### Post by Crosbie on 2007-04-22
You choose Ubuntu - from a menu which says 'Grub'?

What other options do you have?

Is it always and only black, or do you see any information first?

If you have the option to choose 'recovery mode', try that.  It will give you a command line - you might have trouble with the X server configuration.

---

### Post by amaroKer on 2007-04-22
In GRUB, select your top boot option, and press 'e' instead of 'enter'.  Edit the long line (3rd i think) and take out "quiet splash".  Press 'enter' to go to the previous screen, then press 'b' to boot.  Do not worry, these changes are not permanent (one boot only).  You should see a bunch of lines during boot after this.  See what one it stops on, and post back.

Hope this helps!

Logan

---

### Post by fdubru on 2007-04-22
I have 3 booting options:

[LIST]
[*]Ubuntu, Kernel -2-6-20-generic
[*]Ubuntu, Kernel -2-6-20-generic (Recovery Mode)
[*]Ubuntu memtest 86+
[/LIST]

Whatever option I choose, the screen turns black with a white cursor at the top left. I have no option to input anything.

Cheers,
Fred

---

### Post by taurus on 2007-04-22
Ubuntu, Kernel -2-6-20-generic (Recovery Mode)

Then, reconfigure your X again as in my previous post.

---

### Post by fdubru on 2007-04-22
Hi Taurus,

The recovery Mode does not help. I have the same black screen.

Fred

---

### Post by fdubru on 2007-04-22
Hi Logan,

I just tried what you suggested, but same problem. No error message, no post. Nothing at all. I believe that the HD is not even access at all?

Cheers,
Fred

---

### Post by PFMoreno on 2007-05-08
This thread has some shell instructions to follow that didn't work for me, but someone else listed he was able to get it to work if he used the Lilo boot loader and that worked for him.  Those instructions are on page two.  I'm going to give that a try next.

---

