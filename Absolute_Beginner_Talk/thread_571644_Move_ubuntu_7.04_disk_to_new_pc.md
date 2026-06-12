---
title: "Move ubuntu 7.04 disk to new pc?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by neander on 2007-10-09
I have a not so complex ubuntu setup installed on a pc that is a little under powered. I will be getting a new pc (buidling) and wonder if there is any chance that I can just move the ubuntu disk to the new pc without reinstalling everything? I doubt it, but want to ask. Moving from Athlon 3200 to Intel dual core 6800. 

If I attempted I'd try to undo the video driver changes that I made to get decent screen res on the current box. But I still tend to guess that there might be too many differences for it to just take of in the new environment.

---

### Post by dptxp on 2007-10-09
> **neander said:**
> I have a not so complex ubuntu setup installed on a pc that is a little under powered. I will be getting a new pc (buidling) and wonder if there is any chance that I can just move the ubuntu disk to the new pc without reinstalling everything? I doubt it, but want to ask. Moving from Athlon 3200 to Intel dual core 6800. 

If I attempted I'd try to undo the video driver changes that I made to get decent screen res on the current box. But I still tend to guess that there might be too many differences for it to just take of in the new environment.

A fresh installation shall save you a lot of time and shall be clean.
Maybe you install Gutsy (7.10) in the new machine.

---

### Post by louieb on 2007-10-09
I've dropped  a drive w/Ubuntu 6.06.1 installed on it into another machine  before. And after running **sudo dpkg-reconfigure xserver-xorg **the GUI came up. Don't know if thats all you'd have to with Feisty   may have to mess with the **uuid**'s in /boot/grub/menu.lst and /etc/fstab. 

It can't hurt to try. Worst come to worst it just a fresh install to fix it.

---

### Post by mivo on 2007-10-09
Moving over the /home directory is not a problem, but I would not try to move the core installation Too many hardware related configurations that would need to be adjusted. Your personal files and application settings are saved in /home and these are generally system independent.

---

### Post by neander on 2007-10-09
OK, thanks everyone. I think in my case a full redo is not so hard and with this feeback maybe I'll just bite that bullet.

Gutsy is not quite out the gate yet? At least it's not presented front and center on the dl page. However I'd be game if it's nearly out of beta or whatever the stage it's in now is called.

---

### Post by mivo on 2007-10-09
I went from Gutsy back to Feisty, but that may just have been my system. Look at the development forum below for an idea what works and what doesn't. Personally, I would wait the less than two weeks until release. Or at least until the release candidate that should come out in a few days. Then again, if it's a new box and there is nothing to lose, it's certainly worth a try. :) Gutsy is a definite step up.

---

### Post by mike555 on 2007-10-09
You could use " Apt-on-CD " to copy all your installed aps and such onto a CD and then when you install on a new computer just pop in the CD and install from it , instead of downloading everything again ......

---

### Post by neander on 2007-10-09
Interesting stuff...I may be able to wait for Gutsy if it's that close. 

Apt-on-CD, does it copy all apps with data (mysql etc) 'as-is'? Never had exposure it Apt-on-CD, and then I suppose it restores? Does it match the config one has in the original mysql on the restore?

---

