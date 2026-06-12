---
title: "Desktop Effects won't cube"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by yigals on 2007-04-24
At first when I enabled Desktop Effects everything works fine (except for a blank line instead of top border of Firefox, but I can live with that), but after a short while the four desktop buttons at the bottom right became one and I couldn't cube no more. Disabling and enabling won't help, neither restart.

---

### Post by Ziox on 2007-04-24
you need to add more viewports.  Right click the desktop button > preferences > and select 4 workspaces

---

### Post by yigals on 2007-04-24
Doing so adds more desktop buttons, but not giving the cube effects even though the option is still enabled.

---

### Post by yigals on 2007-04-25
I understand that there is no solution?

I have Thinkpad T30, P4 m 1.8 Ghz, 512 RAM, 16 MB ATI Radeon 7500.
Is it recommended for me to install compiz/beryl with such hardware config.?

---

### Post by kvonb on 2007-04-25
Install compiz-gnome-manager, just search for that in synaptic, or rather just search for compiz, you will find a few more goodies to install.

By creating more desktops you are actually creating more copies of the cube!

The desktop switcher will show one long bar instead of seperate boxes because Compiz actually makes one long desktop, but divides it into 4 (or whatever number you select).

That's why it looks odd :).

PS. If you want better control over the cube, ie rotating it with full control using the mouse, install Beryl and use that instead of Compiz.  Compiz is a cut down, very basic effects manager, Beryl goes the whole hog :).

---

### Post by phr0ze on 2007-04-25
This happened to me. It happened when I was playing around with themes. The cube would not come back. Here is what you do.

Turn off the cube effect.
Add 3 more panes on the desktop manager. (You must have 4)
Turn the cube effect back on.

Let me know if this works.

---

### Post by RomeReactor on 2007-04-25
Hi. I think kvonb's solution is best; after installing **gnome-compiz-manager** you can find it in "System-->Preferences-->GL Desktop"; open it, go to the "Workspaces" tab, and select **Number of viewports: 4** (or your desired number).

---

### Post by Average Joe on 2007-04-25
I had exactly the same problem as yigals describes. First the cube worked, then it suddenly stopped working.

But the solution of phr0ze worked fine for me. I got my cube back! :)

Edit: I also installed the gnome-compiz-manager, as kvonb suggested. That gives indeed a bit more to tweak on the compiz settings.

---

### Post by yigals on 2007-04-26
Yep, installing gnome-compiz-manager worked for me as well.
Now I can't stop playing with the extra settings :)

---

### Post by jcrow on 2007-04-26
I had the same thing happen. I followed the post above and turned off the cube in the desktop effects menu, changed to four workspaces, then turned the cube back on and everything worked. I will try installing the Compiz manager as it looks like there are more settings to play with.

---

