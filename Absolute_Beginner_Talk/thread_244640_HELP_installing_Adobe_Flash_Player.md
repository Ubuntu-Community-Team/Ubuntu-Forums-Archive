---
title: "HELP installing Adobe Flash Player"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-08-26
New to ubuntu and need help on how to install Adobe Flash Player....beginner here.

---

### Post by nickpaton on 2006-08-26
I assume this is for use with Firefox Browser.

Close Firefox.

```
sudo apt-get install flashplugin-nonfree
```

```
sudo update-flashplug
```

When you restart Firefox, Flash should work.

---

### Post by bvexen2 on 2006-08-26
Yes, with firfox browser.  Do I just paste that coding into Terminal?

---

### Post by nickpaton on 2006-08-26
Yup - simply copy from the post and paste into the Terminal, and hit enter between each line.

If you have not used Terminal before, when you hit enter it will ask you for your password (same as you used to initially log in).  
As you put in each character of your password, note that the cursor will not move.  
This is normal!

Let us know how you get on & good luck!

---

### Post by Sonic Reducer on 2006-11-23
i got this output when i entered the first line into terminal:

```
ryan@ryan-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
ryan@ryan-desktop:~$
```

whats up with this, all my apt-get's don't work

---

### Post by shirilover on 2006-11-23
You probably need to add the universe/multiverse repositories.

[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto]("https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto")

---

### Post by _simon_ on 2006-11-23
Try it this way:

Download Flash Player 9 beta 2 from here: [http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b2_installer_linuxplugin)

Then place it in /usr/lib/firefox/plugins

Restart firefox if already open and that should be it.

---

### Post by Sonic Reducer on 2006-11-23
> Error while copying to "/usr/lib/firefox/plugins".
You do not have permissions to write to this folder.
thats what i get when trying to drag libflashplayer.so into /usr/lib/firefox/plugins

i'm trying the universe/multiverse thing right now

---

