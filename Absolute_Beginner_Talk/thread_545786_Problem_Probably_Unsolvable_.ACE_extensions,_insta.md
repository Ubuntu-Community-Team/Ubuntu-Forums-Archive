---
title: "Problem Probably Unsolvable: .ACE extensions, installing a game."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by vertexoflife on 2007-09-08
Hello. I am running Ubuntu 7.04 on a Toshiba Tecra laptop.

I own the program Crossover Linux Codeweavers.

I own a copy of the game Neverwinter Nights, but the CD is too scratched. Well within my legal rights, a downloaded a copy of the game off the internet. Now, I should have no problems running it once I actually get it installed.

However, the installation is killing me.

The game came in two .RAR archives, which extracted reveal an .ACE extension file which I am supposed to unace and install together. However, I cant unace, and I am uncertain of how to compile two seperate .RAR archives to create a executable install file.

Crossover Office can easily run Neverwinter Nights after I install it sucessfully.

Any suggestions?

---

### Post by avik on 2007-09-08
Install the unace package through apt-get or synaptic, then use that to unace the .ACE archive.

---

### Post by vertexoflife on 2007-09-08
I did, using 

unace x file.ace in terminal. Didn't seem to do anything to the file.

---

### Post by avik on 2007-09-08
Was another file or folder deposited into the current folder?  What's the output of:

```
unace l file.ace
```

And are sure it's .ace and not .ACE.  Case matters.

---

### Post by vertexoflife on 2007-09-08
Date    &#65533;Time &#65533;Packed     &#65533;Size     &#65533;Ratio&#65533;File                           
                                                                          
10.07.02&#65533;15:13&#65533;        368&#65533;     1579&#65533;  23%&#65533; setup.bat                     
28.05.02&#65533;15:20&#65533;       2428&#65533;    10742&#65533;  22%&#65533; dmvault/dungeonmaster.bic     
10.07.02&#65533;15:31&#65533;    1153040&#65533;  1183976&#65533;  97%&#65533; movies/AtariLogo.bik          
23.03.02&#65533;12:44&#65533;        204&#65533;      352&#65533;  58%&#65533; movies/BiowareLogo.bik        
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/Chap1_Chap2.bik        
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/Chap2_Chap3.bik        
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/Chap3_Chap4.bik        
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/credits.bik            
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/ending.bik             
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/NWNintro.bik           
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/prelude_chap1.bik      
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/prelude.bik            
23.03.02&#65533;12:44&#65533;         32&#65533;      352&#65533;   9%&#65533; movies/WOTCLogo.bik           
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_ruralday2.bmu       
01.07.02&#65533;23:26&#65533;         24&#65533;       44&#65533;  54%&#65533; music/mus_mines1.bmu          
01.07.02&#65533;23:26&#65533;         24&#65533;       44&#65533;  54%&#65533; music/mus_gendungeon1.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_tavern3.bmu         
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_tavern4.bmu         
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_forestday1.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_evildungeon2.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_evildungeon1.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_crypt2.bmu          
01.07.02&#65533;23:26&#65533;         24&#65533;       44&#65533;  54%&#65533; music/mus_crypt1.bmu          
01.07.02&#65533;23:26&#65533;         24&#65533;       44&#65533;  54%&#65533; music/mus_templeevil.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_templegood.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_cityslumday.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_citynite.bmu        
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_citymarket.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_citydocknite.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_richhouse.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_mines2.bmu          
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_rural1.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_lizboss.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_forest2.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_forest1.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_tavern2.bmu         
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_endboss.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_dung3.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_dung2.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_dung1.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_dragon.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_city3.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_city2.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_city1.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_citboss.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_aribeth.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_templegood2.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_ruralday1.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_store.bmu           
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_ruralnite.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_sewer.bmu           
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_tavern1.bmu         
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_castle.bmu          
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_citydockday.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_bat_forboss.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_argend.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_aribev.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_aribgd.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_chap1.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_chap2.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_chap3.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_chap4.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_main.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_maugrm.bmu    
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_morag.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_theme_nwn.bmu       
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_citywealthy.bmu     
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_forestnite.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_forestday2.bmu      
01.07.02&#65533;23:26&#65533;         44&#65533;       44&#65533; 100%&#65533; music/mus_cityslumnite.bmu    
09.03.02&#65533;01:04&#65533;    1283172&#65533;  3719168&#65533;  34%&#65533; ereg/INF1.EXE                 
07.03.02&#65533;23:06&#65533;      99304&#65533;   100864&#65533;  98%&#65533; mythXuha.exe                 

That's the output I get.

---

### Post by vertexoflife on 2007-09-08
When I try to unace by using "unace x file.ace" this is what I get:

UNACE v2.5     Copyright by ACE Compression Software       Jun 18 2003 22:25:55
                                                                          
processing archive /home/b***/NWN/Neverwne.ace                           
Working: Creating listfile. Please wait.                                  
  extracting ambient                                                      
Error: Could not create directory:
 Name is used by a file.

---

### Post by vertexoflife on 2007-09-08
Okay, now I somehow managed to unace the two different parts of the game into different folders. So now I have two parts of the game in different folders, and no idea how to combine them or install the game.

Any hints? lol.

---

### Post by vertexoflife on 2007-09-08
-bump-

---

### Post by avik on 2007-09-09
I've never played or installed Neverwinter Nights, but I'll try my best to help.  I noticed file.ace contains two .exe files and a setup.bat.  Are either of the .exe files the main .exe file, and does the other .ace archive contain any .exes?

What exactly do the two parts contain?  Maybe it's possible to just copy files from one directory to another...

---

### Post by argie on 2007-09-09
I know this doesn't address the issue, but you can get a linux binary for NWN and you don't need to use Crossover Office.

About your problem, I'm not sure but I think once you've installed unrar and unace, the file roller (Archive Manager) program will be able to open those files. If you extract from there you shouldn't have any trouble. I know that File Roller manages to open multipart rar files fine.

---

### Post by slimdog360 on 2007-09-09
[http://nwn.bioware.com/downloads/linuxclient.html]("http://nwn.bioware.com/downloads/linuxclient.html")

---

