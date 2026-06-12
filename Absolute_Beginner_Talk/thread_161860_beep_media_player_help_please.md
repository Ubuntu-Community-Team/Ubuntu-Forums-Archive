---
title: "beep media player help please"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-17
Im trying to get an mp3 player to work and have nice skins.  I downloaded xmms skins following this thread: 
[http://www.ubuntuforums.org/showthread.php?t=77694](http://www.ubuntuforums.org/showthread.php?t=77694)
I saved it in home, and see the skin folder in home folder, but when i try to move it with the cp code it says this:
ryan@ubuntu:~$ cp Winamp5-XMMS /home/ryan/.xmms/Skins
cp: omitting directory `Winamp5-XMMS'
ryan@ubuntu:~$
so i cant select the skins for winamp.  
So I moved onto beep media player, it doesnt even open, i click it in the menu, and nothing. i uninstalled xmms player, then i uninstalled beep media player, then re installed beep media player, click on it in menu, and nothing happens.  Can someone please tell me how to either get skins to work for xmms or how to fix beep media player??? :confused:

---

### Post by jazzmuzik on 2006-04-17
The copy command doesn't quite know what you want to copy since Winamp5-XMMS is a directory, not a file. Try this:

cp -a Winamp5-XMMS /home/ryan/.xmms/Skins

The -a switch tells it to copy recursively, which means to copy the directory and all the contents below it.

Type 'man cp' for more info on the copy command.

---

### Post by x5452 on 2006-04-17
ill try that when i reinstall xmms thanks, any ideas on why my beep player wont do anything?  Id like to get it working since the skins look better](*,)

---

### Post by Perfect Storm on 2006-04-17
eherm...if you are using bmp why would you copy it to a xmms?

```
cp <name of the package> /home/<username>/.bmp/Skins
```

Edit: You should not not unpack the files

---

### Post by x5452 on 2006-04-17
i havent used any yet, i WANT to use beep, but it wont do anything, i click the icon in the menu and it just, does nothing, nothing pops up, no menu, no window ect.  I was asking about xmms because ill need something eventually, but I want to get beep working for better skins, but i dont know how.  do you know any way to diagnose beep media problems?

---

### Post by Perfect Storm on 2006-04-17
Try run 

```
beep-media-player
```
in the terminal.

Also try with remove .bmp folder (make a backup of it first.)

---

### Post by x5452 on 2006-04-18
when i type beep-media-player in the terminal it does nothing, just gives me a new line to write on.  

> Also try with remove .bmp folder (make a backup of it first.)

How do you do this?

---

### Post by GarethMB on 2006-04-18
[QUOTE=x5452]i havent used any yet, i WANT to use beep, but it wont do anything, i click the icon in the menu and it just, does nothing, nothing pops up, no menu, no window ect.  I was asking about xmms because ill need something eventually, but I want to get beep working for better skins, but i dont know how.  do you know any way to diagnose beep media problems?[/QUOTE]

Open the system monitor (its in system tools).

Check that there aren't any sleeping beep processes. If there are kill them.

Then retry ```
beep-media-player
```

---

### Post by x5452 on 2006-04-19
can beep media player only install tar.gz files for skins?  on the muhri website, it says to go to skinz.org or customize.org, but there is no section for bmp or xmms skins. there is winamp though, but the files are all bin .wal or something, is there a way to make those installable?  Or is tar the only ones.. They have real cool one there!!

---

### Post by IYY on 2006-04-19
Just open the theme select window in beep, and drag-and-drop your theme file there. I believe it works.

---

### Post by x5452 on 2006-04-19
for what types of files though? the ones so far havent worked, like .zip and .wal

---

### Post by Perfect Storm on 2006-04-19
I have both wsz, zip and wal in /.bmp/Skins
But it's not all the skins from winamp xmms/bmp can use. Those fancy completly changed winamp skins which have another structure and special features won't work.

---

### Post by x5452 on 2006-04-19
aahh, ok that makes sense, because i was able to drag and drop some zip and some wsz into the bmp pref window, but some i could not, so i was confused.  do you know where to go to get bmp skins that change the shape, make it look more like just a little reciever thing?

---

### Post by Perfect Storm on 2006-04-19
You can only use skins which fits the one I've attached to the post. If the skin use the old winamp format you should not have any trouble using them/it.

---

