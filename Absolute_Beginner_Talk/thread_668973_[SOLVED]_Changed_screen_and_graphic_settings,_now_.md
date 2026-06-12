---
title: "[SOLVED] Changed screen and graphic settings, now stuck"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-01-16
I'm using a Radeon x1900 xt along with a Samsung Syncmaster 204t and a television hooked up to the S-Video Out on Gutsy 64-bit. Recently, I tried for the first time to see how the television works as a second output in Ubuntu. In Windows XP it works except that it makes certain operations too slow. 

Now I've gone back to only wanting to use one monitor, but apparently what little I did in Ubuntu has caused some change that I can't change back! Help!

All I did was the following: I went to System -> Administration -> Screen and Graphics. I clicked Screen 2 and changed it to Default. It asked me to restart my computer, and since then I've been stuck in low graphics mode, and don't know how to get out! :(

On the Graphics Card tab it's showing vesa - I'm pretty sure I was using fglrx before, but now when I pick it, it has no effect - the desktop doesn't change and when I close and open the Screen and Graphics window, it's back to vesa.:mad:

I don't care about getting the television to work, really I'd just like to go back to full resolution and compiz. I'd really appreciate any help! Thanks!!

---

### Post by amingv on 2008-01-16
Have you tried doing this: press Ctrl+Alt+F1, it will switch you to a full shell mode, then type:

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you for some settings to reconfigure your display, then use Ctrl+Alt+F7 to go back to graphic mode and finally Ctrl+Alt+Backspace to restart X. That should do it.

---

### Post by dinostabOMG on 2008-01-16
Thank you kindly! This worked.

---

