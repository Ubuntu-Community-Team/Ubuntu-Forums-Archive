---
title: "mplayer troubles"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by blackjack6.21.91 on 2006-05-10
i've used mplayer for a long time and i've always wanted to be able to use fullscreen in the way that it does in totem (where it actually stretches the movie to fill the screen)

is there a way to do this?

if i'm not clear just tell me,
blackjack

---

### Post by r4ik on 2006-05-10
Hi,
Try change video driver to xv in mplayer.

Good luck !

---

### Post by gabruo on 2006-05-10
Got this from a post sometime ago, but it worked great for me when I had the problem.Just open a terminal and...

                      echo "zoom=yes" >> ~/.mplayer/config

---

### Post by nanotube on 2006-05-10
as r4ik says, using xv should do the trick. here is an excerpt from my ubuntu howto (first link in my sig), with more detail.

> Once you have your MPlayer installed, run it, right click and choose preferences, choose the Video tab, and select "Enable double buffering" and "Enable direct rendering" checkboxes, and also choose "xv" from the available drivers list. Why, use xv instead of the default x11, you ask? Well, for one - this makes the video resizing, and the "fullscreen" option work correctly. With x11, the window expands, but the video continues playing at its normal size.

---

