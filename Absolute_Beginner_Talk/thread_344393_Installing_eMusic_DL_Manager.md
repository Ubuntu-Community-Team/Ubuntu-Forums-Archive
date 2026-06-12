---
title: "Installing eMusic DL Manager"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-01-22
I am just getting involved with Ubuntu, and have not installed anything outside of automatix yet.  I downloaded the eMusic Download Manager, and I was able to extract the tarball fine.  Now, though, I do not know how to install the dl manager.  I tried executing the "install.sh" file, but nothing happened after that.  I also tried double-clicking the emusicdlm file which is a shell script according to the properties.  Any suggestions?

---

### Post by dbbolton on 2007-01-22
did you try running ./configure

---

### Post by Shatrat on 2007-01-22
tar.gz are a bit more involved than installing something from apt.
Youll probably need to navigate to it in the command line and install it.
If there is an install.sh file then it probably isnt a source code archive with a configure and make file like dbbolton says.  Probably you need to cd to the directory where you extracted it and ```
sh install.sh
``` if it still doesnt run, at least it will print some helpful errors to explain why.

---

### Post by rocknrolf77 on 2007-01-22
Emusic's download manager is not any good. And it's not supported anymore either. It's better to use this one : [http://freshmeat.net/projects/emusicj/](http://freshmeat.net/projects/emusicj/) :)

---

### Post by Darko Beta on 2007-01-23
> **rocknrolf77 said:**
> Emusic's download manager is not any good. And it's not supported anymore either. It's better to use this one : [http://freshmeat.net/projects/emusicj/](http://freshmeat.net/projects/emusicj/) :)

Rolf, thanks a lot!  I was able to install and run the alternate dl manager easily.  :D

---

### Post by davebgimp on 2007-02-26
Yeah the Linux DM really stinks. EMusicJ is the best way to go. Works perfectly.

---

### Post by ishimaru_kaito on 2007-02-26
Sounds tupid, but how would I add this to my menus, rather than running from command line? :(

---

### Post by mr_niceguy on 2007-02-27
> **ishimaru_kaito said:**
> how would I add this to my menus, rather than running from command line? :(

Right click the 'Applications' menu and select 'Edit Menus'. From there you can add an item to the 'Sound & Video' sub menu, name it 'Emusic' or 'EmusicJ' and have it run the command you normally enter on the command line. If you browse the icon directories you may even be able to find something related to music.

---

### Post by ishimaru_kaito on 2007-03-04
Fantastic - works a treat - and I upgraded my emusic account because it is all so smooth - now, an extra hard drive for the tunes! \\:D/

BTW - it's all good - emusic, amarok and the ipod all working together to keep my daily commute to work interesting 8-)

---

### Post by nandasunu on 2007-04-16
This is just a thanks for this tip, its helped me out too :)

---

### Post by rocknrolf77 on 2007-04-18
Tip : Songbird now has an emusic store addon :)

---

