---
title: "Uninstalling a Win app from wine"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-03-09
How do you uninstall a windows app in wine. I installed one that refuses to run and would like to get rid of it. It doesn't have its own uninstall program. 
I checked this site but either missed it or it isn't there.
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by Pugwash on 2007-03-09
Can't you just delete the the relevant files in the .wine folder?

---

### Post by Patrick K on 2007-03-09
I can but that leaves junk in the registry. I suppose I could manually clean it.

---

### Post by steven8 on 2007-03-09
Using the xcfe interface, the applications menu has a wine listing, and it links to an uninstaller if it's present.

I'd go to home/.wine/c_drive/Program Files/(your program) and see if there is an uninstaller.  You could run the uninstaller using winefile.  Type winefile into the terminal, and the wine browser will come up.  Use that filepath to find an uninstaller if there is one.

---

### Post by Patrick K on 2007-03-09
Thanks for the reply. Sorry, I don't know what the xfce interface is.

There isn't an uninstaller for the program. It has an uninstall.ini file but no uninstall.exe. The readme file says to use the Add/Remove applet in Control Panel. Since there is no Control Panel in Wine...

I tried various variations on >  wine "c:\windows\uninst.exe -f "c:\Program\ Files\Accent\WNW\DeIsL1.isu"" but no luck. (The second part of the line is from the uninstall.ini file.)

---

### Post by steven8 on 2007-03-09
If you open add/remove, does it show as a removable program?

---

### Post by Patrick K on 2007-03-09
>  	If you open add/remove, does it show as a removable program?
No it doesn't. It was installed under wine, so I didn't expect it would be in Add/Remove. 

Here is the pertinent passage from the program's readme
> V.    UNINSTALLING WEBSTER'S NEW WORLD DICTIONARY AND THESAURUS

1.  Close Webster's New World Dictionary and Thesaurus.

2.  Click Start | Settings | Control Panel on the Windows 
    taskbar.

3.  Double-click Add / Remove Programs.

4.  Select WNW Dictionary & Thesaurus and click Add / Remove. 

5.  Windows displays the following message: "Are you sure
    you want to remove the selected application and all of its
    components?" 

6. Click Yes.Often Windows programs have an uninstall program that the Add / Remove applet calls. In this case it relies on the Windows uninstall program, probably InstallShield. 

I can double click on uninst.exe in wine's windows directory but it just ask if I want to uninstall the selected program. However, I haven't told it which program to uninstall and don't know what program it is referring to. So I canceled out.

---

### Post by steven8 on 2007-03-09
> **Patrick K said:**
> No it doesn't. It was installed under wine, so I didn't expect it would be in Add/Remove. 

Here is the pertinent passage from the program's readme
Often Windows programs have an uninstall program that the Add / Remove applet calls. In this case it relies on the Windows uninstall program, probably InstallShield. 

I can double click on uninst.exe in wine's windows directory but it just ask if I want to uninstall the selected program. However, I haven't told it which program to uninstall and don't know what program it is referring to. So I canceled out.

I didn't really figure it would be either, but it never hurts to ask.  I'm not sure how to interpret that uninst.exe in the wine folder either, unless it would be uninstalling wine itself?

---

### Post by Patrick K on 2007-03-09
That's why I canceled out. I didn't know what it was going to do. At this point, though, having to reinstall wine isn't a big problem. I only have a few apps installed. Looks like I'll have to delete the files and dig through the registry manually. 

Seems this is something the wine team might consider looking at. You'd think after fourteen years of development wine would be a bit farther along than it is.

---

### Post by plainjane on 2007-03-09
I'm a n00b myself, but I had to uninstall something other day in Wine.  I found it in here somewhere.  I was something easy like type uninstall in terminal???  Don't quote me on that, but try searching for just wine, cause I think that was what I was under. I remember it being pretty far back. I had to uninstall and reinstall DVDShrink and I know it had to be something very very easy for me to have tried it this early in the linux game!  Sorry, wish I was more help.  I think I need to start writing this stuff down, so much to learn!
                  plainjane

---

### Post by plainjane on 2007-03-09
[http://www.ubuntuforums.org/showthread.php?t=352097&highlight=uninstall+wine+program](http://www.ubuntuforums.org/showthread.php?t=352097&highlight=uninstall+wine+program)

Found it!  Hope link works.
              plainjane

---

### Post by Patrick K on 2007-03-09
Great, that did the trick. Thanks. Good to know that wine has a workable uninstaller.

---

### Post by steven8 on 2007-03-09
Just checking back and saw this solution.  Very nice!!  Did it allow you to just pick the program you wished to uninstall?

---

### Post by Patrick K on 2007-03-09
It sure did. It puts up a window with all the installed apps. Just pick the one you want to dump and it's gone.
BTW, thanks for your help.

---

### Post by SirPecanGum on 2007-03-21
Thanks plainjane!

---

### Post by plainjane on 2007-03-21
Your welcome!  I ask so so so many questions here it is nice to know the answer to one!

---

