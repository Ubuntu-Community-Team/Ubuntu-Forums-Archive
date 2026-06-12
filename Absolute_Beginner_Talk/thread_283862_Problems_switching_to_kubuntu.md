---
title: "Problems switching to kubuntu"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-10-24
I added the kde desktop earlier today and decided I liked it so much I would switch to it permanently.  This has caused quite a few problems for me.  For some reason aptitude got rid of many of my programs and during the process of bringing them back firefox stopped working.  I posted about that here:[http://www.ubuntuforums.org/showthread.php?p=1658673#post1658673](http://www.ubuntuforums.org/showthread.php?p=1658673#post1658673)
I then tried rebooting and when it finally came back I was left with nothing but the command line, no desktop at all!  I had no idea what was going on so I luckily remembered the command I used to install kde earlier, sudo aptitude kubuntu-desktop, and figured it couldn't hurt so I ran it and got my kde back.  Now firefox still doesn't work and neither does adept that I've noticed.  
Evolution is a program I installed right when I installed firefox the first time because those were the two most noticeable problems, not sure if that helps but I figured the more information the better. 
Anyway I'm just wondering what might have gotten screwed up by all this and how I can bring my firefox back, I've already done sudo aptitude upgrade if that helps any.

Thanks,
Nolan

---

### Post by janbockaert on 2006-10-24
does gimp works? Looks like a gtk-problem. Maybe you should start firefox from a terminal, and post the output here?

---

### Post by Denn1s on 2006-10-24
if firefox and adept are not workin, maybe you have a problem with the internet? also, do you have a package named ubuntu-desktop installed? It alwais asks for uninstall in my box

---

### Post by madddonkey255 on 2006-10-24
Internet works because I'm using Konqueror to write this, also gaim works fine.  When I try to open firefox in the terminal I get this message> X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Which actually is new because before I tried and absolutely nothing came up, so maybe I made some progress somehow?

Gimp opens and also opens pictures, although I also get the same error code as above when it's opened in the terminal.  Also the Konsole has a black background with white font, not sure if this is unusual but I remember it's been both that and white background with black font today if that helps at all.

Thanks a ton you're really saving me.
Nolan

---

### Post by seijuro on 2006-10-25
Just an opinion but if it was me I would backup my data and install fresh from the Kubuntu cd/dvd instead of installing kubuntu-desktop from ubuntu the advantage to doing this is you will end up with fewer updates needed and unwanted packages that you have to remove or leave and waste space. when you install something that needs gnome or gtk apt-get will just download the required libraries to run the apps you want rather than installing everything.

---

### Post by madddonkey255 on 2006-10-25
Yeah I thought about that but I've got nowhere to back it up on.  It would take too many cd's.  
Thanks,
Nolan

---

