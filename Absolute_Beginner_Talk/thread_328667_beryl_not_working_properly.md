---
title: "beryl not working properly"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by tc48 on 2006-12-31
Hello,

I just started using ubuntu today.  I went to install xgl and beryl to get all those cool effects, beryl loads up, and I get the splash screen and some effects.  But my windows no longer have the close minimize or maximize buttons!  And I cant move them on the screen.  Also when I try to change the session to XGL on the logon screen, when I login I just get a blank screen.  I can only login in the default, where the window problems mentioned earlier occur.  During the install I got a message that the xserver package could not be found... And now it still prompts me to install and upgrade but when I hit install updates it says

> W: Failed to fetch [http://beryl-mirror.pricechild.co.uk/pool/edgy/main/xserver-xgl/xserver-xgl_7.0.0.git.20060725-0ubuntu2.1_i386.deb](http://beryl-mirror.pricechild.co.uk/pool/edgy/main/xserver-xgl/xserver-xgl_7.0.0.git.20060725-0ubuntu2.1_i386.deb)
  Size mismatch


What am I doing wrong and what do I have to do to get it running right?  Thanks.

---

### Post by tc48 on 2006-12-31
anyone?

---

### Post by Shiva88 on 2007-01-03
I too am having this problem- Beryl seems to be working properly, except that the entire title bar, including the close/minimize/maximize buttons, are missing from every window.  I've toyed around with the various plugins as suggested in other threads, but disabling them (the screenshot plugin and virtually every setting under "window management") hasn't helped.

Any ideas?  I know I've seen threads around here with similar issues, but I can't seem to find many concrete solutions.  Google-fu has failed me :(

---

### Post by kinematic on 2007-01-03
emerald --replace is the command to get the title bar with buttons.
if you add > beryl-managerto admin>prefs>sessions>startup programs you should start the next session with a "complete" beryl.
you can also place a starter for beryl-manager on your desktop so that you can switch between emerald and metacity.

---

### Post by Shiva88 on 2007-01-03
Thanks for the quick response.  

emerald --replace does nothing for me.

As far as switching between beryl and metacity, I can do that just fine via the beryl manager applet; switching back to metacity immediately restores my window frames, but switching back to beryl immediately removes them again.  Also when in Beryl, I can't even get a usable terminal- running terminal gives me an empty (useless) white box where the terminal should be.

I'm a little confused about your advice to add that line to my startup- as far as I can tell, my problem isn't getting Beryl started, it's getting it to function properly once started.  Or am I missing something?

For what it's worth, I used this guide to get beryl "functioning" as it is now:
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

This is on an HP laptop with a Geforce Go7200 video card, and beryl works fine under Sabayon, so I know that it's at least possible to get it running on this machine.

---

### Post by gentlemanmasher on 2007-01-03
I had the same problem right away and by putting in beryl-manager in the terminal it fixed my problem.

---

### Post by Shiva88 on 2007-01-03
Issue resolved!  I edited my xorg.conf file and changed DefaultDepth from 16 to 24 in Section "Screen".   

Viola!  Beryl looks great, except I then had issues with windows appearing with no contents, just solid black space.  (Ironically, almost the exact opposite issue I'd had before- now I had titlebars,  but no content!)  I was able to resolve this by right-clicking on the beryl applet, and going to Advanced Beryl options > Rendering Platform > Force AIGLX.

Everything's peachy now!

---

### Post by sabertooth_cat on 2007-01-03
Thanks Shiva88, 

I just did "Advanced Beryl options > Rendering Platform > Force AIGLX", without editing xorg.conf, and it solved the "missing title bar" problem.

---

### Post by morphet on 2007-02-13
Yeah, Man, Thanks. I'll try that.

---

### Post by theorem_hunter on 2007-02-23
forcing AIGLX has not done the trick for me but i feel im getting close (using a ATI X700) :(

---

### Post by theorem_hunter on 2007-02-23
sorry... reloading window decorator fixes the problem (im so happy i dont have to trash my ATI card... yet)

---

