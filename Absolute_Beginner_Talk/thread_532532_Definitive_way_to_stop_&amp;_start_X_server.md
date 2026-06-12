---
title: "Definitive way to stop &amp; start X server"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-22
Well, I dove in and downloaded the nvidia driver and installed it myself, but I kinda futzed around aimlessly for a while. I did ctrl+alt+F1 and got a CLI, then tried to install it but it complained about the X server running. I tried gdm stop, and that didn't work, then init 1, which got me to run level 1?, then I tried again and it installed but it did complain that I should be in run level 3. But when I typed init 3, I got back into the GUI???

Sooooo,

Can someone tell me the definitive steps to exit out of the GUI, get to run level 3 like the nvidia driver wants, and then get the x server going again? I managed (yay!) but it wasn't pretty.

---

### Post by mrfelker on 2007-08-22
Ubuntu will install the nVidia drivers through Synaptic (under System Administration.  Installing the drivers directly from the command is very difficult.

---

### Post by mikex on 2007-08-22
> **mrfelker said:**
> Ubuntu will install the nVidia drivers through Synaptic (under System Administration.  Installing the drivers directly from the command is very difficult.

Yes it is, well it wasn't *that *bad, but i want to learn a little more about it on my own.

---

### Post by mikewhatever on 2007-08-22
sudo /etc/init.d/gdm stop

---

### Post by rolf-c on 2007-08-22
What mike said, and you can also restart X on the fly by issuing CTRL-ALT-BACKSPACE.

---

### Post by HermanAB on 2007-08-22
You should use 'init 3' and 'init 5' to switch between running with/without X.

To restart X, simply press 'ctrl-alt-del'.

Hope that helps!

Herman

---

### Post by Hobo Joe on 2007-08-22
Use Envy for drivers. It's easy and fast!

I have a link in my sig.

---

### Post by dwhitney67 on 2007-08-22
I may be wrong on this, but I think another "brutal" way to kill the X server (after you have switched to an alternate virtual terminal) is to run the following command:

[FONT="Courier New"]$ sudo pkill X[/FONT]

or

[FONT="Courier New"]$ sudo kill `ps -e | grep Xorg | cut -d " " -f2`[/FONT]

Btw, I'm surprised Ubuntu 7.04 is still running X11R6 and has not begun using X11R7.

---

### Post by mikex on 2007-08-22
> **HermanAB said:**
> You should use 'init 3' and 'init 5' to switch between running with/without X.

To restart X, simply press 'ctrl-alt-del'.

Hope that helps!

Herman

Still a bit confused though. What does init 3 & init 5 do different than ctrl+alt+del and ctrl+alt+backspace and we still have ctrl+alt+f1 and ctrl+alt+f7, gdm stop, and gdm start. are some of these doing the same thing as others?

---

### Post by mikewhatever on 2007-08-22
> **rolf-c said:**
> What mike said, and you can also restart X on the fly by issuing CTRL-ALT-BACKSPACE.

PS:Another way is to boot into recovery mode. In that case, X never gets started.

---

