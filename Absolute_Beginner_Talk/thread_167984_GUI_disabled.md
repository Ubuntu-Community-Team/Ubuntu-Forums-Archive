---
title: "GUI disabled"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by bobonthenet on 2006-04-29
It seems I have somehow disabled the GUI for ubuntu.  When I try and boot up ubuntu it looks like its doing its normal thing with the loading screen but then after thats done it takes me to an all black screen with a login option.  It appears to be just the terminal like dos or something.  I can log in but since I'm an absolute noob and don't know any commands its pretty useless to me right now.  I know I must have done something to cause this, probably when I was deleting stuff I didn't think I needed with the synaptic package manager.  What do I do to make the GUI come back again?

---

### Post by mostwanted on 2006-04-29
[QUOTE=bobonthenet]It seems I have somehow disabled the GUI for ubuntu.  When I try and boot up ubuntu it looks like its doing its normal thing with the loading screen but then after thats done it takes me to an all black screen with a login option.  It appears to be just the terminal like dos or something.  I can log in but since I'm an absolute noob and don't know any commands its pretty useless to me right now.  I know I must have done something to cause this, probably when I was deleting stuff I didn't think I needed with the synaptic package manager.  What do I do to make the GUI come back again?[/QUOTE]

Could be your x server that is messed up. Try running the command:

```
startx
```

That should start X (the GUI). If it works, well there's at least a temporary solution. If it doesn't do that, throwing some errors, run this to reconfigure your X server:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bobonthenet on 2006-04-29
thanks for your quick reply, I tried what you said and as you had indicated it might I got some errors when typing startx so I tried that second thing you said to do sudo dpkg-reconfigure xserver-xorg, I got errors with that too.  Something about a conflict with something I should have written down and then some other options to try when using the dpkg command.  Unfortunatly the GUI is still disabled but I think your help is on the right track.

---

### Post by zaba on 2006-04-30
```
dpkg -a
```

might be what you are looking for. 

Since startx isn't doing much for you, you might just try typing:
```
gdm
```

after you have logged in. 

Have you been using Ubuntu for long? If not, you might just want to do a complete re-install. (Obviously, not the best answer... it's so... Windows! :mrgreen: ). 

If you have been using Ubuntu for a while, and hope to save all of your data, "sudo apt-get install" could become your new best friend. If typing gdm at the command line doesn't bring everything up like it should, you can sudo apt-get install gdm and that should at least get you a gui again. 

(Of course, it now probably goes without saying that removing things via synaptic without being sure that you need them is not the wisest idea. :mrgreen: )

---

