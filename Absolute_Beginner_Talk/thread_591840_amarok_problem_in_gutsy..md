---
title: "amarok problem in gutsy."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ubunter1 on 2007-10-25
hi,i am using gutsy that was a clean install from fiesty,so far like it very much but am having a problem with amarok,when i try to use it a dcopserver error message appears and says to make sure its running.i use gnome and have in the past with no problems.thanks------- 


   robert@robert-desktop:~$ amarok
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robert/.kde/socket-robert-desktop/kdeinit__0'
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robert/.kde/socket-robert-desktop/kdeinit__0'
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robert/.kde/socket-robert-desktop/kdeinit__0'
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype Amarok/Plugin not found
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robert/.kde/socket-robert-desktop/kdeinit__0'
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/share: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/socket-robert-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/robert/.kde/socket-robert-desktop/kdeinit__0'
There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/robert/.DCOPserver_robert-desktop__0

Please check that the "dcopserver" program is running!
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
trying to create local folder /home/robert/.kde/cache-robert-desktop: Permission denied
kbuildsycoca: ERROR creating database '/home/robert/.kde/cache-robert-desktop/ksycoca'! Permission denied
robert@robert-desktop:~$

---

### Post by ryanVickers on 2007-10-25
it looks like you don't have permissions to that directory - try changing them to be all access, all the time ;)

Also, I would really recommend Exaile over any other player :p
Just my opinion ;)

---

### Post by ubunter1 on 2007-10-26
its weird but ktorrent didn't work as well both these are kde progs,but i had no trouble in the past. i just installed exaile,but the two things i liked about amarok i cant figure how to do in exaile.1-list new songs on screen when listening to music on the net or a cd and the big one is 2- putting a icon in the right side bar to show the program is on(im still a noob) .im running gutsy btw.thanks.

---

### Post by ryanVickers on 2007-10-26
I'm guessing on what you mean for both of these questions, so forgive me if the answers don't help ;)

1. In exaile, You can rightclick an artist/album/genre, etc and "send to new playlist" or something like that, then just double-click the playlist

2. I thought that by default Exaile put's an icon in the notification area...

---

### Post by ubunter1 on 2007-10-26
> **ryanVickers said:**
> I'm guessing on what you mean for both of these questions, so forgive me if the answers don't help ;)

1. In exaile, You can rightclick an artist/album/genre, etc and "send to new playlist" or something like that, then just double-click the playlist

2. I thought that by default Exaile put's an icon in the notification area...

in amarok a shadow like box appeared anytime a new song came on,thats what i meant,sorry for the confusion,and in the notif  area on the right its icon is missing and dont know how to put one there.

---

### Post by ryanVickers on 2007-10-26
ok, ok then ;)

1. go into Tools --> Configure Amarok --> OSD and turn it off ;) (I think :p)

2. No idea, sorry :(

---

### Post by ubunter1 on 2007-10-26
how about doing it in exaile now that i purged amarok ;)

---

### Post by ryanVickers on 2007-10-28
oh, Edit > Preferences > (TAB) Notification and disable it ;)

---

### Post by ubunter1 on 2007-10-29
> **ryanVickers said:**
> oh, Edit > Preferences > (TAB) Notification and disable it ;)

thanks,now is there a way to not have the player laying in the bottom tray? but to put it in the top right tray with the little icon only? along with the weather date etc? amarok did this and would like it to do the same.btw im gettin used to this player and am liking it so ill keep trying.

---

### Post by ryanVickers on 2007-10-29
funny you should ask that!  There just happens to be a plugin for exactly that! :p

To have just the icon and no window list bar in the bottom, go "Edit > Plugins" Then to the "Available Plugins" tab, and then check on "No task bar entry"  Then click "Install/Upgrade", and then go back to the "Installed Plugins" Tab, and if it's not already on, click it on! :p

---

### Post by ubunter1 on 2007-10-29
thanks!,it got it at least out of the bottom task bar tray,and there are lots of other cool plugins for it so ill stick with it,thanks for the help and if you've any more cool plug-in advice or tips,:) thanks again.rp

---

### Post by ubunter1 on 2007-10-30
now that exaile will minimise and not be in the tray, i cant close it,i have to click on the exaile icon in the panel just like im starting it,but it will not open if already playing so i need to force quit it in the system monitor and close python. any idea how to fix this one?.thanks.

---

### Post by ryanVickers on 2007-10-30
you right click that icon and click "Quit", or go "File > Quit" :p

---

### Post by ubunter1 on 2007-10-30
it wont do that as its only in the top icon bar which is the start program bar,so i need to find another way besides kill process through system monitor.heres a photo.thanks.rp.

---

### Post by ryanVickers on 2007-10-30
no, that's the launcher icon, so it won't work there ;)

You need the one in the notification area, which it looks like you removed.  This is a very important area, as it handles the sub-mode of many important apps, such as amarok, exail, the update manager, any kind of mail notifiers, etc.!  I would really recommend you put it back! :p

---

### Post by ubunter1 on 2007-10-30
> **ryanVickers said:**
> no, that's the launcher icon, so it won't work there ;)

You need the one in the notification area, which it looks like you removed.  This is a very important area, as it handles the sub-mode of many important apps, such as amarok, exail, the update manager, any kind of mail notifiers, etc.!  I would really recommend you put it back! :p

i would if i could,the only thing i removed from there was the switch users function but it took another icon with it.now deluge,amsn nicotene and the like have nowhere to go.so i dont know what to do.rp

i guess thats why i dont get updates as well.

---

### Post by ryanVickers on 2007-10-30
yeah, maybe... :p
sorry, this is just kind of funny ;)

You just need to right-click anywhere on the panel and pick "add to panel", and then pick the "notification area", but by how many noon-default launchers you have there, I should suspect you know this already ;)

---

### Post by ubunter1 on 2007-10-30
im glad its funny to you :lolflag: for me its one of the many noobish problems that could take years to solve,but thanks for the help,i learn many new things everyday here in the nix world,ill get it some time.:guitar:

---

### Post by ryanVickers on 2007-10-30
well, I don't think it will take *quite* a year or 2 to add a panel applet, but good luck on your journey through the to the Linux world! ;)

---

### Post by anonymous_x on 2007-11-03
Please help! I just installed Gusty Gibbon, I also installed Amarok and I when I try to play mp3s. I get a message, 

Amarok cannot play mp3.
Install mp3 support.

When I click yes, It takes a while and then shows  a message saying mp3 support installed.
You need to restart amarok, I close Amarok and start again, and it shows the same message. Cannot play mp3,

What else can I do?

---

### Post by ryanVickers on 2007-11-03
Yeah, I never got it to work in Gutsy - That's why I switched to Exaile ;)

It needs specifically "xine" rather than the ubuntu extras or gstreamer.  I'm guessing your on 64 bit, or else this would work!?

---

### Post by renis-pinkles on 2007-11-16
> **ryanVickers said:**
> it looks like you don't have permissions to that directory - try changing them to be all access, all the time ;)

Also, I would really recommend Exaile over any other player :p
Just my opinion ;)

hey, i only just signed up today, and i also only started using ubuntu within the last few days, and i love it! however i am having problems running amarok, just like unbunter, with the DCOP error message...no idea what it means...

you said to change the permissions to the directory, how do i do that?

---

