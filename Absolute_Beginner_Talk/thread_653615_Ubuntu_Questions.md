---
title: "Ubuntu Questions"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by thecrimsonalchemist42 on 2007-12-30
I am sort of new to Ubuntu, so I have a couple of questions about Ubuntu I would like answered. 

1. I have Fiesty Fawn right now and I completed all my updates, it suggests I update to Gutsy Gibbon. Should I and does it do a direct download from there or do I need to put it on a CD? 
2. How do I install ATI drivers for my Radeon X1300?
3. How do I install Compiz Fusion?
4. How do I install mp3 decoder support for K3b?
and
5. Does Ubuntu come built in with a firewall? And if not, how can I get one?

Thank you very much.

---

### Post by Martje_001 on 2007-12-30
1) No, it will download everything it needs from the internet (can take a long time!)
2) With the restricted driver manager (first upgrade to Gutsy)
3) If you upgrade, it is installed by default.
4) Install with synaptic 'ubuntu-restricted-extras'
5) Yes. If you want a front-end (make it graphical) install 'firestarter'.

---

### Post by b0rka7a on 2007-12-30
Hello,
1) Yes, you can upgrade to Gutsy. It will upgrade from the net.
2) Go to "System > Preferences > Restricted Drivers Manager" and install them from there.
3) Compiz-Fusion should be installed after you upgrade to Gutsy and it will work after you install the drivers of you graphics card.
4) Search for "codec" in "Applications > Add/Remove..." and install them from there.
Happy New Year! ;)

---

### Post by thecrimsonalchemist42 on 2007-12-30
Thanks a lot you guys :) Happy New Year!

---

### Post by crjackson on 2007-12-30
> **thecrimsonalchemist42 said:**
> I am sort of new to Ubuntu, so I have a couple of questions about Ubuntu I would like answered. 

1. I have Fiesty Fawn right now and I completed all my updates, it suggests I update to Gutsy Gibbon. Should I and does it do a direct download from there or do I need to put it on a CD? 
2. How do I install ATI drivers for my Radeon X1300?
3. How do I install Compiz Fusion?
4. How do I install mp3 decoder support for K3b?
and
5. Does Ubuntu come built in with a firewall? And if not, how can I get one?

Thank you very much.

1. You can give it a try it's hit/miss.  If you want Gutsy, a clean install is best.
2. Easiest way is the restricted driver manager.  This version is a few versions older, but more stable IMHO.
3. Compiz-Fusion is installed by default in Gutsy. For Feisty, I suggest you search/read the forums.  Compiz-Fusion is hard to get working with your ATI card. Read, Read, Read.
4. Search synaptic for k3b and add the mp3 support. Restricted extras isn't in the Feisty repositories and it doesn't included the k3b specific support you are looking for
5. Yes. It's called IP Tables.  You do have to configure it to make it active.  I use Firestarter.  It can be found in synaptic.

---

