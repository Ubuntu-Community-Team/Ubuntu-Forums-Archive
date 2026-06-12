---
title: "[SOLVED] I can't install any program on the program list!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by skibblesx on 2008-02-28
I go to the add/remove programs area but EVERY single program on there it says that the program is not avalable. Help please.

---

### Post by Joeb454 on 2008-02-28
What errors do you get specifically?

Also try running the following from a terminal (get to it from Applications>Accessories>Terminal)

```
sudo apt-get update
```
You will be asked for your user password. Though it won't show anything when you're typing :)

---

### Post by jan quark on 2008-02-28
also make sure your sources are enabled

go to

system > administration > software sources and enable everything except source and cd

and then reload and try to install one more time

---

### Post by FuturePilot on 2008-02-28
You may need to enable all of the repos. System&#8594;Administration&#8594;Software Sources.
Check all of the boxes in the first tab and uncheck the CD-ROM if it happens to be checked. Go to the Updates tab and check the first two boxes and optionally the fourth to enable the backports. Click Close then Reload when prompted.

---

### Post by skibblesx on 2008-02-28
I just did the terminal thing. Then I went to programs and it says (When I try to install some thing) "The list of applications is not avalable."

---

### Post by skibblesx on 2008-02-28
Thanks guys. I got it to work now. It just needed some kind of update. But I went into the software place now it is working.

---

### Post by Chappy7777 on 2008-02-28
Did you try looking for the program you want in Synaptic? What are you looking for?

Likely you know this, but then maybe not: Go to System/Administration/Synaptic Package Manager, and click on Synaptic. Do a search for the program you want. If it's there, click on it, and then click on the same program on the right side. Click "Mark for Installation". A list will come up of the files you'll be downloading to get the program.  Click apply and let it do it's thing.
 
Synaptic will download and install all the files. You'll know when it's done. The close Synaptic and look under Applications. For example, if you downloaded "Super Tux", look under Games.

I hope this helps. Synaptic works similar to Add/Remove, but I find it is more intuitive.

---

### Post by Joeb454 on 2008-02-28
Great! Please mark your thread as solved :) It's at the top right of this page.

Also I'm guessing you had to go to System>Administration>Software Sources to fix the problem?

---

