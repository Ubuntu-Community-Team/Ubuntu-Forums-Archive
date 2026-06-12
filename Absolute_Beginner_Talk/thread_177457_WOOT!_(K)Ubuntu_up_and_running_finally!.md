---
title: "WOOT! (K)Ubuntu up and running finally!"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by cdi3d on 2006-05-16
Had to wait for the Shipit disks but they worked like a jewel. 
Im now the very pleased owner of a working ubuntu dist. Apt-got the kde desktop and Im good to go. 

But wait, you thought that was all didnt you? Oh no my new friends I now have some questions. 
First let me say Im minimally familiar with the *nix systems. I initally tried Debian and its nice but didnt suit me. So I was recommended Ubuntu. 

Ok the questions. 

1. After a lot of searching I downloaded a few themes, and was attempting to copy their folders to the themes folder in /usr/share. However the system tells me I cant do that because I dont have permission. Is this a case of needing "sudo"? Is this even normal?

2. Mpeg decoders. I tried viewing an mpeg and totem (I believe that was the name?) said I didnt have any decoders installed? I tried to apt get one and it didint seem to work (unless I need to reboot in which case it will work tonight). Barring the rebooting scenerio, can someone recommend one that will work? 

3. Updates. The only thing I liked about the intial use of Gnome was the nice lil update alert. Is there a way to get this working in KDE?

4. Apologies for so many questions Ill try not to make this a habit. Last one now: Wine. Yah I can hear the groans. Sorry folks. Anywho I would completely remove windows from my life if I could get one single game I play working in wine. I read some info on making it work but it seems very involved. I was wondering if wine has improved to the point where World of Warcraft (please dont think ill of me, Im a hopeless addict!) works well and easily within it? Any current users/junkies have some tips or tutorials?

Thanks for any anwers/assists on this.

---

### Post by Jagot on 2006-05-16
1) Run the command 'kdesu konqueror' in Kubuntu or 'gksudo nautilus' in Ubuntu which will allow you to have root access to the files so you should be able to copy then.  You can read more about that here: [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

2) [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by frodon on 2006-05-16
For the second question this wiki page will answer all your questions : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

4- [http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

---

### Post by cdi3d on 2006-05-16
Excellent, thanks to both of you.

Edit. I almost missed your link for no. 4. This was the article I read as well. So this is the most up to date method for getting WOW working with wine? Alrightie then, Ill make that a weekender project.

---

### Post by frodon on 2006-05-16
If you are a gamer you can try also cedega, it's far better than wine but you have to pay for it or compile it yourself from CVS : [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS)
And a thread about it : [http://ubuntuforums.org/showthread.php?t=81232](http://ubuntuforums.org/showthread.php?t=81232)

---

### Post by Sef on 2006-05-16
Congrats. If you have any more questions, post them please.

---

### Post by nalmeth on 2006-05-16
hmm I don't think there's any update-notifier for KDE in Breezy, but there's one in dapper.

couple weeks from release too

---

### Post by cdi3d on 2006-05-16
Im  looking forward to dapper. I considered a full dist upgrade to it, but figgered Id just wait for the release since its so close. 

Thanks all for the answers.

---

