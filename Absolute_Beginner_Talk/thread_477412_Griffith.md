---
title: "Griffith"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-06-18
I have Griffith installed which works very well.

However, whenever I double click an .exe file (with a view to running Wine), Griffith automatically launches.  Any idea how to change this?

---

### Post by dilidon on 2007-07-29
Got it sorted yet? I would suggest you unbind the .exe files from Griffith by assigning them to Wine - right click on the .exe file, select properties, and then "open with" or "open using program" (or smth similar - I am using a localized version of Gnome so I don't know the exact english name for the tab there). There you can select the program you want to associate with that specific type of file. Hope that helps.

---

### Post by expatCM on 2007-07-29
Not sorted .....   

Yes, I have wondered about / tried using Open With for all .exe files but it is not quite as straight forward .....   What I have found is that using Open With seems to work with the individual file when you get the Griffith program opening but it does not make a global setting that all .exe files are Open With wine.  So Griffith keeps appearing.

Since Griffith is the only program to do this I posted on the Griffith forum to ask.  The response back was to the effect that this was an Ubuntu problem and not a Griffith problem :)

---

### Post by dilidon on 2007-07-30
Yeah, it's definitely a desktop setting issue. Are you using KDE or Gnome?
My suggestion should work if you are using Gnome (I can look up the proper English translations if you can't match my approximations). In case you are using KDE, the method is slightly different, although very similar, but should still yield the desired result. Let me know which one u use.
In short - in Gnome you should use  the right click menu and then choose Properties and work it out from there (you can also add applications in case the necessary ones are not visible), in KDE you do the right click but use "open with" and have KDE (or Konqueror, to be correct) remember the new choice by ticking the check box at the bottom of the window.

---

### Post by expatCM on 2007-07-31
Reading your comments makes me think it is something I am doing or not doing.  Let me explain what I do and perhaps you will have some idea ......

I use Gnome.

My first step is to find a .exe.  If I double click then Griffith will open.

If I right click and then select "Open with" a small window opens where I enter the name of the application, Wine in this case.  Click and the Windows installer then runs.

However, this only applies to this single event.  If I click the same .exe again or any other .exe then Griffith will appear......  there is no change to the default file association / Open with.

What puzzles me is that it is Griffith and only Griffith that appears, why not some other application.  I have tested on other machines and the behavior is consistent.

---

### Post by wormser on 2007-07-31
You need to right click and go to **properties** then the opens with tab.  Then selet wine.

---

### Post by expatCM on 2007-07-31
ah ...  now ...  I did not have the same thing as you...  until I closed gnome-commander and used nautilus instead.  Only then did I get the properties which are needed .....

So this one is now solved, thank you for your help :)

---

