---
title: "Intel GMA 915 with beryl?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-05
Does my Intel GMA 915 support beryl?

---

### Post by kosmic on 2007-07-05
Yes Intel graphics works well with beryl.

But you should try compiz fusion, because beryl is merging with compiz

---

### Post by czepluch on 2007-07-05
> **kosmic said:**
> Yes Intel graphics works well with beryl.

But you should try compiz fusion, because beryl is merging with compiz

Okay, but i'm all new to ubuntu, so i'm having a bit trouble installing it, i think. Can you help me ?

---

### Post by kosmic on 2007-07-05
No problem ;)

You can read Vorian post about installing compiz fusion - [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by czepluch on 2007-07-05
> **kosmic said:**
> No problem ;)

You can read Vorian post about installing compiz fusion - [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

I don't really understand everything in the guide .

---

### Post by reacocard on 2007-07-05
> **czepluch said:**
> Okay, but i'm all new to ubuntu, so i'm having a bit trouble installing it, i think. Can you help me ?

If you're new, don't do compiz fusion, it'll only cause you trouble at this point.

For beryl, open a terminal and do
```
sudo apt-get install beryl-ubuntu beryl-manager
```

That'll get everything you need. Now you can run beryl to test it from Applications -> System Tools -> Beryl Manager. If it works well, you can add beryl-manager to your startup programs in System -> Preferences -> Sessions, so that Beryl will start automatically whenever you log in.

I also have intel 915 graphics, beryl works very well (as long as you leave blur disabled), and compiz fusion is even smoother, but CF tends to crash a lot more, so I recommend beryl for now.

---

### Post by kosmic on 2007-07-05
ok you can do what reacocard  says it is a lot more simple ;)

---

### Post by eentonig on 2007-07-05
I have to agree with reacord.

Beryl install is easier and can be done via the repo's. And it runs 'acceptable' in the mentioned GPU.

Compiz Fusion is harder to install and less stable. But it is a whole lot smoother on the GPU.

---

### Post by reacocard on 2007-07-05
Update, I just posted an easier HOWTO for compiz fusion: [http://ubuntuforums.org/showthread.php?t=493074](http://ubuntuforums.org/showthread.php?t=493074)

You can try that if you really want to, but I still recommend beryl at the moment.

---

### Post by Ripfox on 2007-07-11
I have the same graphics, and I have always found, even in Gutsy, that removing all compiz packages and then using APTITUDE (sudo aptitude install beryl) works best of all.

Cheers

---

### Post by hutas on 2008-01-23
> **reacocard said:**
> If you're new, don't do compiz fusion, it'll only cause you trouble at this point.

For beryl, open a terminal and do
```
sudo apt-get install beryl-ubuntu beryl-manager
```

That'll get everything you need. Now you can run beryl to test it from Applications -> System Tools -> Beryl Manager. If it works well, you can add beryl-manager to your startup programs in System -> Preferences -> Sessions, so that Beryl will start automatically whenever you log in.

I also have intel 915 graphics, beryl works very well (as long as you leave blur disabled), and compiz fusion is even smoother, but CF tends to crash a lot more, so I recommend beryl for now.

hi i tried that code and then it gave me this 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  beryl-ubuntu: Depends: heliodor but it is not going to be installed
                Depends: libberylsettings0-gconf but it is not going to be installed
                Depends: beryl but it is not going to be installed
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

what should i do?? 

thanks

---

### Post by reacocard on 2008-01-23
> **hutas said:**
> hi i tried that code and then it gave me this 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  beryl-ubuntu: Depends: heliodor but it is not going to be installed
                Depends: libberylsettings0-gconf but it is not going to be installed
                Depends: beryl but it is not going to be installed
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

what should i do?? 

thanks

Um, beryl is vastly out-of-date now, compiz-fusion should be used instead.  It is installed by default in Gutsy, though you will need to install compizconfig-settings-manager to configure all aspects of it.  compiz-fusion can be enabled on gutsy under System->Preferences->Appearance->Visual Effects. note that you may have to install the correct drivers for your graphics card before you will be allowed to enable compiz-fusion.

---

