---
title: "[SOLVED] Unable to use Evolution Setup Assistant"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-07-09
I've just installed Ubuntu 7.04 (Feisty Fawn) and am unable to use the setup assistant for Evolution Mail because it runs off screen bottom, hiding the "Forward" button and thus rendering the setup assistant useless.  I've tried moving it, but it simply butts up against the top of the main window and won't move vertically upward.

I'd really like to be able to receive and send electronic mail, so if anyone knows how I can get the Evolution Setup Assistant to fit inside the window (as it should in the first place) I would greatly appreciate your letting me know.  I thought about upping the resolution from 800 X 600, but the higher resolution does not appear in the relevant menu.

Thank you for any help you can provide.  I must say, I'm quite surprised to be the first and only person to encounter this bamboozling problem!

:confused:

=^..^=

---

### Post by tgoose on 2007-07-09
A quick fix (I think) is to hold down a key and then clicking and dragging the window. Depending on your computer, it's probably either Alt or the Windows/Apple key.

That way, you don't have to drag the title bar, you can drag anywhere on the window and won't hit the top of the screen!

It should be possible to add extra resolutions but it's been a long time since I had to so I can't remember how!

---

### Post by bigken on 2007-07-09
in a terminal type

sudo dpkg-reconfigure -phigh xsever-xorg 

select your video driver and use the arrow keys and space bar to select your  resolutions

---

### Post by bigken on 2007-07-09
> **Flyvapnet said:**
> I've just installed Ubuntu 7.04 (Feisty Fawn) and am unable to use the setup assistant for Evolution Mail because it runs off screen bottom, hiding the "Forward" button and thus rendering the setup assistant useless.  I've tried moving it, but it simply butts up against the top of the main window and won't move vertically upward.

I'd really like to be able to receive and send electronic mail, so if anyone knows how I can get the Evolution Setup Assistant to fit inside the window (as it should in the first place) I would greatly appreciate your letting me know.  I thought about upping the resolution from 800 X 600, but the higher resolution does not appear in the relevant menu.

[B] Thank you for any help you can provide.  I must say, I'm quite surprised to be the first and only person to encounter this bamboozling problem!

[/B] 
:confused:

=^..^=
thats probablys because your the only one using 800x600

---

### Post by Flyvapnet on 2007-07-09
Thank you, **bigken** and **tgoose**, for your replies.  Well, I finally managed to get a peek at the shy "Forward" button by checking the "Always on top" option and switching the stubborn thing to a different workspace.  So I'm back in the e-mail business and this problem, though not solved in a technical sense, is no longer a problem -- for now.

;)

=^..^=

---

### Post by bigken on 2007-07-09
:lolflag:pleased your up and running

---

