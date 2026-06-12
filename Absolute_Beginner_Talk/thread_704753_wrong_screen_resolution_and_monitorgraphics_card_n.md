---
title: "wrong screen resolution and monitor/graphics card not detected."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by ricardo_dreamlifter on 2008-02-22
Hello, I'm new here. Yeah, another newbie for you all. Well, I installed Ubuntu 7.10 some days ago, but the highest resolution i get is 800x600 and in low graphics mode. My monitor is a Compaq S720 and the graphics card an Intel 82810E. However, Ubuntu won't detect any of them, treating the monitor as a Generic Plug 'n Play monitor and the graphics card as a Generic VESA graphics card or something like that. What can I do there? This has probably been discussed before, but I'd like to have my own answers.
So well, thanks in advance for any help you're willing to give :)

+RR+

---

### Post by taurus on 2008-02-22
Would it detect your graphic card/monitor if you reconfigure your X server again?

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure xserver-xorg
```
Once you are done with it, restart your X server with <Ctrl><Alt>Backspace.

p.s.  If you are not sure about a question, just take the default.  Try using intel driver if it's on the list.  Otherwise, pick i810.

---

### Post by ricardo_dreamlifter on 2008-02-22
I've enetered that code in the terminal before, but it asks for a password or something, and I enter the admin passowrd fast because if I do it slow it like automatically presses enter and sasy "Invalid password" or something like that.

---

### Post by taurus on 2008-02-22
If you are the user that you created during the installing process, then you just use the same password that you log in with.  One thing to keep in mind is that when you type in your password, it won't show any echo so make sure you type it right and hit the Return key.

---

### Post by ricardo_dreamlifter on 2008-02-23
Hey thank you really much, it did work now. Cheers.

+RR+

---

