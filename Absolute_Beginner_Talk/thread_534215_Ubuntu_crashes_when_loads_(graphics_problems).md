---
title: "Ubuntu crashes when loads (graphics problems)"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Canadaboy on 2007-08-24
just say Ubuntu crash when trying to load (because of some x graphics error)

say that you were trying to fix ur graphics card driver so u can have effects (Beryl)

and u looked on a forums

and u did what the guy said
[http://ubuntuforums.org/showthread.php?t=457640](http://ubuntuforums.org/showthread.php?t=457640) (espreon)

(I listened to my friend and restarted instead of logging in and out. Is there a difference?)

and now when I wanna load it it says graphical error

and it loads (commandprompt? terminal? some black safemoe thingy?)

---

### Post by SpiritIsReality on 2007-08-25
howdy
at the command prompt, type
sudo dpkg-reconfigure xserver-xorg
and then press the enter key
when it gives a choice of advanced medium simple, don't pick advanced unless
you can find your monitor's refresh rates before hand.
it's a real good learning experience and should get you back to gui desktop.
the default settings are usually right, can get back to a desktop by pressing enter
at each question.
after it's done, type
sudo shutdown -r now
and press enter, to restart the computer
sudo shutdown -h now
will shutdown halt, and usually power it off.

good cli page here
[http://linuxcommand.org/](http://linuxcommand.org/)
and here
[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)

more good sites(you've probably checked some already but..)
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+dpkg-reconfigure+xserver-xorg+feisty&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com%2Fcommunity+dpkg-reconfigure+xserver-xorg+feisty&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg-reconfigure+xserver+xorg%22+feisty+ati&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22dpkg-reconfigure+xserver+xorg%22+feisty+ati&btnG=Search&meta=)
[http://www.ubuntu.com/support](http://www.ubuntu.com/support)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://www.ubuntu.com/community](http://www.ubuntu.com/community)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

good search pages
[http://www.google.ca/advanced_search?hl=en&output=linux&restrict=linux](http://www.google.ca/advanced_search?hl=en&output=linux&restrict=linux)
[http://www.cyberciti.biz/tips/introducing-linux-custom-search-engine-using-google.html](http://www.cyberciti.biz/tips/introducing-linux-custom-search-engine-using-google.html)
[http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o)
at google.ca, try typing in the box
site:ubuntuforums.org feisty 
and then your search terms, e.g. resolution

and tips on how to run google 
[http://www.googleguide.com/](http://www.googleguide.com/)

free linux books online
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)

trails

---

