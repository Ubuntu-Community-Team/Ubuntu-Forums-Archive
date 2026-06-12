---
title: "Wine and such"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-01-19
I've got a few problems conserning wine.
1. Whenever I run something with wine i get the following message:

     Warning: the specified System directory L"c:\\windows\\system32" is  
     not accessible.

The wierd thing is that everything seems to run okey, well at least some of the applications. I tried to investigate the matter by my self and found that the \system32\ catalogue contains no files, I'm thinking that could be the problem. Does it sound reasonable? If so, what files does I have to get, to get rid of the message?

2. I'm also a big fan of Starcraft, and I'm been working hard to get it working with wine. Well, it now works... sort of. It goes very slow! It's totaly unplayable. Since I only got a PIII 700 MHz I've heard that it might be impossible to run anything with wine in normal speed. Is it true? or do I still got a chance? Then how? I have some clues to what can be the problem, maybe. When I start starcraft I get some error messages:

     Xlib: extension " GLX " missing on display " : 0 . 0".
     fixme : ddraw : Main_DirectDraw_SetCooperativeLevel (0x7fdf8e90) -          
     > (0x 10022,00000013) fixme : xrandr : 
    X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 
    to 8
    fixme : xrandr : X11DRV_XRandR_SetCurrentMode Cannot change 
    screen BPP from 32 to 8
    fixme : x11drv : X11DRV_DDHAL_CreatePalette stub
    fixme : wave : DSD_CreateSecondaryBuffer (0 x 7fdfa620,0 x  
    7fb1fcc4,c2,0,0 x 7fe2e40c,0 x 7fe2e51c,0 x 7fe2e3e : stub
    fixme : wave : DSD_CreateSecondaryBuffer 
    (0x7fdfa620,0x7fb1fc9c,80,0,0x7fe4ed34,0x7fe2e2d4, 0x7fe4ed10 ) : 
    stub
    ...
   fixme : wave : DSD_CreateSecondaryBuffer 
   (0x7fdfa620,0x7fb1fbb8,c2,0,0x7fe8fce4,0x7b90abac, 0x7fe8fcc0) :  
   stub

Can anyone help me to fix these problems?

I dont know if I am suppose to post this here or in the Ubuntu Gaiming forum. But I'm realy new to linux so this feels just right.

---

### Post by Iesos on 2006-01-20
Thats right, I have some more troubles.
After a few weeks I got tierd of using Gnome so I changed to KDE some 36 hours later I got tierd on that too. Now I'm on WindowMaker (some say that no genuine beginner uses WM, but I do) and have some questions:
1. Is there a way too lock my session when leaving the computer? There is a option in the Applications menu => Commands => Lock. Is this for locking your session? If so, too bad, because it gives an error message: 
     Could not execute command: exec xlock -allowroot -usefirst
I don't get it.
I guess I'll be posting more of my problems in a few hours/days time.
/Thanks in advance.

---

### Post by Iesos on 2006-01-20
Oh, now I got my next question. Still regarding WM. How can I add new items to the applications menu. The standard tool, The "Windowmaker preference" says the current file isn't supported by that tool, so I need to know which file I should edit.
An other question: Where can I add commands to run with the start of WM?

---

### Post by Iesos on 2006-01-20
And if there where a way, I would like to changes the name of this thread to "Wine and WindowMaker"

---

### Post by jon_z on 2006-01-20
for your errors with wine, have you setup your video cards yet? it looks like thats what the error is complaining about.  check out the hardware forum and goto video and sound, there are excellent tutorials for ATI and nvidia based cards if you have those.  With wine, I have a AMD Athlon 3200 64 bit, 1 gig ddr440 ram, and a 10k RPM Raptor hard disk. I tried installing Age of Empires 3 which would be a simple task on windows, but it took foooooorreeevvveeerr on ubuntu, so i gave up and just booted up to windows for the game.  If you are just starting to switch over, dont delete your windows partition just yet, if you have dont fret.  A lot of expierenced linux users have a windows partition if they are into serious gaming.  Starcraft is a little taxing for wine in my opinion..  Something to look into if wine is giving you problems is VMware, i have no expierence on it, but if you have deleted windows, it may be something to look into you, best of luck.  *EDIT* for windows maker, i personally do not use that, so i dont know what to tell you about locking the session.  if you cant get it to work, may i suggest unplugging the mouse and hiding it when you leave ;)   Best of luck..

---

### Post by Iesos on 2006-01-20
Good guess, I did have troubles with my graphics. But I have just fixed it, and dispite that, starcraft still is slow and prints the same sort of errors.
Thanks for the mouse-thing, I'll do that in lack of any other options :)

---

### Post by wrtrdood on 2006-01-20
[QUOTE=Iesos]
1. Is there a way too lock my session when leaving the computer? There is a option in the Applications menu => Commands => Lock. Is this for locking your session? If so, too bad, because it gives an error message: 
     Could not execute command: exec xlock -allowroot -usefirst
/Thanks in advance.[/QUOTE]

Probably because xlock is not installed.  It or xscreensaver must be installed to be able to lock the display.  WindowMaker is not like KDE or Gnome in that there are a lot of GUI tools to let you configure things.  If you really want to get it set up (and it truly is a very good manager) you have a learning curve ahead of you.  The config files mostly have to be edited via a text editor and you need to know what you're doing.  Check [http://www.windowmaker.org](http://www.windowmaker.org) for more information.

BTW - if you install xscreensaver you can manually work this by first running it:  xscreensaver -nosplash
then locking with: xscreensaver-command -lock

---

### Post by Iesos on 2006-01-20
I think I have made progress, I haven't solved a single problem, but still progress.

On the lock-session thing, thanks a lot wrtrdood! Now I can lock my session, but not in a acceptible way. When I run xscreensaver -nosplash, the terminal becomes unusable and nothings happens. When I run xscreensaver-command -lock it says:

xscreensaver-command: no screensaver is running on display :0.0

I can lock it though, by $ xscreensaver, and then choose to run the screensaver.
And an other wierd thing is that it I don't uses the computer for 20 min or so, the screen turns black/uses a screensaver. But, when I look in the xscreensaver there I have chosen that the screensaver shouldn't start in 720 minuter whitch is a bit longer. I dont get it. It almost seems as xscreensaver doesn't have anything with the screensaver in WM.

And thanks again, this time for the link. I found it my self earlier, but it didn't help. I started reading the documentations pages aboute the applications menu/root menu. But nothing adds up. It seems to be easy, the thing is that you should edit your WMRootMenu file in /GNUstep/Defaults
Well thats seems easy, to a start. But when I open the file all it contains is "menu.hook". Thats not what it is supose to contain according to WM's website.
How do I seach for files in the terminal? And where should I look?
I found some guy somewhere on the internet that seem to have the same problem. Well, mine are even worse. His solution was that he had the menu.hook in /etc/X11/WindowMaker, so I took a peak at that location. And I dont have a file like that there. I do got the files: menu.posthook and menu.prehook whitch both contains absolutly nothing. So... deadend.

On the WM.org website they are talking about a "Meta key", what key is that? Seems as I dont got it on my keyboard. They are also saying that you are suppose to have a "dock menu", I wonder if that's the menu thats shows then you rightclick one of the items in the dock. Becouse then there is something wrong with my "dock menu". According to WM.org it is suppose to have a "settings" option, but mine only has hide and kill an other stuff that don't help me. I'm intrested in this settings button because according to WM.org it gives a start-with-windowmaker-option that I realy would like to use on some applications.

I hope some realy leet WM user finds this. *sigh*
Well, thanks this far. Good night.

---

### Post by Iesos on 2006-01-21
Okey, you where all too slow, I fixed it myself. At least the applications-menu thing. For everyone with the same problem:
go to: /usr/share/WindowMaker
There you will find a file named "menu". Edit it all you want, just follow the syntax used for all the other options in the menu. To edit:
$ sudo nano menu 
I recomend to make a backup befor editing, for example:
$ sudo cp menu menu.backup
There are also a file named "autostart", I will now try changing in it and see what happens :).

---

### Post by seajob on 2006-01-23
The xlock problem: i begin Xscreensaver the old way. My /etc/X11/Xsession.d/98xscreensaver:

XSCREENSAVER=/usr/bin/xscreensaver
if [ -x $XSCREENSAVER ]; then
        $XSCREENSAVER &
fi

and now Xscreensaver begins everytime a new X session begins.

The menu problem: I really love the default approach in debian and ubuntu; every installed app apears magically in the menu. For the most used apps, instead of changing the menu I use wmdrawer. Try it.

Excuse my english...

Aaaaaaagur.

---

### Post by Iesos on 2006-01-23
I think I've got the most problems figured out by now.

Screensaver:
The command
 $ xscreensaver-command -activate
Works for me (except for once when my xscreensaver-deamon (or something) where killed).

I've figured out the settings-when-right-clicking-a-dockapp-thingy too, one has to put the dockapps beneath the wm-preference button (the one with the screwdriver).

Now Iam more interested in those wine problems.

Thanks for the help this far!

---

