---
title: "Lost cause?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by braindonor23 on 2007-11-11
Hi, I'm pretty much a total n00b to the linux community.  I have used windows and DOS for many years and consider myself an advanced user with those operating systems.  Recently I decided to switch to Linux becuase I wnated to use an OS that was a bit lighter, and also just to learn something new.  I played with a bunch of distros, and Ubuntu is the one I've settled on liking.  Unfortunately I am having the same problem with it as with the other distributions I've tried, and that is that every time I try and make any change, the computer fails to boot afterward.  this has applied to most every change of desktop settings I have made, but the main root of my problem is my desire to install the proper drivers for my network and graphics hardware, and since I've no idea how to restore, or to repair possible misconfigurations from the console, this has led to hours of sitting through the installation again so I can start from a clean slate.  I'm using (or at this point trying to use) ubuntu v7.04 (fiesty), and my desire is to at least configure my GeForce6100 to my liking, install more applications, and hopefully use my linksys wireless card (though I will say that ubuntu is the only one I've tried that can utilize my RTL8201 wired ethernet with full functionality). right now my efforts amount to the installs reporting success from within the shell, only for my box to greet me with a plethora of error messages on shutdown, and boot problems ranging from a mild invisible cursor in gnome to complete non-recognition of my boot filesystem.  if anyone can point me to a fast and dependable way to restore my ubuntu partition to it's previous glory, that would be the most help, as I'm tired of reinstalling.

---

### Post by stinger30au on 2007-11-11
might i suggest you try a copy of "Ubuntu Ultimate Edition" version 1.6

[http://forumubuntusoftware.info/index.php](http://forumubuntusoftware.info/index.php)

this version is based on 7.10 and goes everything except come with the kitchen sink

---

### Post by Malta paul on 2007-11-11
Hi, Linux is different to windows but great when you get the hang of it. As an old DOS user like myself you will soon learn the differences.
Here are some references that may help you:
 [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
Good luck :)

---

### Post by rorestuff on 2007-11-11
What are you using to edit the configuration files? A text editor? Or are you using the admin GUIs in GNOME?

---

### Post by braindonor23 on 2007-11-11
No, I've not been using a text editor to change the files manually.  I have been using the admin tools from the gnome desktop.  Today I started again, this time using gutsy instead.  same issue.  defualt configuration works, but if I so much as change my scren resolution, the computer crashes on the next bootup. so basically I can leave everything exactly as it is to start with, making it functional, but relatively useless, or I can try and change something, anything, and have an "operating" system that doesn't "operate".

*EDIT* ok, seems like my problem is solved.  Turns out my filesystem was marked as type vfat and formatted as ext2, though I have no idea how that happened.  I have reformatted the whole drive and reinstalled 7.10. Now my graphics accelleration and wireless card have configured automatically, and my settings from previous sessions come back with no issues.  I still get some network related errors on shutdown, but the networking still works fine every time I boot up, so I don't care.  Thanks also Malta paul for the links. lots of information to get me started.

---

