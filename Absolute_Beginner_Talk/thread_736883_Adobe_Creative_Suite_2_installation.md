---
title: "Adobe Creative Suite 2 installation"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Gwynn on 2008-03-27
Hi all. I love this forum, I asked a question on 26 March and received three answers within an hour. Fantatic!

I'm attempting to install Adobe Creative Suite 2. It is a seven CD (or maybe DVD) installation. I'm using Wine for the install.

CD1 goes through without a problem, however when CS2 asks for CD2 to continue the installation it keeps rejecting it. What am I doing wrong?

With gratitude for and advice or suggestions.

Gwynn.

---

### Post by intel on 2008-03-27
which version of wine are you using ?

CS2 should be supported, have you tried the latest Wine version ?

---

### Post by Gwynn on 2008-03-27
Hi Intel,
Thanks for responding. The Wine version is 0.9.46

It's installed Photoshop (which is on CD1).  The installer then asks that CD 2 be put in the CD tray. I do this and click on OK but it just spits it back out.

Do I need to mount all seven CDs before I start the install procedure?

Gwynn

---

### Post by Ralphie on 2008-03-28
If this is a legal version, you should only need that first CD. 
When installing, make sure that you unmark all of the other things for installation. Make sure Photoshop is the only thing being installed. I think by default it installs Adobe Bridge, as well.

Nothing but photoshop will work on the current version of wine. 

Also you should update your wine version, because it wasn't until version 0.9.54, that CS/CS2 were more fully supported.

---

### Post by Gwynn on 2008-03-28
Hi Ralphie,  thanks for your response.

Yes, I've installed Photoshop and Bridge from CD1. It's InDesign that I'm particularly in need of installing though.

Ah well... I'll just eat this plateful of humble pie and set about reacquainting myself with Mr. Gates pro tem.

---

### Post by Ralphie on 2008-03-28
ah, yes, someday I hope the whole CS will run natively on linux!

One option, if your computer is quick enough, is to run the whole creative suite, ( indesign... everything...) through VirtualBox.
This is a virtual machine of windows. so basically you would be running both ubuntu and windows at the same time, hence the need for a quick computer. I run this currently, and it runs pretty nicely, and without a hitch.

*edit*
I have looked up indesign CS2 on the wine app db, and it looks as if people are getting it to work with minimal issues!
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9060](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9060)

It might take some tinkering, though.

I think I just might have to mess with this when i get home tonight!

---

### Post by neodarksaver on 2008-03-28
maybe you can try crossover... but it's not free. that's the only problem. but  then, your money to codeweaver goes to those wine developers. so not a bad deal i guess.

---

### Post by Ralphie on 2008-03-28
I doubt crossover will do any better than wine. 
I bought crossover, but currently use wine, just because I haven't found anything that I can do with crossover that I can't do with wine. 

The best thing about crossover is the forums, they offer a lot of help that can actually be applied to Wine. So I'd say just stick with wine, the updates are less of a hassle.

---

### Post by icechen1 on 2008-03-28
Trying the latest WINE version from their site should fix the problem.You are using 0.9.46 and the latest version is 0.9.58.
Site:[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
It seems CS2 won't work in 0.9.44 according to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9060](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9060).

---

