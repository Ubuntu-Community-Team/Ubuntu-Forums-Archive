---
title: "Opening in terminal works, menus dont?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Stew2 on 2006-05-20
Hello all, 
Just wondering if anyone has run across this. I have installed some programs (through synaptic) like frozen bubble, pysol, and lbreakout 2, etc. Synaptic installed icons for the programs in the games menu but they wont open from the menus. However they open and run fine in with the terminal :confused: . Anyone else have this happen? If so, how do you fix it? My 5 year old son likes to play the games but doesnt necessarily want to launch them from a terminal :) . I tried reinstalling the games with synaptic but the results are the same. Thank you for any help you can give me on this.
Regards,
Stew

---

### Post by S{yndrom}e on 2006-05-20
you can either make a panel short cut or a desktop shortcut. I recommend a desktop shortcut since the icon is nice and large :). First right click on the desktop and select create launcher. Type in what you want the program to be caleed (no actual effect on the program)  and a comment if you like. Now see the box named command? Click browse and manuveur through your files until you reach the game executable. Select an icon if you wish and voila!
You have your icon

---

### Post by Ecthelion on 2006-05-20
Have you tried to look at the commands that are executed when you 'click' on the icon's in the menu?
You can configure most of your menu's with 
Applications > System tools > Application's menu editor
If that doesn't work you can also just type 
```
smeg
```
in the command line
Hope you can find the error this way...

---

### Post by S{yndrom}e on 2006-05-20
Oh i see what you mean. If you have trouble actaully finding the game executable, than type this into the terminal:

find /usr/bin -name *nameofgame* or if that doesnt return anything

find /home/*yourusername*/ -name *nameofgame*

---

### Post by Stew2 on 2006-05-20
[QUOTE=S{yndrom}e]you can either make a panel short cut or a desktop shortcut. I recommend a desktop shortcut since the icon is nice and large :). First right click on the desktop and select create launcher. Type in what you want the program to be caleed (no actual effect on the program)  and a comment if you like. Now see the box named command? Click browse and manuveur through your files until you reach the game executable. Select an icon if you wish and voila!
You have your icon[/QUOTE]

Wow! :D  Quick answer! :D  Thank you, it works great. Any idea why they wont open with the icons in the menus though? Thanks again!

---

### Post by S{yndrom}e on 2006-05-20
im not quite sure about that but i think it is becuase you need to refresh the gnome panel do this by doing

sudo killall gnome-panel

Edit: i think i know what to do. you have to move the game you want to /usr/bin/games. Then refresh the gnome panel with the command above.

There are two ways to move the file.

one is sudo nautilus which uses a GUI file manager with full permissions

the other one is sudo mv */directory/where/game/is/game* */usr/bin/games/nameofgame*

---

### Post by Stew2 on 2006-05-20
[QUOTE=Ecthelion]Have you tried to look at the commands that are executed when you 'click' on the icon's in the menu?
You can configure most of your menu's with 
Applications > System tools > Application's menu editor
If that doesn't work you can also just type 
```
smeg
```
in the command line
Hope you can find the error this way...[/QUOTE]

Thanks for the reply, I just checked out the commands being executed by the icons in the menu and made sure they are the correct launch commands. They are, but they still wont launch. Yet the desktop launchers that I made from S{yndrom}e's advice work fine. Strange... I get no errors when trying to start the programs from the original menus either. They either dont respond at all or  quickly close. Anyone else had this problem?

---

### Post by Ecthelion on 2006-05-20
[QUOTE=S{yndrom}e]Oh i see what you mean. If you have trouble actaully finding the game executable, than type this into the terminal:

find /usr/bin -name *nameofgame* or if that doesnt return anything

find /home/*yourusername*/ -name *nameofgame*[/QUOTE]

That's not what I meant...
I was rather thinking that maybe the command that is run when you click on the menu icon could be wrong...

But I have to agree that it would be real strange then...
Your idea with desktop shortcuts is better.

---

### Post by S{yndrom}e on 2006-05-20
Echtelion: sorry that post wasn't ment for you it was aimed at the OP. I thought he ment he executed games through terminal becuase he couldn't find the actual executable to click. Sorry!

---

### Post by S{yndrom}e on 2006-05-20
Finaly found out how to add programs to the menu. Right click on the Applicatations tab. Select Edit Menus. Once in select the games tab and at the bottom click New Entry. Input some basic data (such as name for it, icon and the terminal command for it).

---

### Post by Stew2 on 2006-05-20
[QUOTE=S{yndrom}e]Finaly found out how to add programs to the menu. Right click on the Applicatations tab. Select Edit Menus. Once in select the games tab and at the bottom click New Entry. Input some basic data (such as name for it, icon and the terminal command for it).[/QUOTE]

Thank you for the reply. :)  The games icons are already in the games menu. I believe they were put there when synaptic installed the games, I also checked the terminal launch command line in the properties and it is the correct command. The same command that is used in the desktop launchers. Its almost like there is some kind of a broken link with the originals? I tried refreshing the panels as you suggested as well but that didnt make the originals work. I am very happy though that the desktop launchers you suggested work fine :D. Im just still trying to figure out why the originals in the menus arent working. Thanks again, I appreciate the help.

Regards,
Stew

---

### Post by Stew2 on 2006-05-20
Another strange thing. All the programs in the menus that came with the original Ubuntu install work fine, it's just the ones I add afterwards (through synaptic) that dont seem to work even though synaptic puts the icon and launcher in the menu. I ran Automatix after my ubuntu install, could it have something to do with the sources list being changed? :confused: No errors though, they just dont launch other than in terminal or with homemade launchers on the desktop. Weird huh? :) 

Regards,
Stew

---

### Post by S{yndrom}e on 2006-05-20
I think i got it. But i Need to one thing first. Do you know where the game files are located?

---

### Post by Stew2 on 2006-05-20
[QUOTE=S{yndrom}e]I think i got it. But i Need to one thing first. Do you know where the game files are located?[/QUOTE]

The game files are located at /usr/games. They are in the same folder as all the originally installed games. Hope this is the info you need :) .


Edit: I just upgraded to Dapper and everything works correctly now. I suspect reinstalling Breezy would have fixed it as well! Thanks to all who helped.
Cheers,
Stew2

---

