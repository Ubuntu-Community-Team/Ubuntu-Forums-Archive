---
title: "Beryl - Where to start?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by superbungalow on 2007-08-02
I would very much like to install beryl on my new ubuntu system, but i don't want to install it without knowing exactly what I'm doing, and I'm not that computer smart, so where do you think I should start?

---

### Post by loserboy on 2007-08-02
[www.ubuntuguide.org](www.ubuntuguide.org)  should have some well made howtos for it, there will be one for Ati users and one for nvidia users I think

---

### Post by Rocket2DMn on 2007-08-02
Beryl has merged with Compiz to become Compiz Fusion.  There won't be any further development for Beryl, but Compiz Fusion will be getting updated, so I suggest that.

---

### Post by mpospisil on 2007-08-02
Yeah I just updated from Beryl to Compiz Fusion last night.  This site does a great job on telling you exactly what you need to do.

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by superbungalow on 2007-08-02
Hey, thanks for the advice, I started installing compiz-fusion from: 

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

But I rebooted after the envy thing, and now my audio wont play. It's happened to me before:

[http://ubuntuforums.org/showthread.php?t=515578](http://ubuntuforums.org/showthread.php?t=515578)

But I was wondering what to do know, I could try repeating the fix, but I don't want to change anything!!! WIll it be safe?

---

### Post by cwmoser on 2007-08-02
Two things I remember when I installed Beryl:

1-) that it allowed for me to manually start Beryl, and still does -- i.e. Applications -> System Tools -> Beryl Manager

2) when I installed the nVidia video drivers, it goofed up my GUI.  I had to Ctrl + Alt + F2 to go to command prompt, log in to console.  Then vi /etc/X11/xorg.conf file to revert the video back to the way it was.  HINT:  Preserve a copy of xorg.conf before you attempt this.  When done editing xorg.conf, go back to the GUI via Ctrl + Alt + F7.

Give it a go -- Beryl is one of the best enhancements to Ubuntu.

Carl

---

