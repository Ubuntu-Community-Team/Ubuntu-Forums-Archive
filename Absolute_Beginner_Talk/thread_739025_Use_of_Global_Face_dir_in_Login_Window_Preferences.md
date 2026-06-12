---
title: "Use of Global Face dir in Login Window Preferences"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-03-29
Can not seem to find any document on this.

I am using Human List option in login window preferences. This one shows the names of the users with a dummy face at the side. Out of pure hunch, I tried to use Global Face dir. I have put username.png files (world readable) in /usr/share/pixmaps. But the faces are not shown in Login Window.

(See attachments for the set up tabs I am talking about)

If my hunch about showing faces was not correct, sorry, I wasted your time. But if it was correct, please let me know what is it I am missing. How can I show individual faces at the login window?

Thanks..

---

### Post by Oldsoldier2003 on 2008-03-31
[http://ubuntuforums.org/showpost.php?p=4040588&postcount=3](http://ubuntuforums.org/showpost.php?p=4040588&postcount=3) explains in a little more detail what to do to get facebrowser working

---

### Post by mmasroorali on 2008-03-31
Somehow it did not work for me. Still my login window shows the default icons.

Please see the debugging snapshot.

---

### Post by kaivalagi on 2008-03-31
your symlink has the wrong name, you require it to be called .face

Looks like you created a folder called .face/ and symlinked something like:
```

cd ~/
ln -s /path/to/you/image ~/.face/
```

The command should be in the form:

```

ln -s /path/to/you/image ~/.face
```

You can also just copy your image to the home folder and rename it to .face

Hope that helps

---

### Post by mmasroorali on 2008-04-01
Again it does not work. 

These are the commands I have executed,

Previously created directory was removed,
   rm -rvf .face/
  
The symlink was created,
   ln -s /usr/share/pixmaps/masroor.png ~/.face

Check that this is really an image,
   display .face

I logged out, rebooted the machine, still it did not work. Frustrated.

---

### Post by kaivalagi on 2008-04-01
Try doing it with the gnome tool:

```
gdmphotosetup &

```

You are running GDM right?

---

### Post by mmasroorali on 2008-04-07
gdmphotosetup gave the solution.

A BIIIIIG thanks.

---

### Post by kaivalagi on 2008-04-07
No worries, glad I could help

---

### Post by ad_267 on 2008-04-07
Also if anyone else wants to know, you can just go System - Preferences - About Me and then click on the picture next to your name.

---

### Post by kaivalagi on 2008-04-07
Thats good to know :)

Except, when I tryed to open the dialog it crashes, see attachment. This is all because I removed evolution as I use thunderbird for emails and calendar.

If anyone has the same problem as this, re-install the evolution data server package and dependencies to fix it. Atleast you don't need a bulky evolution install.

```
sudo apt-get install evolution-data-server
```

---

