---
title: "Stuck on splash screen please help!"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by dcbtfoabaaposba7 on 2007-03-25
Hey, 
Story-

I was changing my computers theme and when i clicked to change the theme my computer icons all dissapeared and everything all went away. My moues could move around but there was nothing to click and right click didn't work. I decided to unplug my computer and when i turned it back on and loged in, my computer got stuck on the splash screen. I've tried several times, it will not get pass this screen. What did i do to cause this? how can i fix this? thanks a lot for any help.
This is kinda urgent since i have all my school papers on that computer.!

---

### Post by alienexplorers on 2007-03-25
Boot into recovery mode and login.  You have to then type startx (or sudo startx). See if this gets you in.

---

### Post by dcbtfoabaaposba7 on 2007-03-26
Thanksss. Okay that let me get into recovery mode, but how to i fix the problem for booting in normal mode?

---

### Post by philipho on 2007-03-26
Did you do a backup of your xorg.conf file?

---

### Post by dcbtfoabaaposba7 on 2007-03-26
No, i dont think so. Is it to late to do that? If not, how do you do it? thanks

---

### Post by cowlip on 2007-03-26
try this if you need access quickly, you'll lose all desktop customizations (although you can restore them easily because they have been backed up):


Do while in your ~ (home) folder, perhaps you can copy these into a shell script:

mv .gnome2 .gnome2.old
mv .gnome .gnome.old
mv .gnome-private .gnome-private.old
mv .gconf .gconf.old
mv .gconfd .gconfd.old
mv .gnome-desktop .gnome-desktop.old
mv .gnome2_private .gnome2_private.old
mv .gnome_private .gnome_private.old
mv .metacity .metacity.old

Also, are there any errors in ~/.xsession-errors ?

less .xsession-errors

[http://gnomesupport.org/forums/viewtopic.php?t=10465](http://gnomesupport.org/forums/viewtopic.php?t=10465)

---

### Post by dcbtfoabaaposba7 on 2007-03-26
I found someone with a similar problem. 

[http://ubuntuforums.org/showthread.php?t=304562&highlight=splash+start+up+froze]("http://ubuntuforums.org/showthread.php?t=304562&highlight=splash+start+up+froze")

He said he got it fixed by just deleting a ~/.icons directory. I searched for this but i couldnt find it. How can i find and delete this. 

Also, how do you start a shell script. Im sorry for all these questions- im still new to this.
If anyone can help, thankss.

---

### Post by cowlip on 2007-03-26
It's ok, I should have just made one for you :)  To find a directory with a '.' in front of it, you need to unhide folders.  Do this in a terminal with 'ls -al', or in Nautilus with CTRL + H or right clicking and choosing 'show hidden files'.

```

#!/bin/sh
mv .gnome2 .gnome2.old
mv .gnome .gnome.old
mv .gnome-private .gnome-private.old
mv .gconf .gconf.old
mv .gconfd .gconfd.old
mv .gnome-desktop .gnome-desktop.old
mv .gnome2_private .gnome2_private.old
mv .gnome_private .gnome_private.old
mv .metacity .metacity.old

```

copy that into a text editor and save it to your HOME folder (~) as 'shellscript.sh'.  Then open a terminal up.  Do this, making sure you're in the same directory:

chmod +x shellscript.sh
./shellscript.sh

If that doesn't work, can you "unhide" hidden files in Nautilus by right clicking or pressing CTRL + H, and then copy and paste the text in the file '.xsession-errors'?  Or try to open it in a terminal with:

gedit ~/.xsession-errors

---

### Post by dcbtfoabaaposba7 on 2007-03-28
Im still facing the problem. I did as you said and got this:

[HTML]root@nathaniel-desktop:~# chmod +x shellscript.sh
root@nathaniel-desktop:~# ./shellscript.sh
mv: cannot move `.gnome2' to a subdirectory of itself, `.gnome2.old/.gnome2'
mv: cannot move `.gnome' to a subdirectory of itself, `.gnome.old/.gnome'
mv: cannot stat `.gnome-private': No such file or directory
mv: cannot move `.gconf' to a subdirectory of itself, `.gconf.old/.gconf'
mv: cannot move `.gconfd' to a subdirectory of itself, `.gconfd.old/.gconfd'
mv: cannot stat `.gnome-desktop': No such file or directory
mv: cannot stat `.gnome2_private': No such file or directory
mv: cannot stat `.gnome_private': No such file or directory
mv: cannot move `.metacity' to a subdirectory of itself, `.metacity.old/.metacity'
[/HTML]

thanks for your reply. I did the xsession-errors thing and now one of my calenders that i had on my desktop appeared but nothing else. Am i getting close to fixing this? please helpp. thanks

---

### Post by dcbtfoabaaposba7 on 2007-03-29
Bump! -Please help me with this. I am so desperate :( :(

---

### Post by cowlip on 2007-03-29
These are ok, I just couldn't remember if they existed

```
mv: cannot stat `.gnome-desktop': No such file or directory
```

It's this "cannot move to a subdirectory: error that makes me go, "what?" ```
mv: cannot move `.metacity' to a subdirectory of itself, `.metacity.old/.metacity'
```

---

### Post by cowlip on 2007-03-29
OK...are you in your /home/yourusername here directory when you run that script?  Or are you in the recovery's login?  Because this ```
**root**@nathaniel-desktop:~#
``` made me wonder; I think most people run as a normal user with Ubuntu.

Make sure you are in the /home directory where you lost your gnome panel.

---

### Post by dcbtfoabaaposba7 on 2007-03-30
Yeah, im in recovery mode when i did it. I just copied and made that script then clicked my terminal icon on my desktop and pasted the code in. when i click my home folder it takes me to my root folder, so i guess its the same thing? 
thanks for the reply.

---

### Post by dcbtfoabaaposba7 on 2007-04-03
bump..

---

