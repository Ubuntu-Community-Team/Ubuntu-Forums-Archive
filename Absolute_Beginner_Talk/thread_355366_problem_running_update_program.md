---
title: "problem running update program"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by homh on 2007-02-07
Ther is an icon on my computer that says updates are available for downloading.  When I try to run that program I get the message

An error has occurred.  
E: dkpg was interrupted.  You must manually run 'dkpg --configure -a' to correct the problem.

How do I do this?  When I go into terminal mode and type that line it doesnt work and I get a list of possible commands to use.

I cant downlaod and install any more programs until I get this fixed.

---

### Post by DougieFresh4U on 2007-02-07
open terminal-Applications>Accesories  and type code- **sudo dpkg --configure -a** and that should take care of your error):P Dougie

---

### Post by homh on 2007-02-07
Thank you!

That was easy. 

But now I get another error message when I try to run the update program.

An Error has occurred

E: /var/cache/apt/archives/dnsutils_1%3a9.3.2-2ubuntu3.1_i386.deb: corrupted filesystem tarfile - corrupted package archive

---

### Post by taurus on 2007-02-07
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DougieFresh4U on 2007-02-07
See what happens with code **sudo apt-get -f install** What were you trying to install when your problem started?

---

### Post by homh on 2007-02-07
DougieFresh4U, your suggestion didnt work, I received the same error message as before.

But Taurus' worked.  Everything seems to be back to normal now.l  I tried downloading another program to test it and all went well.  THANK YOU THANK YOU VERY MUCH!!!


This was all my fault, I think.  Yesterday I received the notice that there were some updates available for downloading and I clicked on the icon in the upper right hand corner of my screen.  It downloaded the updates and started to install them and then everything seemed to freeze and there wasnt any more activity.  I coudnt do anything so I turned off the power to my computer and then turned it back on.  Thats when I started having problems.  

Everyone here is terrific and I thank both Dougie and Taurus for your help getting things working right again.

---

### Post by taurus on 2007-02-07
Glad to hear everything is back up and running again for you.  Got another problem, you know where to post now.

---

