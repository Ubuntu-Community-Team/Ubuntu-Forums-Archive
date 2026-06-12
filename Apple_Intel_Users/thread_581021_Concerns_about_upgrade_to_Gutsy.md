---
title: "Concerns about upgrade to Gutsy?"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-19
Currently running Feisty on a MacBook (C2D, 2.16 GHz) and everything runs perfectly.
Now I want to upgrade to Gutsy (network upgrade).
Anything I should be worried about?
I'm particularly concerned about my wifi connection as getting wifi set up in Feisty was a bit of a struggle on this machine and where I am right now, I only have limited access to a wired connection.
Thanks for any help
Paul

---

### Post by Hatfield on 2007-10-19
I have the exact same MacBook and I upgraded to Gutsy yesterday.  I lost my MadWifi.  Used make clean(edited; see below) and reinstalled the current madwifi(ng) and everything was fine again.  Took 20 minutes.

---

### Post by PaulFXH on 2007-10-19
Thanks but what does "cleaned" mean?
Reformatted the drive?

---

### Post by Hatfield on 2007-10-19
No no no.  Make clean.:lolflag:

---

### Post by PaulFXH on 2007-10-19
Hmmm, you've lost me.
```
make clean
```
is a command used in compiling from source but for this upgrade, no compilation is involved.

---

### Post by Hatfield on 2007-10-19
I'm a newb.  You most likely know more than I do concerning Ubuntu.  I took the advice of a buddy yesterday and followed his direction.  I went into my old MadWifi directory used make clean and then reinstalled and my wifi worked again.

In hindsight, I shouldn't have replied.  I'm sure you'd get a better answer from someone more experienced.  I'm still learning, but I just wanted to pass along how I got mine to work again.

---

### Post by PaulFXH on 2007-10-19
> I'm still learning
Me too, and I really don't want to stop learning.
From what you say, you actually did compile the madwifi driver. I assume you must have afterwards typed
```
make install
```
to install your newly compiled driver.
Actually, I had a problem in Feisty in that the newer madwifi just didn't work for me and I had to use a legacy madwifi driver. As you have the exact same machine as me, I would be interested to know exactly what driver you used (maybe you can supply a link)
Thanks a lot

---

### Post by Hatfield on 2007-10-19
Followed [https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

sudo aptitude install build-essential
wget [http://snapshots.madwifi.org/madwifi-ng-current.tar.gz](http://snapshots.madwifi.org/madwifi-ng-current.tar.gz) (I found it [here](http://snapshots.madwifi.org/))
tar -zxvf madwifi<tab>
cd madwifi<tab>
make
sudo make install
sudo modprobe ath_pci

---

### Post by PaulFXH on 2007-10-19
OK, thanks for that.
Interestingly, the Feisty part in the link you gave just ddn't work for me. But, if the Gutsy bit worked on your machine, then its gotta work on mine, right?
Anyway, I'm gonna try it now.
Thanks for your input

---

### Post by Hatfield on 2007-10-19
Crap.  You jinxed me.  I just hopped on my MacBook(been typing on the PC all morning) and my wifi is NOT working.:(  It *was* working all day yesterday after the Gutsy upgrade but now it's not.  So forget most of what I said.  I'm now in the same boat as you.  I'm gonna remove the old MadWifi modules and follow the Gutsy directions from the above wiki I posted earlier.

---

### Post by cyberdork33 on 2007-10-19
there is a bug in madwifi that will cause things to fail every once in awhile. you should be able to reboot and wifi will work again.

---

