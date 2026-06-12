---
title: "Changing the File menu theme"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-07
Hello all
How do I change the File menu bar? I have seen a greenish metal like bar with the Aero themes for emerald, but I do not know from where to change the menu bar..
Any help would be appreciated.

---

### Post by herbster on 2008-03-07
For changing your themes you can go to System > Preferences > Appearance.

To download more themes, you can go to gnome-look.org.

---

### Post by sayakb on 2008-03-07
> **herbster said:**
> For changing your themes you can go to System > Preferences > Appearance.

To download more themes, you can go to gnome-look.org.

Thanks for the prompt reply. I've already tried that. Plus, I am using Emerald, so I cannot change my Window borders from Preferences->Appearance. Also, I do not find any option to change the File Menu Bar specifically.. :(

---

### Post by herbster on 2008-03-07
There's no means of instantly selecting a menu bar theme, because that's part of the GTK theme in use. You can edit the theme file to your liking, though:

```
gedit ~/.themes/nameoftheme/gtk-2.0/gtkrc
```

That can be tricky, though, depending on the theme.

For Emerald themes, I believe you can go to System > Preferences > Emerald (or Emerald theme manager) and you should be able to choose the theme you want for the window borders.

---

### Post by sayakb on 2008-03-07
> **herbster said:**
> There's no means of instantly selecting a menu bar theme, because that's part of the GTK theme in use. You can edit the theme file to your liking, though:

```
gedit ~/.themes/nameoftheme/gtk-2.0/gtkrc
```

That can be tricky, though, depending on the theme.

For Emerald themes, I believe you can go to System > Preferences > Emerald (or Emerald theme manager) and you should be able to choose the theme you want for the window borders.

I downloaded an Aero theme which shows 3D Green Menu bars. But I dont actually get those menu bars.
Would try the code you posted. Thank you.

---

### Post by sayakb on 2008-03-09
My ~/.Themes folder is empty. Moreover, I can't find any option to change the menubar under emerald.. :(
Can somebody help?

---

### Post by FreewareFan on 2008-03-09
Are you talking about the panel that is at the top of the screen, the one that contains the system menu and such??  Is that what you are calling the menubar?

IF so, you just right-click on it, choose Properties, and then choose the background you want to use to make it look 3D.

It that's not what you're talking about, then my mistake...   Anyway, hope this helps!

FwF

---

### Post by sayakb on 2008-03-09
> **FreewareFan said:**
> Are you talking about the panel that is at the top of the screen, the one that contains the system menu and such??  Is that what you are calling the menubar?

IF so, you just right-click on it, choose Properties, and then choose the background you want to use to make it look 3D.

It that's not what you're talking about, then my mistake...   Anyway, hope this helps!

FwF

Nope... I mean the menu bar having the File Edit View.. etc options on the Nautilus windows.

---

### Post by FreewareFan on 2008-03-09
Ah, I see.  Well, I've used Emerald for a bit now, and the only things that I know of that the themes change is the title bar of the windows, and not the actual meunbar of the program itself.  I don't really see how Emerald could go into the binary file of a program and change the way it appears.  Just the window title bar of the actual window and all the window borders are affected, as far as I know of...

Could you post a screenshot of what you are trying to obtain?  That might be a big help..

FwF

---

### Post by sayakb on 2008-03-09
Here is a screenshot:
[http://i30.tinypic.com/21lu3uq.jpg](http://i30.tinypic.com/21lu3uq.jpg)

---

### Post by FreewareFan on 2008-03-09
Hummm... Tell you what, sit tight, and I'll go get the theme, install it, and see what happens on my system.  I'll post back when I know something.

FwF

---

### Post by sayakb on 2008-03-09
Also, I remember to have seen some "See my menubars" type of topics on some public forum which I cannot find now. It showed some custom menubars for the nautilus windows.

---

### Post by sayakb on 2008-03-09
> **FreewareFan said:**
> Hummm... Tell you what, sit tight, and I'll go get the theme, install it, and see what happens on my system.  I'll post back when I know something.

FwF

Okay.. :)

---

### Post by FreewareFan on 2008-03-09
OK, got it.  What you have to do is to go and download the moomex-Theme at
[http://www.gnome-look.org/content/show.php/moomex-theme?content=57063](http://www.gnome-look.org/content/show.php/moomex-theme?content=57063)

Then you will have control over the program menu bars.    Hope this helps you!

FwF

---

### Post by sayakb on 2008-03-09
> **FreewareFan said:**
> OK, got it.  What you have to do is to go and download the moomex-Theme at
[http://www.gnome-look.org/content/show.php/moomex-theme?content=57063](http://www.gnome-look.org/content/show.php/moomex-theme?content=57063)

Then you will have control over the program menu bars.    Hope this helps you!

FwF

But I don't actually use the Moomex theme. I use a dark self made emerald theme. So if I use the Moomex GTK theme + My own colors for the Window bodies plus emerald for the window decoration, will it work?

---

### Post by FreewareFan on 2008-03-09
Just for future reference, what I said about Emerald still goes.  It does not change your program appearance.  It only changes the window borders and titlebar appearance.   

That second theme I pointed you to is actually a GTK+ theme, which CAN change the way your programs look....  

Anyways, have fun with your new look!

FwF

---

### Post by FreewareFan on 2008-03-09
I believe it will.  There's only one way to find out....  Be bold, seize the day, go forth... and all that!

Post back with your results..

FwF

---

### Post by sayakb on 2008-03-09
> **FreewareFan said:**
> I believe it will.  There's only one way to find out....  Be bold, seize the day, go forth... and all that!

Post back with your results..

FwF

Sorry, but this may sound dumb, but how do I install a GTK theme?

---

### Post by FreewareFan on 2008-03-09
Go to System - Preferences - Appearance.  When that opens up, click on the Install button, and point it to the file you downloaded...  Just like that!

Just to clear things up a bit here.   You don't even want that first theme that you pointed me to.  That's an Emerald theme, and it will not do what you want, and it will mess with the custom colors you have already made, that you said you want to keep.  

You DO want the GTK+ theme I pointed you to, and you install it the way I just said.   If it messes with your window border and title bar colors, then after you install it, just go back to Emerald and choose the theme you made, and all should be good to go...  

FwF

---

### Post by herbster on 2008-03-09
The menubar is, again, a result of the GTK theme in use. Metacity/Emerald/etc. have nothing to do with any part of the visual appearance other than the titlebar/border and in Emerald's case, a glow/shadow.

[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

That should help you to edit the theme to your heart's content. Once you get the hang of editing themes (it is not difficult, regardless of your current knowledge level-- I know folks that make their own themes, etc. but can't compile a package) you will be able to customize the look as you desire.

---

### Post by sayakb on 2008-03-10
Thanks FreewareFan
I couldn't install the theme since it wasn't showing up in the directory when I clicked install button.. I realized that the file I downloaded wasn't in tar.gz format, so I converted it to one. It seems to work now, though I don't seem to get just the Menubar themed, the ubuntu panel gets completely black in color and I don't seem to find out how to remove it. But I would keep working on it though. Thanks again.. :)

---

### Post by FreewareFan on 2008-03-10
You're welcome... 

Also, you might try to re-apply your custom Emerald theme now, to see if it will change the panel and your window border settings back to your custom colors..

FwF

---

### Post by sayakb on 2008-03-10
> **FreewareFan said:**
> You're welcome... 

Also, you might try to re-apply your custom Emerald theme now, to see if it will change the panel and your window border settings back to your custom colors..

FwF

I tried that.. but doesn't seem to help.. seems like the panel is completely under control of the GTK theme. 
I would be playing with the gtkrc file and would hopefully come out with something. :)

---

### Post by FreewareFan on 2008-03-10
Hey, if you get it to work, let me know, would you?  I'd like to run it on my system!

Thanks.

FwF

---

### Post by sayakb on 2008-03-11
> **FreewareFan said:**
> Hey, if you get it to work, let me know, would you?  I'd like to run it on my system!

Thanks.

FwF

Sure.. would work on it as soon as my exams get over.. ;)

---

