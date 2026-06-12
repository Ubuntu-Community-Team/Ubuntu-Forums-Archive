---
title: "A Host of Problems..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-21
I've been having a host of problems lately but I have resolved most of them except four:
-1)sorta a silly one but...how do you get the add applications button under "Applications" if it's not there anymore. (I like to use both this one and synaptic depending on the situation)
-2)How come when I open mplayer it says "New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)."
-3)How come firefox won't startup??? I tried creating another username and it actually opened up in that new username... but in my username it won't open...and yes I have already tried uninstalling/reinstalling it in synaptic
-4)When I open up aegis virus scanner, it says "A new version of File: :Scan is available.  Do you want to update?" And when I click yes it take me to a terminal, prompts me for my password, I type it in, and then it says "Update complete. Please restart Aegis."  The thing is that when I close and open it again the whole update thing happens again!
Please help me and thanks in advance.

---

### Post by user1397 on 2006-03-21
I forgot to mention that if there are any threads that contain info about these issues please post them here.
Thanks.

---

### Post by user1397 on 2006-03-21
Hmm I also forgot to mention a fifth problem...
-5)That when I try to use the sound recorder, it doesn't record (I have tried it with 2 different microphones).

---

### Post by supergrapeman on 2006-03-21
[QUOTE=erik1397]Hmm I also forgot to mention a fifth problem...
-5)That when I try to use the sound recorder, it doesn't record (I have tried it with 2 different microphones).[/QUOTE]

Is this the Breezy release? I had the same issue, until I tried recording with a different app (Audacity). This worked fine. Then I tried Skype, that worked fine, too. Give them a go, see if you get any further.

---

### Post by user1397 on 2006-03-21
That's the weird thing, audacity and skype both did not work either!

---

### Post by user1397 on 2006-03-21
Will anyone help me???!!!:confused:

---

### Post by Sandlst on 2006-03-21
For the re-adding of Add/Remove applications, have you tried right clicked on "Applications" selected edit menus, and checked the relevant box?
As for Firefox, I would try to remove the config file-to do this go to (places/home) click "View" and click on "Show Hidden Files" delete the .mozilla folder, then try running/reinstalling firefox.
Not sure what to do about the Mplayer problem, sorry.  Hope this Helps!

*EDIT* my subfont.ttf is located in /usr/share/mplayer, but yours is looking in ~/.mplayer....so (if its in the same place as mine) try to run```
mkdir .mplayer
```
then```
sudo cp /usr/share/mplayer/subfont.ttf ~/.mplayer/subfont.ttf
```  If this doesnt work, try searching for the file subfont.ttf under (Places/Search for Files)  You will probobly have to change the "look in folder" option to File System.  Also, for the virus scanner, have you tried updating it as root?  It may need root privilages.....

---

### Post by user1397 on 2006-03-21
[QUOTE=Sandlst]For the re-adding of Add/Remove applications, have you tried right clicked on "Applications" selected edit menus, and checked the relevant box?
As for Firefox, I would try to remove the config file-to do this go to (places/home) click "View" and click on "Show Hidden Files" delete the .mozilla folder, then try running/reinstalling firefox.
Not sure what to do about the Mplayer problem, sorry.  Hope this Helps!

*EDIT* my subfont.ttf is located in /usr/share/mplayer, but yours is looking in ~/.mplayer....so (if its in the same place as mine) try to run```
mkdir .mplayer
```
then```
sudo cp /usr/share/mplayer/subfont.ttf ~/.mplayer/subfont.ttf
```  If this doesnt work, try searching for the file subfont.ttf under (Places/Search for Files)  You will probobly have to change the "look in folder" option to File System.  Also, for the virus scanner, have you tried updating it as root?  It may need root privilages.....[/QUOTE]
Thanks for the reply.  Your mozilla suggestion worked, but for the add apps thingie, it is simply not there in that menu!

---

### Post by Sandlst on 2006-03-21
In the 'edit menu' screen, do you have a button for "Defaults" next to "Close"?  Im afraid the problem may be that Im on dapper......have you tried also going to (Applications/System Tools/Application Menu Editor)?  Scroll down the list of apps on the left side, add/remove programs should be the last one.  If its not there, click "New Entry" call it "Add/Remove Programs" under name, command=/usr/bin/gnome-app-install
Icon=/usr/share/pixmaps/gdebi.png
Hope this works for you!

---

### Post by user1397 on 2006-03-21
Thank you again for the replies, but some things still don't work.  Somehow I'm pretty sure that the add apps files got deleted because I can't find the pic and when i put in the command, it won't open.  I have to download it i think but i don't know how.  As for the mplayer thing, my subfont.ttf file is not under usr/share/mplayer!
my search did't provide any results!

---

### Post by Sandlst on 2006-03-21
Doing some searching on google I found this page:[http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_Multimedia]("http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_Multimedia")
It tells you to fix the problem, try this command:```
sudo ln -s /usr/share/fonts/truetype/freefont/FreeSans?.ttf ~/.mplayer/subfont.ttf
```  

To reinstall gnome-app-install, do ```
sudo apt-get install gnome-app-install
```
Hope this helps!

---

### Post by user1397 on 2006-03-21
Okay fixed the add apps problem, but still got the mplayer problem.:(

---

### Post by Sandlst on 2006-03-21
I assume you have already tried reinstalling mplayer...have you tried also deleting the .mplayer folder in home, then reinstalling?

---

### Post by user1397 on 2006-03-21
Okay thank you so far.
Problem number four is the only remaining one.  So whats the code to update it as root?

---

### Post by Sandlst on 2006-03-21
I unfortuatly do not have Aegis installed, but I would guess that you are accessing it through the menu?  If this is the case, right click on the menu item and select "add to desktop".  Once it is on your desktop, right click the desktop icon, select "Properties" go to the "Launcher" tab, highlight the Command entry, right click and copy, open a terminal (without closing the properties window) type ```
sudo
``` Then paste the command after it.  Be sure there is a space between sudo and the command.  This will run it as root, which I hope will work.  Good Luck!

---

### Post by user1397 on 2006-03-21
[QUOTE=Sandlst]I unfortuatly do not have Aegis installed, but I would guess that you are accessing it through the menu?  If this is the case, right click on the menu item and select "add to desktop".  Once it is on your desktop, right click the desktop icon, select "Properties" go to the "Launcher" tab, highlight the Command entry, right click and copy, open a terminal (without closing the properties window) type ```
sudo
``` Then paste the command after it.  Be sure there is a space between sudo and the command.  This will run it as root, which I hope will work.  Good Luck![/QUOTE]
Thank you so much for helping me out so much! That worked.

---

### Post by user1397 on 2006-03-21
I'm sorry this list keeps on getting bigger, but there are 2 new problems that I have encountered:) 
1)  I can't get skype to work with my microphone (or headest/mic)
and
2)  I can't work the sound recorder with my devices (I have tried with audacity-no luck with that)

---

### Post by Sandlst on 2006-03-22
Do the programs appear to be working, just no sound is recorded?

---

