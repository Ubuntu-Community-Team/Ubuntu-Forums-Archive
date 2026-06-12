---
title: "swift fox problems"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-17
I  installed swiftfox from [www.getswiftfox.com](www.getswiftfox.com), Swiftfox 1.5.0.3 as I run a P4.  So I get the "swiftfox-1.5.0.3-pentium4.tar.bz2" on my desktop and I read the instructions on installation.  I extract all the files into my home folder.  So now I have a Swiftfox folder in my home folder.  I double click on it then find the installation file "swiftfox" and run it it tells me to close any firefox browsers so i do then it brings me up into swiftfox.  This is where i get lost because it seems as if I am running the program and it is all working.  But whenever I try opening a document or running firefox it always uses my old version, the one that came with ubuntu.  How do I get it to run my new version, the swiftfox version.  I tried playing with the comman line in properties but it just says that the file path does not exist.  Everyone else seems to have had an easy installation and I don't understand why mine will not work the way I want it to.  Any suggestions?  Thanks.

---

### Post by _simon_ on 2006-05-17
ok.. firstly if you have a firefox icon on the desktop or in a panel you need to right click and select properties. In command you need to put the path for swiftfox. For example I put in: ```
/home/simon/swiftfox/firefox
``` so when I click the icon it runs swiftfox, not firefox.

secondly... go to System -> Preferences -> Preferred Aplications

Where it says Web Browser, choose custom and in the command bit add the path again followed by %s e.g. ```
/home/simon/swiftfox/firefox %s
```

That should be it then mate.

---

### Post by aysiu on 2006-05-17
Follow this tutorial, but adjust it so that it unzips and moves the Swiftfox .tar.gz instead of the Firefox one: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by pgmario on 2006-05-18
Did you follow the instructions in my [how-to]("http://ubuntuforums.org/showthread.php?t=142798&highlight=firefox")?

---

