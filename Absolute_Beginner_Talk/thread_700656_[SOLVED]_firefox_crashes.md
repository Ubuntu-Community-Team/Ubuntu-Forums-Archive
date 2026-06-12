---
title: "[SOLVED] firefox crashes"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by DarinB on 2008-02-18
firefox crashes i get the screen that reads close firefox or restart
when i click the icon all i get is the error message...in win i hit task manager and can kill it there
how do i do this in feisty???????????????
i tried alt f2 but i don't have firefox opened to xkill it.
help???????
AND WHY DOES IT CRASH IN THE FIRST PLACE 
USUALLY IT IS WHEN I HAVE MULTIPLE FIREFOX TABS OPEN.
OR CLICK A SHOW LIKE DAILY SHOW SEGMENTS.

---

### Post by TeoBigusGeekus on 2008-02-18
Go to System->Administration->System Monitor
Tab Processes and right click firefox-bin.
Try to end it or kill it. Hope that helps!

---

### Post by sports fan Matt on 2008-02-18
1st off daily show is a great show btw:)  

2nd off, i too have a similar issue with Firefox, I think in my case I corrupted the firefox profile folder cause i couldnt initilize the browser's security component, son I took a drastic step and deleted that folder but I backed up the folder first.  

Not exactly sure if its the same, but I use swiftweasel and it works well..

---

### Post by DarinB on 2008-02-18
thanks next time i will use system monitor process then try to kill it there
what is swiftweasel???????

---

### Post by y-lee on 2008-02-18
[http://swiftweasel.tuxfamily.org/]("http://swiftweasel.tuxfamily.org/") is an optimized for speed version of firefox.  I use it and it is faster and easy to install. They also added a [repo]("http://swiftweasel.tuxfamily.org/wiki/index.php5?title=Apt") :)


**EDIT:** Also of interest is [ pkill an easier linux kill command ]("http://www.terminally-incoherent.com/blog/2007/08/01/pkill-an-easier-linux-kill-command/")and [How To Kill Stuff On Linux]("http://www.terminally-incoherent.com/blog/2007/10/05/how-to-kill-stuff-on-linux/") for command line tools to kill stuff.

---

### Post by billgoldberg on 2008-02-18
in a terminal:

pkill firefox

Firefox crashes because of the flash player.

Opera doesn't have this but flash player is harder to install.

---

### Post by DarinB on 2008-02-18
i just installed swift weasel will that help the flash problem?????

---

### Post by billgoldberg on 2008-02-18
I don't think so. Other firefox based OS like netscape 9, flock, ... also crash. As does epiphany.

Try opera, but installing flash won't be that easy as it was for firefox.

Firefox 3 beta 3 also still crashes with flash (not all the time offcourse, about twice a week).

---

### Post by y-lee on 2008-02-18
Firefox can crash for alot reasons including flash, add ons are also another reason, another is it has a memory leak that is supposedly mostly fixed in version 3 coming out.

Swiftweasel is basically firefox so it probably will not help with crashing. If it or firefox crashes alot let us know here because that is not typical...something is up :(

---

### Post by DarinB on 2008-02-18
i am trying swiftweasel i will get back if it crashes i did install swiftdove and my system crashed about four times i just remove swift dove and i am fine again.

---

### Post by DarinB on 2008-02-19
FYI
my system works much better with swiftweasel.
it is much faster and more stable with flash.
i did install the one for my Pentium 4 and it races along visibly faster that firefox or is it smolderingfox or dyingfox.
thanks folks i will keep all posted.

---

### Post by TeoBigusGeekus on 2008-02-19
The latest Flash Player is not compatible with the latest Opera for Linux (9.2something).
In order to be able to install flash in Opera you're gonna have to use Opera 9.5(beta) but then 
the crushes are bound to be more often than in Firefox (ask me!!!).
In general, however, Opera is much more stable and less resource hungry than Firefox.

---

### Post by DarinB on 2008-02-19
i am just not into more headaches i want my life simple. so i will pass on opera.
that's what ubuntu is supposed to be about simple
so far i have really tasked swiftweasel and no crashes a few restart old session or start new one.
not a big deal the annoying ones are the "you need to restart" or i am using the system monitor to kill the bin file and start again. but that has only happened when i installed swiftdove i took it out and am still doing great no crashes.
BTW i have quite a few ad ons

---

