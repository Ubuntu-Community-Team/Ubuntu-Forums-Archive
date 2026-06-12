---
title: "Can't find Tomboy"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by SiteFodder on 2006-12-02
This may be really silly.  The Synaptic Package manager shows that I have Tomboy installed.  I can't find it.  So I reinstalled it with Synaptic Manager.  Still can't find it.  Where am I going wrong?  I am using 6.10 Edgy Eft.

Thanks

---

### Post by ciscosurfer on 2006-12-02
What happens when you hit ALT-F2 and type in [B]tomboy

[/B]Here's the fix: go to a terminal and enter the following```
sudo gedit /usr/share/applications/tomboy.desktop
```scroll to the bottom and completely remove the line that says **OnlyShowIn=KDE**;  

Save the file, and close GEdit.  You can now logout and then log back in for the changes to take effect or you can issue the following in a terminal again to get the same effect```
sudo killall gnome-panel
```Tomboy will now be located under your Applications > Accessories menu

Cheers!

---

### Post by SiteFodder on 2006-12-02
It brought it up.  Shouldn't there be an Icon somewhere?  Thanks for the help

---

### Post by ciscosurfer on 2006-12-02
Read my original post again.  I added more info.

Cheers!

---

### Post by linux-beginner on 2006-12-02
I've got the same problem. Frist time Tomboy runs with "run Application" but after change of tomboy.desktop I can't run it! Now I have it in Application tab but it doesn't run!

---

### Post by lamego on 2006-12-02
In case you want to upgrade to tomboy 0.5.1 and get a proper menu entry:
[http://www.getdeb.net/app.php?name=tomboy](http://www.getdeb.net/app.php?name=tomboy)

---

### Post by ciscosurfer on 2006-12-02
> **linux-beginner said:**
> I've got the same problem. Frist time Tomboy runs with "run Application" but after change of tomboy.desktop I can't run it! Now I have it in Application tab but it doesn't run!Sorry 'bout that. :(  I ran into the same problem as all of you when doing my suggestion.  At this point, I would suggest possibly running the newest version as posted above (the dev version).

EDIT: Confirmed.  Thanks, lamego!

EDIT: @lamego, did you create the .deb for Tomboy located at getdeb.com?  I noticed in /usr/bin/tomboy that your username is in there....hmm...

EDIT: @lamego, nevermind. ](*,) I noticed you are software packager in your signature. \\:D/

---

### Post by wyth on 2006-12-06
It's a panel application.  Right-click on the panel, click on Add to Panel, and it's in there.

---

