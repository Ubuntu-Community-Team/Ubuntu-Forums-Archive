---
title: "Realplayer 64 bit controls"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2008-02-03
I can't get my realplayer controls to work in firefox, to see an example of the controls i'm talking about go to [http://www.bbc.co.uk/radio4/comedy/](http://www.bbc.co.uk/radio4/comedy/) and click on one of the 'listen' buttons.

I have nspluginwrapper on my system (from flashplayer-nonfree), installed RealPlayer.bin from the real site, and then ran 

nspluginwrapper -i /opt/RealPlay/mozilla/nphelix.so

and then I could use Realplayer in my browser, however where there are controls for the realplayer stream (for example at BBC Radio) the controls do nothing, whereas in 32 bit ubuntu they work fine with realplay.

I believe that its something to do with the nphelix.xpt file that comes with realplay, but i tried copying that to the same directory as nspluginwrapper installed to to no avail (even tried naming it nspluginwrapper.nphelix.xpt to match the .so file).

Does anyone know of a solution to this?

Thanks in advance

---

### Post by richardward101 on 2008-02-10
Anyone?
I realize I could probably get it working if I installed a 32 bit Firefox, but I'd rather stick to 64 bit if possible.

---

