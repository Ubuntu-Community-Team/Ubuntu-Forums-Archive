---
title: "[SOLVED] Need help"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by bokz on 2007-11-05
First off hello everyone. :D Well I'm basically a total noob to ubuntu and not the best at windows either but anyway on to my problem, I am using ubuntu version 7.04 the second newest i believe. As i was updating (i believe this is when it happened) my menu's on the top and bottom started to flicker and then disapeared leaving me with no option but right clicking on my desktop witch i don't think will fix it. I know this is probably a really stupid question but can somone please help me on how to get this back. thanks you very much :).

---

### Post by Sef on 2007-11-05
This is your problem that you are looking for a solution to -

Your top and bottom toolbars have disappeared and you you would like to know how to have them again.

Question:

What were you updating: A few programs or to the latest operating system (Gutsy Gibbon, 07.10)?

> I know this is probably a really stupid question but can somone please help me on how to get this back. thanks you very much .


No it is not a stupid question.   If you don't ask you will not learn.

---

### Post by hyper_ch on 2007-11-05
> **bokz said:**
> not the best at windows either

Don't worry, that's an advantage because you are not a Windoze Power User and hence you are not inclined that all things must be done the same as on Windoze. It's difficult to change habits and Windoze Power Users have their minds set to a certain way of how things should work ;)

As for your problems, I refer to the previous poster. Without more data it's not easy to give any advice.

Btw, which version are you using? Ubuntu (Gnome), Kubuntu (KDE) or Xubuntu (Xfce)?

---

### Post by bokz on 2007-11-05
> What were you updating: A few programs or to the latest operating system (Gutsy Gibbon, 07.10)?

I'm not 100% sure what it all was...It was some 120 things? it took around 10 mins and im pretty sure it wasnt Gutsy Gibbon, 07.10.  I didn't travel to far into anything from my toolbars(they were like automatic updates). if that makes any sense
Ubuntu 7.04 (Feisty Fawn) is the version

---

### Post by hyper_ch on 2007-11-05
Actually an upgrade to 7.10 will take a bit longer... you'll have to download about 700 MB of new files, more than 120 packages should be upgraded and I'm sure it'll definitively take longer than 10min to complete all of that.

---

### Post by bokz on 2007-11-05
to be honest though im sure the updating had nothing to do with any of it. My friend installed this program for me yesterday and it did the same thing(he was just browsing the internet, not updating), he looked up the problem on his lap top.  It didn't work and his solution was to reinstall. I don't mind having to reinstall but i don't want this problem to occur again if I do. Like I said before the toolbars started to flicker and then just disappeared.
I'm acessing the internet and my msn only now but alt+tabing, these were the programs i had opened when my tool bars disappeared.

---

### Post by 3rdalbum on 2007-11-05
Try pressing Alt-F2.

If a box opens where you can type a command, type "gnome-panel" and hit Run.

If you get the flickering again, do the Alt-F2 again and type "xterm" and hit Run.

Then, in the terminal, type "gnome-panel" again and tell us if any error messages appear in the terminal window.

---

### Post by bokz on 2007-11-05
Nothing happens when i press alt+f2

---

### Post by JBAlaska on 2007-11-05
Right click on your desktop and select Open Terminal , Type:
```
gnome-panel
```

Post the output if a panel does not start.

---

### Post by bokz on 2007-11-05
i have no option to open a terminal( infact ive been wondering what that is for a while now, and how to open it)
The only options i have when i right click my desktop are:
Create folder
Create launcher
Create Document
-----------------
Clean up by name
Keep aligned
-----------------
Paste
-----------------
Change desktop background

is the terminal somthing to do with create launcher?

---

### Post by bokz on 2007-11-05
I've been reading though previous posts and the closest i could find was " i lost my top and bottom toll bars. his alt+f2 did not work either and he acually had a terminal already open--

> It was THE MILLION DOLLAR ANSWER: "Gnome-panel &." Thanks a million. Now, I need to search out a new sources.list mine is so screwed I may as well see if I can find a decent one. Bye-the-by, I would really have been in trouble as Alt + F2 did not work and luckily, I had pulled out a shortcut to a terminal. Then again as my proficency with this OS grows, I could probably have done just as well at the standard DOS line.

I've said it already but ill say it again im a total noob with ubuntu and not to bright with comps in general, but could someone also tell me what a shortcut to a terminal is also. I'm sure ill have to end up re-installing but ill plan to have a terminal open the first day just incase.
Thanks alot for all the help so far.

---

### Post by markharding557 on 2007-11-05
ok you need to make a shortcut on the desktop for the terminal 
right click on the desktop,select create launcher
you now should have create luancher box
next  select browse and choose file system in the places menu
navigate to usr/bin,this is where the executables are,and select gnome-terminal
type terminal in name click ok you should  now see a terminal icon

open the terminal and put gnome-panel and hopefully your bars will reapear.

---

### Post by bokz on 2007-11-05
Ahh I see, I did it and the toolbars come on, only problem is they only flicker for 30 secs then disapear again :(.

I think this will help? maybe?

> bokz@bokz-desktop:~$ gnome-panel
Failed to load gnome-fs-desktop: Failed to load image '/usr/share/icons/gnome/16x16/places/gnome-fs-desktop.png': Image has zero width
Failed to load gnome-fs-desktop: Failed to load image '/usr/share/icons/gnome/16x16/places/gnome-fs-desktop.png': Image has zero width
Failed to load gnome-fs-desktop: Failed to load image '/usr/share/icons/gnome/16x16/places/gnome-fs-desktop.png': Image has zero width

(gnome-panel:7753): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -11 and height 24

Gtk-ERROR **: file gtkrecentmanager.c: line 2031 (get_icon_fallback): assertion failed: (retval != NULL)
aborting...
Aborted (core dumped)
bokz@bokz-desktop:~$ 




Thanks

---

### Post by bokz on 2007-11-05
Don't give up on me!!!!! :lolflag:

---

### Post by jimrz on 2007-11-05
> **bokz said:**
> i have no option to open a terminal( infact ive been wondering what that is for a while now, and how to open it)
The only options i have when i right click my desktop are:
Create folder
Create launcher
Create Document
-----------------
Clean up by name
Keep aligned
-----------------
Paste
-----------------
Change desktop background

is the terminal somthing to do with create launcher?

Try control+alt+backspace (should re-start gnome) and see if that takes you back your login screen. Then login and see if it will come back up normally. If that does not work, try control+alt+F1 which should take you to a cli login prompt, login with your regular user name/passwor the type
```
sudo shutdown -P now
```
hit enter, enter your password and hit enter. This will shut down and power off the box. Then try restarting again to see if that helps.

---

### Post by bokz on 2007-11-06
> Try control+alt+backspace (should re-start gnome) and see if that takes you back your login screen. Then login and see if it will come back up normally

The same thing happens when I normally restart it, it started to flicker then disapeared

> If that does not work, try control+alt+F1 which should take you to a cli login prompt, login with your regular user name/passwor the type
Code:

sudo shutdown -P now

hit enter, enter your password and hit enter. This will shut down and power off the box. Then try restarting again to see if that helps.

This time it was different it started up for about 10 seconds with the tool bars on then they disappeared without any flickering. About 30 seconds after they appeared again and then started flickering as usual. :S I think ill try step 2 over.

thanks

I tried step 2 over and am sure i did it exactly like you said, same thing happened.

thanks

---

### Post by jimrz on 2007-11-06
> **bokz said:**
> The same thing happens when I normally restart it, it started to flicker then disapeared



This time it was different it started up for about 10 seconds with the tool bars on then they disappeared without any flickering. About 30 seconds after they appeared again and then started flickering as usual. :S I think ill try step 2 over.

thanks

I tried step 2 over and am sure i did it exactly like you said, same thing happened.

thanks

Sorry, can't think of anything else that might be a quick and simple fix. Since that is a relatively fresh install, maybe re-installing would be best. If you made a separate "/home" partition you could likely retain that and just replace "/", as that is probably where the problem lies, on a new install.

---

### Post by markharding557 on 2007-11-06
> **bokz said:**
> Ahh I see, I did it and the toolbars come on, only problem is they only flicker for 30 secs then disapear again :(.

I think this will help? maybe?





Thanks

the next thing to try is creating a new user so you can see if the problem happens with different user
so go to system menu,users and groups here you can add a new user.
when done log in as new user and see what happens.
i hadn't given up on you,we are just in different time zones:)

---

### Post by bokz on 2007-11-06
> the next thing to try is creating a new user so you can see if the problem happens with different user
so go to system menu,users and groups here you can add a new user.
when done log in as new user and see what happens.

I don't think I can access system menu, users and groups without my tool bars lol.
I'll probably end up just re installing it tonight and see what happens on from there.
> i hadn't given up on you,we are just in different time zones

I know, everyones been such a great help :) I just didnt want my topic on page 50, so I uh refreshed it 8)

---

### Post by markharding557 on 2007-11-07
many apologys forgot about your menus 
load the terminal and enter"gksu users-admin and your're go

---

### Post by bokz on 2007-11-07
YOU ARE MY SAVIOUR :biggrin:

the new account has the toolbars :D:D:D:D 
Thank you so much to everyone, not only is my problem fixed but U learned how to open a terminal. Lol (which will come in handy :P) 
Anyway im uber happy now so thank you very much again.
If the problem happens again I'll be looking in things I've done to make it happen so I could give more info next time.
Thanks again \\:D/

---

### Post by Maestro23 on 2007-11-07
> **bokz said:**
> YOU ARE MY SAVIOUR :biggrin:

the new account has the toolbars :D:D:D:D 
Thank you so much to everyone, not only is my problem fixed but U learned how to open a terminal. Lol (which will come in handy :P) 
Anyway im uber happy now so thank you very much again.
If the problem happens again I'll be looking in things I've done to make it happen so I could give more info next time.
Thanks again \\:D/

Good deal man.  Please mark this SOLVED using the Thread Tools.

Thanks.:guitar:

---

### Post by bokz on 2007-11-07
I guess its not really solved though seeing how it did it again O_O (I didn't even touch the screen, I left it for 2 hours.) I came back and they were gone.

---

### Post by tjutberg on 2008-03-24
was this ever solved? cause i got the same problem now.
the panels flicker for 30 seconds and then disappears. 
if i start it again from a terminal the same happens again.
im using gutsy, compiz-fusion on an amd 64.

anyone solved this?

---

