---
title: "Problems w/ Connection Manager."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-02-20
i am using the app that is listed here. [link]("http://www.ubuntuforums.org/showthread.php?t=299462&highlight=connection+manager")

previously it worked no problem, but now i am unable to click on setup network or connect. the screen comes up but nothing happens when i click it. i used this to enter a previous networks info, and i selected preferred network thinking that it would auto connect the next time that i was in range and it does. But i am unable to connect to any other network now. 

i am curious if i can reinstall it but i downloaded the .deb package and did not use apt-get. how can i uninstall it?

I like the graphical ability to configure my wireless settings so i loved this app.  is there any other apps out there w/ the same functionality?

thanks in advance. :)

---

### Post by tgalati4 on 2007-02-22
In a console, what does ifconfig and iwconfig reveal.  If you are not connected then those two commands will give that status.  If the graphical window stopped working but the network connection is still good, then I would assume that a system update screwed up the windowmanager that is running your network chooser.

There is gnome wifi-radar.  It's a simple app, but it works for selecting different wireless networks.  Not as cool as Edgy's connection manager, but it seems to work.
Did you try:
sudo apt-get remove crappypackagethatisgivingmeaheadache.deb
Perform an update, make sure you have the latest and greatest.  Then reinstall the package.  Of course it may still be broken, search the bug reports to see if others are having problems.  If not, then perhaps it is a new bug that needs filing.

---

