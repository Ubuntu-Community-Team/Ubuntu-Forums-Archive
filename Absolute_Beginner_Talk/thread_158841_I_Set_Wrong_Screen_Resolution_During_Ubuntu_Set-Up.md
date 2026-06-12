---
title: "I Set Wrong Screen Resolution During Ubuntu Set-Up"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-04-11
When I installed Ubuntu one of the few questions I had to answer was my screen resolution.  I have an 19" LCD monitor with a DVI input.  I you erroneously set it at 1040 x 768, which is supported by my monitor and looks quite good in Ubuntu.  Indeed, while on this subject, Ubuntu's graphics and text appear excellent -- at least as good as Microsoft Clear Type, maybe better, because I think things are a little larger.  In any event, is there any way to correct this so that I have the option of displaying Ubuntu in my monitor's native resolution of 1280 x 1040?  If I did that, would everything get real teeny tiny like what happens in Windows when you increase the screen resolution? I did do a search in this forum for screen resolution but nothing on point came up.  There was a way to start an Ubuntu "wizard" to reset screen resolution settings, but when I came to a dialog asking how much memory to allocate to system memory for my presumably onboard video chip I canceled out not wishing to end up with no video at all.

Okay, sorry for the long post for a simple question.  Any suggestions?  Thanks very much in advance.  I hope someday to have sufficient expertise to answer some of the more simple questions posted here myself.

-- Gene

---

### Post by IYY on 2006-04-11
There is a resolution changing program: System > Preferences > Screen resolution. If your desired res is listed there, you can just select it. Try that. If it's not in the list, you'll need to reconfigure Xorg.

And yes, everything will become smaller. You can change increase the font sizes, though, so it's ok.

---

### Post by esteban2x on 2006-04-11
How do you reconfigure to change the res?  I just loaded Ubuntu and my screen is so small it's very annoying. I think it's 640 480 with a screen that is only about 4 inches by 6 inches. the res is good but the screen is really small. I'm using a gateway laptop. I"m VERY new at this. I tried to change it one time using a command someone suggested but I ended up choosing the wrong one and had to totally reload Ubuntu to get it back.

---

### Post by Mustard on 2006-04-11
HowToReconfigureXorgCreated Saturday 01/04/2006 10:47

Try this...

ctrl + alt + f1 to get to a terminal (remember that you can use ctrl + alt + f7 to get back to desktop). Login with username and user password to get a command prompt

```
sudo /etc/init.d/gdm stop
#shutdown gnome desktop manager
```

```
sudo dpkg-reconfigure xserver-xorg
#reconfigure xorg.conf
```

The above command starts a dialog.  Choose the default answers for whatever things you don't know the answers to.  When you get to the screen resolutions dialog, add the screen resolutions you want by pressing the **space bar** when the cursor is on the selection you want.  When you finish answering all the questions it will make a backup of your old xorg.conf and name it according to the date and time it was made.  It will then write a new copy of your xorg.conf according to the choices you made in the configuration dialog.

Then do this..

```
startx
#restart the Xserver
```

if startx doesnt work try this..

```
sudo /etc/init.d/gdm restart
#restarts the gnome-desktop-manager
```

Check to see if your new resolution settings are working.

If you still have issues visit this thread...

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by da5id on 2006-04-11
[QUOTE=IYY]There is a resolution changing program: System > Preferences > Screen resolution. If your desired res is listed there, you can just select it. Try that. If it's not in the list, you'll need to reconfigure Xorg.

And yes, everything will become smaller. You can change increase the font sizes, though, so it's ok.[/QUOTE]

No, it's not in Pref because I set max rez wrong during install.  If I knew how to reconfigure Xorg, whatever that is, I would not have posted here in the ABSOLUTE BEGINNERS forum.  Do you remember when you were one?;)

---

### Post by halitech on 2006-04-11
da5id, check out the info from Mustard. I had the same problem with a test box at work and I ran through the same procedure and it allowed me to change it higher.

---

### Post by da5id on 2006-04-12
Mustard, way cool -- worked.  8/10 -- 2 points deducted for omitting to mention the noob you were going drop his *** to a black screen command prompt and s/he should first print instructions. :-)  Thx much, Gene

PS Well, technically you did, but I entered (ok, cut 'n paste) your first command to the fancy "Terminal" in Accessories, then I went to dreaded black screen.  At least now I know what my tutorial means about white on black.

---

### Post by Mustard on 2006-04-12
[QUOTE=da5id]Mustard, way cool -- worked.  8/10 -- 2 points deducted for omitting to mention the noob you were going drop his *** to a black screen command prompt and s/he should first print instructions. :-)  Thx much, Gene

PS Well, technically you did, but I entered (ok, cut 'n paste) your first command to the fancy "Terminal" in Accessories, then I went to dreaded black screen.  At least now I know what my tutorial means about white on black.[/QUOTE]

Your constructive feedback has been noted and will be acted upon. ;)

I'm glad you managed to have some success with the reconfiguration.

---

### Post by steve.horsley on 2006-04-12
In Gnome, you can set the font size after setting the resolution from the menu:
System->Preferences->Font, click Details and you can change the dots-per-inch to match your monitor. You may have to restart X afterwards by pressing Alt-Ctrl-Backspace.

---

