---
title: "'Alacarte menu Editor' Doesn't work."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2006-06-18
I open alacarte and try to move files up the ladder and some apps I don't want on the list so I un-check the boxes but when I close Alacarte and then go into the menu nothing is changed.
When I first installed Ubuntu (Dapper) it worked, but now it dosn't seem to want to respond to any thing I do to the Menu.

Any Ideas why this would happen or how to fix the problem?

---

### Post by ComplexNumber on 2006-06-18
try logging out then logging back in again.

---

### Post by user1397 on 2006-06-18
or try pasting this into a terminal: ```
killall gnome-panel
```

---

### Post by nitricacid on 2006-06-18
[QUOTE=ComplexNumber]try logging out then logging back in again.[/QUOTE]

I have done this (even restarted computer) and the menu still stays the same.

---

### Post by nitricacid on 2006-06-18
[QUOTE=erik1397]or try pasting this into a terminal: ```
killall gnome-panel
```[/QUOTE]

What happens if I do this and then I can't get any apps back to my menu?

---

### Post by Anduu on 2006-06-18
What version of Alacarte are you using...the one from the repos is 0.8 but there is a version 0.9 available...

Check here [http://www.ubuntuforums.org/forumdisplay.php?f=67](http://www.ubuntuforums.org/forumdisplay.php?f=67)

I was having a lot of problems with 0.8.

0.9 still isn't perfect but it solved a lot of issues for me.

---

### Post by user1397 on 2006-06-18
[quote=Anduu]What version of Alacarte are you using...the one from the repos is 0.8 but there is a version 0.9 available...

Check here [http://www.ubuntuforums.org/forumdisplay.php?f=67]("http://www.ubuntuforums.org/forumdisplay.php?f=67")

I was having a lot of problems with 0.8.

0.9 still isn't perfect but it solved a lot of issues for me.[/quote]yes i also have 0.9, it worked fine for me too.
the killall gnome-panel command does not delete your panels, it just updates them, so there's nothing to worry about.

---

### Post by nitricacid on 2006-06-18
[QUOTE=Anduu]What version of Alacarte are you using...the one from the repos is 0.8 but there is a version 0.9 available...

Check here [http://www.ubuntuforums.org/forumdisplay.php?f=67](http://www.ubuntuforums.org/forumdisplay.php?f=67)

I was having a lot of problems with 0.8.

0.9 still isn't perfect but it solved a lot of issues for me.[/QUOTE]

Still using 0.8 (found in synaptic).
I just downloaded 0.9 and wondering if Could I bother you for the install command?
I rarely ever use .deb files\manual installing (usually all done through synaptic).

I will try this and then let ya's know if the problem is fix.

---

### Post by Anduu on 2006-06-18
Just make sure GDebi Package Manager is installed and all you need to do is double click on a .deb file and it will install.

You may have to right click and "open with" GDebi.

---

### Post by nitricacid on 2006-06-18
[QUOTE=Anduu]Just make sure GDebi Package Manager is installed and all you need to do is double click on a .deb file and it will install.

You may have to right click and "open with" GDebi.[/QUOTE]

I get this message when I open the file in GDebi:

"An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported."

Don't know if this mean Gdebi is an old version or...

BTW, i am installing alacarte 0.9.

---

### Post by user1397 on 2006-06-18
[quote=nitricacid]I get this message when I open the file in GDebi:

"An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported."

Don't know if this mean Gdebi is an old version or...[/quote]no its talking about alacarte having an older version (0.8) but dont bother with it, just install 0.9.

---

### Post by nitricacid on 2006-06-18
[QUOTE=erik1397]no its talking about alacarte having an older version (0.8) but dont bother with it, just install 0.9.[/QUOTE]

Ok, I just got done installing 0.9 and now when I open Alacarte it doesn't respond to check/unchecking boxed and I can't move any of the apps up or down the colums.

---

### Post by Anduu on 2006-06-18
Try running it as sudo and see what happens..."sudo alacarte" from a terminal

---

### Post by nitricacid on 2006-06-18
[QUOTE=Anduu]Try running it as sudo and see what happens..."sudo alacarte" from a terminal[/QUOTE]

It runs under sudo but still the same problem. #-o
It seems this only happen since i installed VLC and it made an icon in the Applications>Sound & Video section.

---

### Post by Anduu on 2006-06-18
Hmmmm...well I don't know what to say.

Instead of the "killall gnome-panel" route you can just try restarting and try again.

---

### Post by user1397 on 2006-06-18
[quote=nitricacid]It runs under sudo but still the same problem. #-o
It seems this only happen since i installed VLC and it made an icon in the Applications>Sound & Video section.[/quote] did you ever try the killall gnome-panel command?  try it, and then try uninstalling VLC to see if it works, and if it still doesn't, just reinstall VLC
[quote=Anduu]Try running it as sudo and see what happens..."sudo alacarte" from a terminal[/quote]actually, for opening graphical applications with the terminal, the command "gksudo <command>"is recommended, instead of "sudo <command>", as that may cause problems.

---

### Post by nitricacid on 2006-06-18
should Ubuntu-desktop be installed?
I killed Ubuntu-Desktop Kill all the games I don't need or want so I could save some space

---

### Post by user1397 on 2006-06-18
[quote=nitricacid]should Ubuntu-desktop be installed?
I killed Ubuntu-Desktop Kill all the games I don't need or want so I could save some space[/quote]what do you mean you "killed ubuntu-desktop"? you uninstalled it or what?  yes you should have the ubuntu-desktop package.  it's just a metapackage that links to all of the other packages in the ubuntu-install.

---

### Post by nitricacid on 2006-06-18
I have tried everything listed in this thread and I am greatly thankfull to everyone that helped but everything I tried did not seem to work.

Alacarte just does not want to let me check/uncheck or move anything.

Does anyone know any other ways of editing the Menu list?

---

### Post by Anduu on 2006-06-18
> actually, for opening graphical applications with the terminal, the command "gksudo <command>"is recommended, instead of "sudo <command>", as that may cause problems.

Well when I use gksudo it edits the entries of the root account.These changes are *only* reflected when logged in as root.

---

### Post by nitricacid on 2006-06-18
[QUOTE=Anduu]Well when I use gksudo it edits the entries of the root account.These changes are *only* reflected when logged in as root.[/QUOTE]

Could you tell me what folder holds all the apps that are in the Menu?

---

### Post by nitricacid on 2006-06-18
Does anyone know if I should installed the PATCH that from this site? [http://www.realistanew.com/projects/alacarte/](http://www.realistanew.com/projects/alacarte/)
I am pretty sure I have everything else installed that I need to run this app.

Also, how would I go about installing the patch?

---

### Post by user1397 on 2006-06-18
[quote=nitricacid]Does anyone know if I should installed the PATCH that from this site? [http://www.realistanew.com/projects/alacarte/]("http://www.realistanew.com/projects/alacarte/")
I am pretty sure I have everything else installed that I need to run this app.

Also, how would I go about installing the patch?[/quote]how did you install version 0.9?  was it from the forums thread: [http://ubuntuforums.org/showthread.php?t=163272&highlight=alacarte+0.9](http://ubuntuforums.org/showthread.php?t=163272&highlight=alacarte+0.9) ?

---

### Post by siguy on 2006-06-26
I have the exact same problem. Changing Alacarte versions did nothing. There must be some way I can just directly edit the menu, right? Some files somewhere?

Alacarte just refuses to work for me no matter how I run it or what version.

---

### Post by dngpng on 2006-07-01
My Alacarte also could not remeber my choice, no matter I "killall gnome-panel", logout and login or even restart the computer. I know there's some way to edit the menu entry(e.g. to directly edit those .desktop files), but it's quite inconvenient without Alacarte.

There should be some reason, or maybe a bug. Hope anyone would help. Thanks in advance!

---

### Post by Daishiman on 2006-07-01
Same thing here.

Seriously, where does Gnome store its menu settings?

---

### Post by dngpng on 2006-07-01
> Seriously, where does Gnome store its menu settings?
under /usr/share/applications/, you can edit those .desktop files as to change the menu items.

---

### Post by dngpng on 2006-07-10
I finally find a solution to my problem. Probably it helps in your case:

I think there may be something wrong with the file permissions in my $HOME folder, so i just do a simply 

```
sudo chown MY_USER_NAME .*
```
and
```
sudo chgrp MY_SUER_NAME .*
```

in my $HOME folder (/home/MY_USER_NAME).

---

