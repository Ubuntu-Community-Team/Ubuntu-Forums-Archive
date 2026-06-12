---
title: "Half-Life 2 and Counter-Strike Source"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-16
So, I was playing regular cs 1.6 through wine and I have no troubles, but I am with HL2 and CSSource. THe problem being that when I go to load them they come up and for a bit I see the splash screen but then it goes to a black screen and i can hear the mouse roll over options as I move it around while its loaded. I understand I probably need to lower the graphics resolution down a bit but how can I do that? I run Steam through Wine, now CS 1.6, so far has been the only one that does this. Any help is greatly appreciated!! :)

---

### Post by echo $USER on 2007-05-16
Try this...

WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 800 -height 600 -applaunch 240 \
    -heapsize 512000 +map_background none "$@"

---

### Post by Tumpster on 2007-05-16
Where would I put that echo? I'm new to wine, I installed WIne and selected the steam.exe file and told it to open with wine.

---

### Post by echo $USER on 2007-05-17
> **Tumpster said:**
> Where would I put that echo? I'm new to wine, I installed WIne and selected the steam.exe file and told it to open with wine.

Just copy and paste into terminal... check this out can explain better than I...

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by Tumpster on 2007-05-17
I did that but it still went to black. I mean I see the screen as usuall but after like 5-30 seconds of it saying waiting and showing me the HL2 or CS Source screen it goes to a black screen but I can hear it as I roll my cursor over the selelctions. Anyone have some advice? Thanks!@

---

### Post by to4i on 2007-05-17
Try to add -dxlevel 70 in the terminal, or -dxlevel 80....

---

### Post by echo $USER on 2007-05-17
> **to4i said:**
> Try to add -dxlevel 70 in the terminal, or -dxlevel 80....

good call

---

### Post by Tumpster on 2007-05-17
Ok, that got it up and running for CS Source, is there anything different I need to do for Half-LIfe 2?

---

### Post by _mOrgoth_ on 2007-05-17
I did one little experiment, before css I installed dx9 using wine. When I started CSS it works great!!! I just had to set same resolution in CSS sa in ubuntu. If they are different, when I exit CSS system freez

---

### Post by mrfuzzemz on 2007-05-19
> **_mOrgoth_ said:**
> I did one little experiment, before css I installed dx9 using wine. When I started CSS it works great!!! I just had to set same resolution in CSS sa in ubuntu. If they are different, when I exit CSS system freez

Wow.  I never thought of that.  I'm going to give that a try.

---

### Post by Tumpster on 2007-05-22
I'm still having HL2 problems, it goes to a black screen after a while even though I can hear everything. What can I do to run HL2 like I was able to run CSSource? Thanks!

---

### Post by Tumpster on 2007-08-06
Bump!!!

---

