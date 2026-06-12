---
title: "Ubuntu turned in to Kubuntu???"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-04-22
Hey there :) 

 I installed KDE via Terminal using the following command  sudo aptitude install kubuntu-desktop  and everything went fine except for one thing. Now my Ubuntu has become Kubuntu even after logging out and changed the session to Gnome. I am confused and to be honest a little frustrated lol. Does that normally happen ? Is this normal ? please help. 

Thanks

---

### Post by mabelrxu on 2007-04-22
wait ... you typed xubuntu-desktop and got kubuntu? that's definitely odd ... if you typed xubuntu-desktop, you should get xubuntu, and kubuntu-desktop should give you kubuntu ... and can you describe how your "Ubuntu has become Kubuntu"? ubuntu and kubuntu are basically the same thing underneath, it's like the same person wearing different clothes ...

---

### Post by nick24 on 2007-04-22
It "turned" in to kubuntu after I install  KDE on it. Its funny because I have a Gnome desktop with all the KDE apps , they all start with K ........hhmm I guess its a bug or something .

---

### Post by nick24 on 2007-04-22
> **mabelrxu said:**
> wait ... you typed xubuntu-desktop and got kubuntu? that's definitely odd ... if you typed xubuntu-desktop, you should get xubuntu, and kubuntu-desktop should give you kubuntu ... and can you describe how your "Ubuntu has become Kubuntu"? ubuntu and kubuntu are basically the same thing underneath, it's like the same person wearing different clothes ...

Sorry I typed  sudo aptitude install kubuntu-desktop. Sorry for the typo again.

---

### Post by Xarok on 2007-04-22
Can you post a screen-shot of what you're talking about?

Of course if you install KDE you will also get all the KDE apps, and you can use those within gnome (I think).

---

### Post by ofek on 2007-04-22
This is no bug, it just changed the gdm theme which could be easly changed back from the main menu, start System->Administration->Login Screen Setup.
You can download new ones from [http://www.gnome-look.org](http://www.gnome-look.org) as well...

---

### Post by nick24 on 2007-04-22
Thanks for the help guys .....as always............I guess its normal ........I googled and came up with some solution.  [http://linuxfud.wordpress.com/2006/08/13/changing-from-ubuntu-to-kubuntu/](http://linuxfud.wordpress.com/2006/08/13/changing-from-ubuntu-to-kubuntu/)

---

### Post by mabelrxu on 2007-04-22
like i said,  ubuntu and kubuntu are basically the same thing, and those two flavors are especially interchangable (as opposed to ... say, xubuntu and kubuntu), so you should unconciously be running both kde and gnome apps in both environments anyways ... it's no biggie ... i just didn't like the blue colors kde apps brought into my pretty brown gnome back when i was running ubuntu edgy :)

---

### Post by rocknrolf77 on 2007-04-22
Just do a ```
sudo aptitude remove kubuntu-desktop
``` If you just want kde you can do a ```
sudo aptitude install kde-core
``` Then just add the stuff you want :)

---

### Post by mabelrxu on 2007-04-22
ooo ... good idea ... i think i'll do that too, to try out kubuntu without gobbling up too much hd space

---

