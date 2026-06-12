---
title: "Gnome interface problems"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2006-12-19
I need some help (yeah, you probably guessed that already :))
 
 I recently tried to install compiz. It didn't work out very well, due to my graphics card not being set up completely. So, I figured I'd just remove it with aptitude and stay with gnome for the moment. removing it went fine, but (and this is the problem :)) when I book into gnome, there is no window borders and the bottom panel that used to show my window manager is empty, apart from the trash bin. So, is there a "restore default gnome setup" magic button somewhere, or is it the hard way with manually adding all the gnome apps to the star-up again?

Thanks in advance.

---

### Post by MarkTX on 2006-12-19
I had this same problem when i tried to uninstall Beryl.  I lost all controls and couldn't do anything but boot into Terminal mode.

In the end, i edited /etc/X11/xorg.conf but i wouldn't recommend this because even though it worked for me, it messed up my display configuration which was a pain to reconfigure.

If anyone does have an 'easy' restore default magic button, i'd sure like to know it too!

---

### Post by Big_Croc7 on 2006-12-19
If you're happy using apt-get from the command line (or you have another window manager installed as well as gnome) you could possibly uninstall gnome then install it again? Though that might be more work than adding them manually, but if you still have the package files somewhere (so you don't have to download them) it might not take too long.

---

