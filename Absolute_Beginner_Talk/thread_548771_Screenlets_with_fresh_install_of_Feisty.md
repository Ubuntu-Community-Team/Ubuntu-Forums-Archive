---
title: "Screenlets with fresh install of Feisty?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-11
Can I use screenlets with a fresh install of Feisty?  The way I understand, Feisty has compiz built in, but the screenlets use Beryl.  

is this true?

I'm not a Macbook, if that matters at all.

---

### Post by DarwinsTheory on 2007-09-11
Works fine with Compiz-Fusion..

Not sure about the native Compiz  in Feisty....

But it wouldn't take much effort for you to test   :-)

Matt

---

### Post by dmber on 2007-09-11
cool, i'm very new to Linux, just discovered Screenlets on gnome-look.org last night.  do you know of a good step-by-step off the top of your head i can follow?

thanks.

---

### Post by slughappy1 on 2007-09-11
I followed the instructions form [http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/](http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/) they work perfectly.

For Ununtu7.04 I did the following: from the link above
1) type in to the terminal: sudo gedit /etc/apt/sources.list 
2) add this line to the file: deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets  
2) type in to the terminal: wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - 
3) type in to the terminal: sudo apt-get update
4) type in to the terminal: sudo apt-get install screenlets
5) and then I rebooted

---

### Post by dmber on 2007-09-11
awesome, thanks!

---

### Post by slughappy1 on 2007-09-11
No problem. I might want to mention that I followed the instructions from [http://ubuntuforums.org/showthread.php?p=3255930#post3255930](http://ubuntuforums.org/showthread.php?p=3255930#post3255930) to install the latest version of compiz fusion. Although in step 3 of the compiz part you should type in sudo apt-get update before sudo apt-get upgrade

---

