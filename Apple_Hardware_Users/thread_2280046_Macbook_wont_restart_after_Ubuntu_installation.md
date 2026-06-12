---
title: "Macbook wont restart after Ubuntu installation"
date: 2015-05-27
forum: Apple Hardware Users
---

### Post by tim118 on 2015-05-27
Hi

I just installed the latest Ubuntu version on a Macbook late 2009. I had some problems at first (i8042 no controller found-problem) but I was able to handle them. 

So I installed Ubuntu on a extra 50 GB SSD partition (empty, I tried different formations) and it looked like it installed well. But when it asks me to restart and I  agree, I get to a black screen saying:

wait-for-state stop/waiting
 * stopping rsync daemon rsync            [ OK ]
 * speech-dispatcher disabled; edit /etc/default/speech/speech-dispatcher      
 * asking all remaining processes to terminate...            [ OK ]

More in the middle of the screen appear 2 small red dots with grey boxes around - they come up after each other. Then its stucked 

I have to restart by pressing the start button 10 seconds or something and after this I get to black screen. Only when I start with pressed alt button, I can choose where where I want to start, but Linux (except the boot-stick) isnt a choice. 

I also tried to turn on WIFI for auto-updates, added nobootwait before  installation etc - basicely I tried every solution you can find on the  web.

Any ideas?

 :guitar:):P      :guitar:

---

### Post by este.el.paz on 2015-06-02
tim:

Does OSX work on this computer?  Did you use rEFInd?  Did you install GRUB?  What version of Ubuntu are you using?  These kind of questions?

e..

---

### Post by Karl_Hungus on 2015-06-08
What is your GFX card... and EXACT model of your macbook?

did you try installing using a DVD-ROM (forces legacy/BIOS) mode also you should use proprietary drivers.

-mes

---

