---
title: "How to use wine???"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-02
Hey i just installed wine in the add/rm programs list. Im want to be able to play a few windows games using it. How do I use wine?:D

---

### Post by Qwerty_ on 2006-09-02
```
 wine game.exe 
``` 

That should do it also make sure you are in the right dir where the .exe that you want to run is.

---

### Post by WalmartSniperLX on 2006-09-02
> **Qwerty_ said:**
> ```
 wine game.exe 
``` 

That should do it also make sure you are in the right dir where the .exe that you want to run is.

awesome thanks

---

### Post by DougieFresh4U on 2006-09-02
I tried wine game.exe & came up with 'module not found' I am having a rough time with this wine crap!!](*,)

---

### Post by eternalis on 2006-09-02
Game.exe means the name of the Game EXE file.

---

### Post by WalmartSniperLX on 2006-09-02
> **eternalis said:**
> Game.exe means the name of the Game EXE file.

Lol -slaps self- thats what i thought at first but i tried 'game.exe' lol

---

### Post by WalmartSniperLX on 2006-09-02
Ok well im trying to install doom 3 and it makes it as far as the actuall install process where it extracts the files, but when it starts, it stops and theres an eror saying it cant find something, then it freezes and i cant close the installer. I would have to reboot and try again to see what it says exactly. But does anyone know what i would be talking about and how to fix it?

---

### Post by bodhi.zazen on 2006-09-02
Welcome to wine.

Try wineHQ: [http://appdb.winehq.org/appview.php?iAppId=1278](http://appdb.winehq.org/appview.php?iAppId=1278)

AS far as re-booting, in a terminal type:
```
wineserver -k
``` to kill wine (you do not need to re-boot).

---

### Post by WalmartSniperLX on 2006-09-02
> **bodhi.zazen said:**
> Welcome to wine.

Try wineHQ: [http://appdb.winehq.org/appview.php?iAppId=1278](http://appdb.winehq.org/appview.php?iAppId=1278)

AS far as re-booting, in a terminal type:
```
wineserver -k
``` to kill wine (you do not need to re-boot).

Ok thanks :D

---

### Post by WalmartSniperLX on 2006-09-02
O i c it wont work with the retail disc. Ok thanks ALOT :D

---

### Post by Matt Yun on 2006-09-02
You might be SOL with the Windows version of Doom3; it's not WINE compatible according to [Frank's Corner]("http://www.frankscorner.org/index.php?p=fps").  

Unfortunately, WINE is not exactly newbie-friendly, apart from trivial Windows programs.  [www.frankscorner.org](www.frankscorner.org) is an excellent resource for WINE.

If all you want to do is play Doom3, why don't you try the native Linux version?  See [the Doom3 GNU/Linux FAQ]("http://zerowing.idsoftware.com/linux/doom/").  I don't play it myself, so I can't provide any further guidance.

---

### Post by WalmartSniperLX on 2006-09-02
> **Matt Yun said:**
> You might be SOL with the Windows version of Doom3; it's not WINE compatible according to [Frank's Corner]("http://www.frankscorner.org/index.php?p=fps").  

Unfortunately, WINE is not exactly newbie-friendly, apart from trivial Windows programs.  [www.frankscorner.org](www.frankscorner.org) is an excellent resource for WINE.

If all you want to do is play Doom3, why don't you try the native Linux version?  See [the Doom3 GNU/Linux FAQ]("http://zerowing.idsoftware.com/linux/doom/").  I don't play it myself, so I can't provide any further guidance.

Ok thanks Ill look into that! :D

---

### Post by WalmartSniperLX on 2006-09-02
Just wondering but isnt there something else (or more others) like wine but allows different games?

---

### Post by WalmartSniperLX on 2006-09-02
Ok I installed a game demo (call of duty). How do i run it using wine???

I tried running it using the wine command and directing to the dir where the .exe is but i get this message saying I need to run it from the correct folder. What does that mean?

---

### Post by bodhi.zazen on 2006-09-02
> **WalmartSniperLX said:**
> Ok I installed a game demo (call of duty). How do i run it using wine???

I tried running it using the wine command and directing to the dir where the .exe is but i get this message saying I need to run it from the correct folder. What does that mean?

What command are you using exaclty?

wine .....

For games try cedega:
[Cedega wiki]("http://en.wikipedia.org/wiki/Cedega")
[Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1}")

---

### Post by WalmartSniperLX on 2006-09-02
> **bodhi.zazen said:**
> What command are you using exaclty?

wine .....

For games try cedega:
[Cedega wiki]("http://en.wikipedia.org/wiki/Cedega")
[Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1}")

im using "wine <pathname/filename.exe>

EDIT: Thanks for the links :D

---

### Post by WalmartSniperLX on 2006-09-02
Does cedega cost money?

---

### Post by bodhi.zazen on 2006-09-02
I think there is $ involved, I do not use cedega (not a gamer, sorry).

The path_to_program.exe can be tricky.

Windows uses "Program Files" in the path. The <space> in "Program Files" can be hard for Linux.

Use "Program\ Files" (Watch that slash).

for example:

wine /home/user_name/.wine/c_drive/**Program\ Files**/Program.exe

Of course, use the correct path for your box/install.

---

### Post by WalmartSniperLX on 2006-09-02
> **bodhi.zazen said:**
> I think there is $ involved, I do not use cedega (not a gamer, sorry).

The path_to_program.exe can be tricky.

Windows uses "Program Files" in the path. The <space> in "Program Files" can be hard for Linux.

Use "Program\ Files" (Watch that slash).

for example:

wine /home/user_name/.wine/c_drive/[b]Program\ Files[b]/Program.exe

Of course, use the correct path for your box/install.

OMG that solved a big prob for me with wine. Thanks a lot :D lol i couldnt get that dir stuff figured out

---

### Post by WalmartSniperLX on 2006-09-02
Ok one last thing. When im prompted for the startup entry what do I title it as? Do i keep it at what is selected by default?

---

### Post by greeklegend on 2006-09-02
If you have actual windows installed, it can be helpful if you dump the entire contents of your windows system32 folder into the wine system32 folder. Many functions of windows arn't implemented in wine as yet, but using  windows binaries improved things for me a bit.

---

### Post by WalmartSniperLX on 2006-09-02
> **greeklegend said:**
> If you have actual windows installed, it can be helpful if you dump the entire contents of your windows system32 folder into the wine system32 folder. Many functions of windows arn't implemented in wine as yet, but using  windows binaries improved things for me a bit.

thats an excellent idea. So if i just extract my system32 folder into the wine system 32 folder Ill notice an improvement with software compatibilites?

---

### Post by WalmartSniperLX on 2006-09-03
Ok now Im trying to get Steam working and it installs, but when it does the update it just closes. What is wrong?:confused:

---

### Post by WalmartSniperLX on 2006-09-03
I think its cuz i didnt install the font package into the system/fonts dir. Do i just copy the .exe in there or do i have to use a certain command?

---

### Post by WalmartSniperLX on 2006-09-04
Lol ok. :P Im trying to install Sonic Stage so i can put music on my mp3 player in linux. The problem is that i need to run both the install.exe and the install.ini. Cuz when i use wine install.exe it opens the start menu, but i cannot click the options since the script isnt running. How do i get it to run both the ini and exe??? Is that even what ur supposed to do? :confused:  sorry im a wine noob as much as a linux noob :mrgreen:

---

