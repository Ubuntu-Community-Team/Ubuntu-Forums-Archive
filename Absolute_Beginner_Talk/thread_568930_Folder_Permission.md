---
title: "Folder Permission"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by zainka on 2007-10-06
Installed Ubuntu, everything OK

I am the  only user and uses the only  account created account
Still. How do I get write access to for examlp etc\firefox folder. Need to replase bookmarks.html, but I do not get the permission for doing it.

I mean, If I try to change grub menu.lst, system asks for admin password. Why would the system not simply do the same here? How do I get folder permissions for the time needed???

---

### Post by taurus on 2007-10-06
Why don't you save bookmarks.html in your own $HOME directory instead of in /etc/firefox?

Otherwise, use sudo command if you need to modify anything outside of your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Frak on 2007-10-06
It should be in your /home/(username_here)/.firefox directory
That can be written to without any special permissions.

---

### Post by zainka on 2007-10-06
Hmm, why didnt i install the folder in my home folder... God question since firefox is preinstalled  by each ubuntu version. So this question should rather be directed to the ubuntu team... 

However, I do not cry...  problem solved by command sudo gedit bookmarks.html 

thanx anyway

---

### Post by taurus on 2007-10-06
> **zainka said:**
> Hmm, why didnt i install the folder in my home folder... God question since firefox is preinstalled  by each ubuntu version. So this question should rather be directed to the ubuntu team... 

However, I do not cry...  problem solved by command sudo gedit bookmarks.html 

thanx anyway

Every program is installed in /usr/bin (/bin) so everybody can use them.  But all your personal settings should go into your own $HOME directory!  That's why there is /home/**USER** for you to use...  :rolleyes:

---

### Post by zainka on 2007-10-06
As before, sounds Ok to me all you say, but I only started to use preinstalled firefox, No one ever asked ME where to put that damn bookmarks.html file. It WILL be installed in etc/firefox by default

---

### Post by mgmiller on 2007-10-06
If you have a default Ubuntu install, look in your home directory in /home/<your user name>/.mozilla/firefox/g0zynpij.default/  you should see a bookmarks.html that you can edit.

That weird folder name g0zynpij.default may be a little different in your machine.

.mozilla is a hidden folder, so you will need to hit ctrl h to make the hidden folders visible in Nautilus.

---

### Post by zainka on 2007-10-08
Right, so the mozilla folder in etc/firefox is more like an profile template then, I guess, used when creating new profiles. I can live with that. Thanks for the info

---

### Post by mgmiller on 2007-10-08
No problem...:popcorn:

---

