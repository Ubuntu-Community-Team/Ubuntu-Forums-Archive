---
title: "/etc/gdm"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-04-17
I have been playing around with XGL. I downloaded it from the repos, and am trying to get it to work. I am following the instructsions here

[http://www.rage3d.com/board/showthread.php?t=33847510](http://www.rage3d.com/board/showthread.php?t=33847510)

1) are these good instructions for me to follow. I am running kubuntu dapper flight 6 (KDE) and have an intel intergrated chipset.

2) at step 4, it says 
```
Modify /etc/gdm/gdm.conf-custom
```

I cant find this file. I dont even think I have the directory /etc/gdm

Is this normal>? Did I miss an installation or something?

Thanks so much.

---

### Post by K.Mandla on 2006-04-17
EDIT: Sorry, not the right answer. Ignore this post, please. :rolleyes:
2nd EDIT: Okay, I think I did my homework this time. Not having the /etc/gdm might have something to do with using KDE, since gdm is the Gnome desktop manager. You might have some luck with instructions here. ...

[http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077)

or here. ...

[http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

---

### Post by Qrk on 2006-04-17
The instructions should probably read 

```
sudo gedit /etc/gdm/gdm.conf-custom
```

But personally, I'd recommend just:

```
sudo ln -sf /usr/bin/Xgl /etc/X11/X
```

and restarting X. That way, if something goes wrong, you haven't changed anything.

---

### Post by Paul Bennett on 2006-04-18
Thank you K.Mandla. Those links are better for hat im trying to do. I will definatly use them.

If I do

```

sudo ln -sf /usr/bin/Xgl /etc/X11/X
```

I did that once and restarted, but could not logon. Wehn I entered my username and pass, the screen want balnk for a few seconds then returned to the login screen. So I changed it back. Any ideas what I did wrong?

Is that the "same thing" as editing the file? Can I do that instead of editing?

Thanks so much.

---

### Post by Qrk on 2006-04-18
It isn't the same thing as editing the file. If you wanted to use the sym link, you would do that instead of editing your gdm config.

X (/etc/X11/X) is a symlink. You can change that to either point to x.org or Xgl. I recommended it because all you need to do to reverse the changes is to:

```
sudo ln -sf /usr/bin/Xorg /etc/X11/X
```

Which points X back to xorg. That way if something doesn't work, you haven't changed anything drastic. The disadvantage is that you won't easily switch between the two at gdm start up. 

If you want to switch back to x.org, for example, you'd have to run the above command and restart X instead of being able to select xorg as an option on the Gdm screen.

The guide on the wiki page does it doing this method. 
[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)

---

