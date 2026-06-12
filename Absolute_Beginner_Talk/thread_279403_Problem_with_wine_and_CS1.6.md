---
title: "Problem with wine and CS1.6"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-10-17
Im istalling half life GOTY and before I start it says that my system cant play suppor wav files.?!?! Anyone konw of this? Help? PLEZE?:-D

---

### Post by aktiwers on 2006-10-17
Try going to 
winecfg

in terminal and pick the audio tab. Then pick OSS drivers.
does that work?

---

### Post by Hmarroqu on 2006-10-17
that was already checked,so i checked all of the choice. ill update on what happens next.:rolleyes:

---

### Post by aktiwers on 2006-10-17
If you didnt check it earlyer, wine will proberbly do it automaticly the first time you enter the Audio Tab. It for me. Well.. yeah give os an update on how it worked. :)

---

### Post by Hmarroqu on 2006-10-17
Eff it...:mad:  Steam doesnt work either...it updates and just stops at around 26%...ive tried this to many times. i think i might just dual boot so i can play my beloved CS on craposoft windows8)

Actually, ill follow ur link, i might to VISTA

---

### Post by Hmarroqu on 2006-10-17
Also, how would i go about removing all the files that Wine put on my HD (HL GOTYE files)

---

### Post by aktiwers on 2006-10-17
Have you tried this..  should fix the hanging on 26%.
> wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14Remeber the path to steam should be the same as yours.

EDIT:
Uh.. almost forgot I had that in my sig. Its a little outdated that howto, but I link to another howto in there, that shows how to install WinXP. But you cant run 3D games in Vmware :(

All the files Wine installed, is in your Home folder. If you press Ctrl+h it will show hidden files. Then there is a folder called .wine . In there it all is.

---

### Post by Hmarroqu on 2006-10-17
> **aktiwers said:**
> Have you tried this..  should fix the hanging on 26%.

Remeber the path to steam should be the same as yours.

I did that and got "module not found":confused:

---

### Post by aktiwers on 2006-10-17
Okey.. look above I edited my post.
Here is the guide I used to get Cs and steam up running.
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

It should work for you too! :)

---

### Post by Hmarroqu on 2006-10-17
> **aktiwers said:**
> 

All the files Wine installed, is in your Home folder. If you press Ctrl+h it will show hidden files. Then there is a folder called .wine . In there it all is.
  

LOL! you anwered my question before i posted it..hahah 

a little unrelated but i was gona ask how to add a .dll file cause i need it for NERO8)

---

### Post by aktiwers on 2006-10-17
Just find where Nero is installed, and copy/paste I guess :)
But there is a Nero for Linux too.
[http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)
But it cost money... (if you dont steal it).. ups.. cant talk about that here.
But they have a free verion as well i think. ;)

---

### Post by Hmarroqu on 2006-10-18
yea the nero for linux is werid...i like ultra edition for win...

Anywho...Ive been trying with the command u gave me and on the linuxgamers page with my own directory of course and to no avail

i figureed that i had no Steamtmp.exe where it should be.. in sys32...and when i run the command 

wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14


it states 

Error: Steam.exe (main exception) : Falied to get file attributes, Win32 Error 2 "file not found"

:-k

---

### Post by aktiwers on 2006-10-18
Sorry im not familiar with this problem..  I hope someone else can help you out here.

Else it might maybe work, to remove it all, and install it again, following that guide I posted. That worked for me.

---

