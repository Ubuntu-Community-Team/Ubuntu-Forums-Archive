---
title: "Can't Execute as Root"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Virtunate on 2006-11-09
Okay so I found this guide on the net for getting XGL working. 
[http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/](http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/)
Everything went fine until the end when I try and get the file to the home directory when it says that I don't have the privledges to do that. 
Plus when I tried putting in that .xsession file at the very end of that guide, it screwed with my sessions and I have to revert to the Default GNOME.
Any suggestions?(*,)

---

### Post by CatKiller on 2006-11-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Virtunate on 2006-11-09
Second thing
With that Guide, am I doing it correctly. I put that last command 

sudo chmod +x .Xsession in the script itself. I put myself as root using that guide, but it still does not allow me to save it to my home directory.
Am I doing that last step right?

---

