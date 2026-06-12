---
title: "Some simple questions"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Jaryth on 2007-09-08
Hello hello all, Im Jaryth.
Iv been interested in Linux for a wile, but... just did not know where to start... I tried a few live CD's.. had some bad experiences, and got turned off for a wile (decided to go back to XP) but... then I decided to give it another go.. and found Ubuntu. I must say, I was extremely impressed. An amazing Distro, and (after stalking around these forums for the last few days) an amazing community to come with it!

So... I tried Ubuntu and liked it, and decided to install  (64bit). It went well. I have had some troubles on the way (such as Video card issues, that I later solved), and Iv learned a lot in the process. However, there are a few questions that after a few searches, I still haven't found the answers to. Anyone want to lend out some much appreciated help?
First:

Once Ubuntu starts, I have no trouble mounting my other Partitions (Windows formated NTFS), by entering my user password... the thing that bugs me is I must do this every single time. Is there any way to make it so it automatically connects (Mounts) all of my other partitions on startup? (without needing my password).

Another thing, after a bit of work and some uninstalling and reinstalling, I finally got Beryl and the Emerald theme manager working... but two things about that... for Emerald, all the themes change are the outside rims of the window, and not the colours or buttons at all. The only way to change those is thought the built in Theme manager. Is this normal?
Also, I can get the manager to run on startup, but for some reason I can not get the full beryl (with effects) or the theme manager to start on start up? is there any way to do this? (Every time I have tried, when Ubuntu starts, none of the windows have any outside frames, and the only way to fix it, is to go into the Terminal and type "beryl", then it reloads the options.. however this process does not finish, and if I close the terminal it goes back to the windows with no frames... forcing me to leave that one terminal there, doing nothing.)

So... yes, sorry about the long winded post. If anyone could provide help on these matters it would be very much appreciated! As well, for anyone that does, I thank you for taking the time to read my overly long post.

-Jaryth

:)

**Edit: Everything is pretty much fixed I guess, thanks for the help!**

---

### Post by meborc on 2007-09-08
for ntfs part... install a package called "ntfs-config"... then start it from the admin menu... this will write the correct lines tho the /etc/fstab file, which automounts drives during boot...

---

### Post by tact on 2007-09-08
> **Jaryth said:**
> 
Once Ubuntu starts, I have no trouble mounting my other Partitions (Windows formated NTFS), by entering my user password... the thing that bugs me is I must do this every single time. Is there any way to make it so it automatically connects (Mounts) all of my other partitions on startup? (without needing my password).

You need to enter suitable lines in your fstab file  (it is /etc/fstab).  be sure to back up the file before you edit it.  Exactly what goes in there depends on the file system, what partition it is on,  and so on so you need to give much more info for more specific guidance - or just search the forum here.

> **Jaryth said:**
> 
Another thing, after a bit of work and some uninstalling and reinstalling, I finally got Beryl and the Emerald theme manager working... but two things about that... for Emerald, all the themes change are the outside rims of the window, and not the colours or buttons at all. The only way to change those is thought the built in Theme manager. Is this normal?


Yes its normal.  Icon themes for icons.  Beryl, compiz, and others are window managers and have window decorators (frames etc).

Lots of nice icon themes etc to be found on the net etc. 

> **Jaryth said:**
> 
Also, I can get the manager to run on startup, but for some reason I can not get the full beryl (with effects) or the theme manager to start on start up? is there any way to do this? (Every time I have tried, when Ubuntu starts, none of the windows have any outside frames, and the only way to fix it, is to go into the Terminal and type "beryl", then it reloads the options.. however this process does not finish, and if I close the terminal it goes back to the windows with no frames... forcing me to leave that one terminal there, doing nothing.)


How are you doing it now?  I think the Beryl installation page for ubuntu used to describe how to create a startup script, and how to call it from your session manager so it starts after system startup (a small time delay inserted).

It is certainly easy to do.  More details on what you have tried. Then someone will sure help.

---

### Post by Jaryth on 2007-09-08
@meborc 
Yes, that worked perfectly, thank you Very much for the help!

@tact
thank you for the information on the themes.

As for the Beryl startup, well, I just added a startup command (in System>Preferences>Sessions ) with the name Beryl, and the command... Beryl.

and also, upon disabling it, I find that no matter what, when I first load Ubuntu, until I start up Beryl, I have no window frames (meaning I can not move any windows, nor minimise them. I can however still close them by File>Close). I have a screen shot here as an example of what I see:
[http://img.photobucket.com/albums/v481/jaryth000/Noedges.jpg](http://img.photobucket.com/albums/v481/jaryth000/Noedges.jpg)
as you can see, none of the programs have any Frames... help? XD

However, like I said, once I load Beryl, I get the frames back. However I still do not get the full effects or the Emerald theme, until I enter the Beryl command into the Terminal. But like I said, all it does is sit there after that, and if I close the window Im back to square one.
Here is a screen shot of that too:
[http://img.photobucket.com/albums/v481/jaryth000/beryl.jpg](http://img.photobucket.com/albums/v481/jaryth000/beryl.jpg)

And it just sits there at "Reloading Options" forever.

However I will go look at the Beryl installation page for help, and see if there is anything there.

Thanks for the help thus far!

---

### Post by Jaryth on 2007-09-08
Ok an update:
After checking out the Beryl forum (on Tact's advice) I found a setup script that helped me fix most of the problem...
My last part in that, is there any way to set Beryl as the default window manager when it starts? for some reason it always starts as MetaCity?

(anyone else having the issue I was having with Beryl can check out: [http://forum.beryl-project.org/viewtopic.php?f=36&t=4781](http://forum.beryl-project.org/viewtopic.php?f=36&t=4781) for more information)

---

### Post by tact on 2007-09-08
Ahhh cool - you got it sorted.  (The startup script thing).   Once you mentioned that you put beryl into the session manager (not using script) then we know whats wrong.  You do need that small time delay from booting til Beryl kicks in or it doesn't load right.

Glad that part is sorted.

Now about getting beryl to start up with emerald by default (I presume thats what you mean, tho you didnt say it the same way)....

I see from your screenshots that when Beryl is running you have the red beryl icon thing in your notification area.   I haven't used beryl for a long time (its merged back in with compiz - so I have been using compiz for some months now) - but if memory serves me well I think...  think... that I never had to do anything special to start with emerald.  I just had it selected as the window decorator (right click the red jewel and select emerald) and it came up every time.  (It is possible memory is incorrect - am geting old.  hehehe)

If I remembered wrongly someone may correct me.  Have you considered switching over the the newer compiz-fusion?  You can use emerald with compiz also.

---

### Post by tact on 2007-09-08
Oh yeah..  just a tip.  Regarding those times when you type beryl-manager at a terminal prompt and it holds the terminal open.... if you close it beryl stops again...

Instead of doing it that way - press Alt-F2 and type the command in there.  Then click "run".  This way you dont have a terminal window open all the time just for beryl.  And it remembers the last x commands so next time you hit Alt-F2 you can up/down arrow to find the same command.  No need to type again.

---

