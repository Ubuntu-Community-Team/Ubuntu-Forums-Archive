---
title: "What am I doing wrong?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by dittyman1 on 2006-08-24
I tried installing automatix, but I must have done something wrong, since nothing happened.  I thought I followed the instructions in the automatix wiki.  What needs to be put into the text editor (I'm using gedit) and what needs to be put into the terminal?  Thanks guys.

---

### Post by mssever on 2006-08-24
Perhaps you can give us some more details? Have you tried the instructions [here]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix")?

---

### Post by dittyman1 on 2006-08-24
Yep.  I was trying to install using that wiki.  

"Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Next you must get our GPG key in order to authenticate our repository:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -"

That's the part of the wiki that was confusing me.  My question is, I guess, does all of that have to go into the terminal?  Because I wasn't expecting to also be using the text editor.

Thanks.

Mark

---

### Post by Fedz on 2006-08-24
I right clicked the link and saved it on desktop and renamed it from .html

Then open right click and chmod permission too 755 as it needs execute access.

Open terminal screen and type **./automatix-installer**

Sick back and watch a wall of text as the terminal screen downloads the install and after awhile pops up loads of software and I can tell you they all work like a dream (for me).

Totum video player with browser plug-in and all codecs get put in if you select it from the list and XMMS is great for music and streaming (audio).

Hope this helps

---

### Post by mssever on 2006-08-24
Copying from the site I linked to earlier:
> Open up terminal and paste the following lines one after the other (wait for each command to finish before you paste the next)  ```
wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer
```

---

### Post by dittyman1 on 2006-08-24
Sweet.  Thanks man.  I'll try it that way instead.

---

