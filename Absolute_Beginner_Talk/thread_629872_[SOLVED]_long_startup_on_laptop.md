---
title: "[SOLVED] long startup on laptop"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-12-02
I recently installed ubuntu gutsy on my laptop, but when I start my computer it takes about 5-10min where I see nothing but a black screen (which can be annoying some times)
at first I thought that it was because I had installed advanced desktop effects, but it makes no difference at all if I turn it off
after this "black screen" thing it runs like a dream (not surprised that it would :) )
please help :(

Packard Bell:
2GB ram
2GHz
80GB disk space
don't know if this helps, but I'm always being told to be a bit specific about everything :)

---

### Post by GSF1200S on 2007-12-02
> **Fanin said:**
> I recently installed ubuntu gutsy on my laptop, but when I start my computer it takes about 5-10min where I see nothing but a black screen (which can be annoying some times)
at first I thought that it was because I had installed advanced desktop effects, but it makes no difference at all if I turn it off
after this "black screen" thing it runs like a dream (not surprised that it would :) )
please help :(

Packard Bell:
2GB ram
2GHz
80GB disk space
don't know if this helps, but I'm always being told to be a bit specific about everything :)

When grub comes up (what allows you to select the kernel to boot or windows), load the recovery kernel and watch the boot process. It will tell you what the kernel is doing, and just see where the hang is. To get a gui after the kernel boots up, type in:

```
sudo /etc/init.d/gdm restart
```

Report back and tell us what the hang is. I had ndiswrapper doing this to me on another comp. There was actually a bug in Feisty beta where Ubuntu hung at the network manager for a little bit, but that was quickly resolved...

**EDIT** Im not sure if Ubuntu has this as I run kde core on it right now, but some distros allow you to push a button to hide the loading screens and show you what the kernel is doing.. Alternatively you can use the recovery version selected from grub as I said and it should at least show you where the hang is...

---

### Post by Fanin on 2007-12-02
> **GSF1200S said:**
> When grub comes up (what allows you to select the kernel to boot or windows), load the recovery kernel and watch the boot process. It will tell you what the kernel is doing, and just see where the hang is. To get a gui after the kernel boots up, type in:

```
sudo /etc/init.d/gdm restart
```

Report back and tell us what the hang is. I had ndiswrapper doing this to me on another comp. There was actually a bug in Feisty beta where Ubuntu hung at the network manager for a little bit, but that was quickly resolved...

**EDIT** Im not sure if Ubuntu has this as I run kde core on it right now, but some distros allow you to push a button to hide the loading screens and show you what the kernel is doing.. Alternatively you can use the recovery version selected from grub as I said and it should at least show you where the hang is...

after typing that command in, it takes me to the desktop, but shows a pop up that says:

[B]"Internal error
failed to initialize HAL!"[/B]

what do you mean "show you where the hang is" ?
I guess I forgot to mention that I'm a complete noob.. sorry :)

---

### Post by GSF1200S on 2007-12-02
> **Fanin said:**
> after typing that command in, it takes me to the desktop, but shows a pop up that says:

[B]"Internal error
failed to initialize HAL!"[/B]

what do you mean "show you where the hang is" ?
I guess I forgot to mention that I'm a complete noob.. sorry :)

Nah, i just wasnt clear enough. You said it hangs at the "black screen..." Where is that exactly? Is it right before you get a login screen, or is it sometime earlier? Im not exactly sure what timeframe of the boot process you are referring to, so forgive me :). Usually a hang (or a period of time that is longer than it should) will happen while the kernel, or the core part of the OS, is loading.

So, I should have said to reboot the computer. Then when grub comes up (the screen that allows you to select Ubuntu or windows, if you have it), select the recovery mode option right under what you usually pick. Then, as the kernel loads, it will tell you what its working on. When it seems to freeze or stop loading, note what step its on. Now, with recovery mode, it will load to the kernel only! Youll be sitting at a command prompt scratching your head. Thats where the command I threw down helps- it loads the GUI. You may need to reboot again (if the lack of HAL affects things like a wireless card, etc), but prolly not.

Then, just let us know where it "hangs," and well do our best- i guess you could think of this as a means to collect more information rather than a fix. We kind of need to know where the problem is.. I hope I was a little more clear :)

---

### Post by Teknyk on 2007-12-02
possibly related to the usplash issue?
I had the same problem.
[http://ubuntuforums.org/showthread.php?t=579568](http://ubuntuforums.org/showthread.php?t=579568)


The steps here fixed mine
[http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

---

### Post by Fanin on 2007-12-02
> **GSF1200S said:**
> Nah, i just wasnt clear enough. You said it hangs at the "black screen..." Where is that exactly? Is it right before you get a login screen, or is it sometime earlier? Im not exactly sure what timeframe of the boot process you are referring to, so forgive me :). Usually a hang (or a period of time that is longer than it should) will happen while the kernel, or the core part of the OS, is loading.

So, I should have said to reboot the computer. Then when grub comes up (the screen that allows you to select Ubuntu or windows, if you have it), select the recovery mode option right under what you usually pick. Then, as the kernel loads, it will tell you what its working on. When it seems to freeze or stop loading, note what step its on. Now, with recovery mode, it will load to the kernel only! Youll be sitting at a command prompt scratching your head. Thats where the command I threw down helps- it loads the GUI. You may need to reboot again (if the lack of HAL affects things like a wireless card, etc), but prolly not.

Then, just let us know where it "hangs," and well do our best- i guess you could think of this as a means to collect more information rather than a fix. We kind of need to know where the problem is.. I hope I was a little more clear :)

the black screen is right before the login screen

when I enter the recovery mode, every thing seems to be OK (there are a whole bunch of ok's just flying by, until it reaches the point where I have to write commands n' stuff) the last line says "setting up console font and keymap [OK]"

oh and I did notice that the wireless was not working after I typed in that cmd :confused:

hope this answers some of your questions!

---

### Post by GSF1200S on 2007-12-02
> **Fanin said:**
> the black screen is right before the login screen

when I enter the recovery mode, every thing seems to be OK (there are a whole bunch of ok's just flying by, until it reaches the point where I have to write commands n' stuff) the last line says "setting up console font and keymap [OK]"

oh and I did notice that the wireless was not working after I typed in that cmd :confused:

hope this answers some of your questions!

Ok.. I think this is your problem as mentioned above:

[http://ubuntuforums.org/showthread.php?t=579568](http://ubuntuforums.org/showthread.php?t=579568)

I would follow the steps he said to fix it in his little post (also above).

If you need any help with commands to access those files that are modified, let us know :)

**EDIT** Oh, and the wireless card didnt work because the Hardware Abstraction Layer wasnt initialized. Youll have to reboot for that one to fix.. just do a normal boot.

good luck!

---

### Post by Teknyk on 2007-12-02
> **GSF1200S said:**
> 
I would follow the steps he said to fix it in his little post (also above).


The credit for that fix isn't mine. Those are the posts I found that were applicable to my issue and resolved it is all.

---

### Post by Fanin on 2007-12-02
starts super fast now.. thanks guys :):):)

---

### Post by Teknyk on 2007-12-02
sweet! I actually managed to help someone :D

can you mark this thread resolved Fanin?

---

### Post by Fanin on 2007-12-02
there you go :lolflag:

---

### Post by GSF1200S on 2007-12-02
Awesome.. good job Tek ;)

---

### Post by Fanin on 2007-12-02
> **GSF1200S said:**
> Awesome.. good job Tek ;)

thanks to you too man :)

---

