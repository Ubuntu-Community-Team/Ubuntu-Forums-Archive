---
title: "installing things"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by time_shift on 2006-02-03
i dont want to come off as a total noob but that is what i am, luckily that will change... eventualy.
first i don't know how to install things that i download off the net such as firefox 1.5.0.1 or scummvm.
secound synaptic package manager seems to not be able to find lib files for the things that i would like to get. ive already put security updates and updates on in the software sources and i got the updates.
third i was wondering about security issues and ad-ware and spyware. i know in windows you have to have anti-virus and anti-spyware and such, is it the same in ubuntu.
forth im trying to install a wireless network card it says its a BCM4306 802.11b/g wireless adapter made by linksys. i looked for a driver but all i found was information.
ps is there a keyboard command to get from workplace to workplace

---

### Post by aysiu on 2006-02-03
[QUOTE=time_shift]i dont want to come off as a total noob but that is what i am, luckily that will change... eventualy.
first i don't know how to install things that i download off the net such as firefox 1.5.0.1[/quote] [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) > or scummvm. You can download this through Synaptic--just enable the Universe repositories.

> secound synaptic package manager seems to not be able to find lib files for the things that i would like to get. ive already put security updates and updates on in the software sources and i got the updates. See the first link of my signature (this will help you with scummvm, too).

> 
third i was wondering about security issues and ad-ware and spyware. i know in windows you have to have anti-virus and anti-spyware and such, is it the same in ubuntu. No. Some people do it just to be safe or to make sure they're not spreading viruses on to their Windows-using friends and relatives accidentally.

> ps is there a keyboard command to get from workplace to workplace Go to System > Preferences > Keyboard Shortcuts. You can define your own command.

---

### Post by byen on 2006-02-03
Hey there.. Welcome to Ubuntu! I cant answer all your questions but let me try...
Q: i was wondering about security issues and ad-ware and spyware
A: Adware and spyware dont work in linux. You do not need an antivirus either (unless you want to scan incoming mail for viruses and save your friends from hassle when you forward them)

Q: i know in windows you have to have anti-virus and anti-spyware and such, is it the same in ubuntu.
A: I think the previous question answers this. But if you do want an antivirus to scan your windows drive..there are a few. ClamAV and [F-Prot]("http://ubuntuforums.org/showthread.php?t=88357") to name two (there are many how-tos for this)

Q: im trying to install a wireless network card it says its a BCM4306 802.11b/g wireless adapter made by linksys. i looked for a driver but all i found was information.
A:I have one too. And [this thread]("http://ubuntuforums.org/showthread.php?t=25683") helped me. It is a how-to for Hoary but it works for Breezy too!

Q:Is there a keyboard command to get from workplace to workplace 
A:I dont know if there is a command but you can configure shortcuts by using >System>Preferences>Keyboard shortcuts

Q:first i don't know how to install things that i download off the net
A:Look for packages with the extention ".deb" for download and to install them just go to the location in the terminal and do "sudo dpkg -i package_name" (you can also download .tar.gz etc files but .deb is the best for Ubuntu) But before doing that I strongly suggest doing: System>administration>synaptic package manager >search> program (or sudo apt-get install program_name) to see if it is in the repositories (they usually are). Please search if someone else tried installing the packages you  want to install... I got firefox using [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") and some did using various how-tos in this forum so...EDIT:well aysiu has the answers for the rest... I guess thats about it...
hope it helps. Goodluck!

EDIT:
AYSIU: WHoa.... you are fast ! ;-)  Seems like Im the slowest when it comes to typing in this forum.

---

### Post by tim15856 on 2006-02-03
First thing you might want to do is install Automatix. It will properly install a lot of software you may want. It can also install Firefox 1.5. It may also install some lib files you'll need. [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563) Synaptic should have most everything else you might need. It should know what dependencies needs to be installed. For installing other software:

From source:
[https://wiki.ubuntu.com/CompilingSoftware?highlight=%28compile%29](https://wiki.ubuntu.com/CompilingSoftware?highlight=%28compile%29)

Everything else:
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

---

### Post by mustang on 2006-02-03
[QUOTE=time_shift]i dont want to come off as a total noob but that is what i am, luckily that will change... eventualy.
first i don't know how to install things that i download off the net such as firefox 1.5.0.1 or scummvm.
[/QUOTE]

In most cases with tar.gz's, it's a matter of extracting and compiling (if necessary). With firefox, you just click on the firefox executable. However, here is a more comprehensive guide to install firefox:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

Don't download the firefox from the link given in that guide though since it's 1.5. Go to [http://www.mozilla.com/](http://www.mozilla.com/) and get the new one. All the other directions still apply.

> secound synaptic package manager seems to not be able to find lib files for the things that i would like to get. ive already put security updates and updates on in the software sources and i got the updates.

Hmm could you clarify this problem? That's good that you installed the security updates and everything but how is that related to snynaptic not finding lib files?

> 
ps is there a keyboard command to get from workplace to workplace

Crtl + Alt + Arrowkey

More in System->Preferences->Keyboard Shortcuts

Sorry I couldn't answer the rest of your questions. Good luck getting everything working and keep the questions coming!

Edit: **wow** I am slow. Three replies before me already

---

