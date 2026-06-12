---
title: "Ubuntu Slow"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by ART_Adventures on 2006-09-03
Hello People,

I am new to Linux, being mainly a Windows users, and I decided to install Linux on my older secondary machine to see what it was like.

Ubuntu installs correctly, though when it mentions about installing hardware drivers it says something about not being able to reserve a region, and claims about upgrading my bios. Now, I notice when using the OS, it works very, very slowly- everything redraws slow and it takes a long time for things to appear on the screen and for the system to boot. The system spec is:

Pentium 3
256MB RAM
ATI Rage

Can anybody help? Could it be something to do with graphics card drviers? Though, I'm not sure how to update things like this on linux, and I'm not familar with the shell (command prompt) on this OS.

Thanks.

---

### Post by ART_Adventures on 2006-09-04
Is anybody able to help?

---

### Post by handy on 2006-09-04
Search the forum's for **ATI**, you will eventually find out the best procedure for installing drivers for it.

I can't help you, I have only ever set up nVidia...

You might find what you need in one of the following links?

[http://ubuntuforums.org/showthread.php?t=221320](http://ubuntuforums.org/showthread.php?t=221320)

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

Also, posting in the **Hardware Help / Video & Sound** sub forums will probably get you more responses, to any future questions that you may have, after looking at the above links... :) 

All the best...

---

### Post by 3rdalbum on 2006-09-04
Try this:

Open the terminal and type:

```
sudo nano /etc/X11/xorg.conf
```

(that's a capital X in X11).

In the line that says Load "DRI", put a hash (#) before the line. So now it should say #Load   "DRI".

Now scroll down to the bottom of the file, where it says Section "DRI". Put a hash at the beginning of this line, the next line, and so on until the end of the file.

Press Control-X to exit, Y to save, then Enter to confirm. Now restart the computer. This might fix your problem.

---

