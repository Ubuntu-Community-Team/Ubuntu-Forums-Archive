---
title: "daimonin need help!!!!!"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by hiro nakamatty on 2008-03-23
please please please can someone help me? i am a total noob at linux, i only just switched from windows, but im trying to install daimonin RPG, but i don't understand how to use the terminal, can some1 make me a step-by-step guide to installing it. please help me!much appreciated

---

### Post by llamakc on 2008-03-23
The instructions are provided with the zip file. Unzip it and read the appropriate README.txt. On Linux this would mean navigating to /PATH/TO/client/make/linux/ and reading the file README.debian which gives directions.

---

### Post by hiro nakamatty on 2008-03-23
thanks for that mate, but, i can't find the appropriate README file that give instructions for the installation

---

### Post by Tomatz on 2008-03-23
Send me a link to the game. Then i can have a look and post back instructions :)

---

### Post by hiro nakamatty on 2008-03-23
ok, thanks alot mate, this is a link to the download page where i got the linux download from.
[HTML]http://www.daimonin.com/Download.html[/HTML]

---

### Post by hiro nakamatty on 2008-03-23
please help

---

### Post by Tomatz on 2008-03-23
SOLVED:

[http://ubuntuforums.org/showthread.php?p=4582709#post4582709](http://ubuntuforums.org/showthread.php?p=4582709#post4582709)

---

### Post by hiro nakamatty on 2008-03-24
hey mate, thanks alot for the info, i only just got back on computer so i gonna try it out now, i give you a shout whether it works or not.

thanks/ matty.:lolflag:

---

### Post by hiro nakamatty on 2008-03-24
right, i typed ```
sudo apt-get install libsdl libsdl-mixer libsdl-image
``` like you said but i got this message
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libsdl
```

---

### Post by Tomatz on 2008-03-24
Sorry i got the package names wrong :oops:

Do step 1 like this:

**sudo apt-get install libsdl1.2debian libsdl-mixer1.2 libsdl-image1.2**

That should sort it :)

---

### Post by hiro nakamatty on 2008-03-24
right, i followed your instructions but when i tried to run the game i got this;

```
Can't find file settings/options.dat. Using defaults.
..Trying to find "Widget: STATS".. Found! (Index = 0) (22 widgets total)
..Trying to find "Widget: RESIST".. Found! (Index = 1) (22 widgets total)
..Trying to find "Widget: MAIN_LVL".. Found! (Index = 2) (22 widgets total)
..Trying to find "Widget: SKILL_EXP".. Found! (Index = 3) (22 widgets total)
..Trying to find "Widget: REGEN".. Found! (Index = 4) (22 widgets total)
..Trying to find "Widget: SKILL_LVL".. Found! (Index = 5) (22 widgets total)
..Trying to find "Widget: MENUBUTTONS".. Found! (Index = 6) (22 widgets total)
..Trying to find "Widget: QUICKSLOTS".. Found! (Index = 7) (22 widgets total)
..Trying to find "Widget: CHATWIN".. Found! (Index = 8) (22 widgets total)
..Trying to find "Widget: MSGWIN".. Found! (Index = 9) (22 widgets total)
..Trying to find "Widget: MIXWIN".. Found! (Index = 10) (22 widgets total)
..Trying to find "Widget: GROUP".. Found! (Index = 11) (22 widgets total)
..Trying to find "Widget: PLAYERDOLL".. Found! (Index = 12) (22 widgets total)
..Trying to find "Widget: BELOWINV".. Found! (Index = 13) (22 widgets total)
..Trying to find "Widget: PLAYERINFO".. Found! (Index = 14) (22 widgets total)
..Trying to find "Widget: RANGEBOX".. Found! (Index = 15) (22 widgets total)
..Trying to find "Widget: TARGET".. Found! (Index = 16) (22 widgets total)
..Trying to find "Widget: MAININV".. Found! (Index = 17) (22 widgets total)
..Trying to find "Widget: MAPNAME".. Found! (Index = 18) (22 widgets total)
..Trying to find "Widget: CONSOLE".. Found! (Index = 19) (22 widgets total)
..Trying to find "Widget: NUMBER".. Found! (Index = 20) (22 widgets total)
..Trying to find "Widget: STATOMETER".. Found! (Index = 21) (22 widgets total)
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
Defaultskin (skins/subred.zip) not found. Your client will most likely crash!
PHYSFS: skins/subred not found.
PHYSFS_addPath facepack.zip failed: File not found
PHYSFS_addPath4 failed: File not found
List Video Modes
All resolutions available.
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no
VideoInfo: video memory: 0KB
Could not load skin-definition for skin: subred.
Reason: No such file or directory
Using defaults.
file: bitmaps/palette.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/palette.png
load_bitmap(): Can't load bitmap bitmaps/palette.png
file: bitmaps/font7x4.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font7x4.png
load_bitmap(): Can't load bitmap bitmaps/font7x4.png
file: bitmaps/font6x3out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap bitmaps/font6x3out.png
file: bitmaps/font_big.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font_big.png
load_bitmap(): Can't load bitmap bitmaps/font_big.png
file: bitmaps/font7x4out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap bitmaps/font7x4out.png
file: bitmaps/font11x15.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font11x15.png
load_bitmap(): Can't load bitmap bitmaps/font11x15.png
file: bitmaps/font11x15out.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/font11x15out.png
load_bitmap(): Can't load bitmap bitmaps/font11x15out.png
file: bitmaps/intro.png does not exist in physfs
PHYSFSRWOPS_openRead failed: (null)
ERROR sprite.c: Can't load sprite bitmaps/intro.png
load_bitmap(): Can't load bitmap bitmaps/intro.png
Segmentation fault (core dumped)

```
:confused::confused::confused::confused::confused::confused::confused::confused:
i have no idea what any of this means, if you could make sense of any of this, can you please try and figure a way out lol, much appreciated, thanks alot
thanks/ matty

---

### Post by Tomatz on 2008-03-24
Type this in a terminal:

**SDL_AUDIODRIVER=null daimonin**

or

**SDL_AUDIODRIVER=null ./daimonin**

If all works well get back and ill tell you how to make it start like that everytime.

Its a bug well known to the developers :)

---

### Post by hiro nakamatty on 2008-03-24
sorry mate:)

but here we go again...
```
bash: daimonin: command not found
```


srry bout wasting your time m8, thanks

matty

---

### Post by hiro nakamatty on 2008-03-24
srry but it still comes up with the same error message i sent you before about the WIDGET etc...

---

### Post by Tomatz on 2008-03-24
Can you r click on the main menu, then edit menu, then find daimonin and tell me the command it uses?

---

### Post by Tomatz on 2008-03-25
**This is now SOLVED go here:**

[http://ubuntuforums.org/showthread.php?p=4582709#post4582709](http://ubuntuforums.org/showthread.php?p=4582709#post4582709)

---

