---
title: "esword"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-28
I got this from Frank's corner but I don't know what he means. I love this Bible program and I woul love to be able to install NASB and other add-ons.
It did install without doing this tip he gave but it will not let me install add ons.

[B]Tested Wine Version: 20050111

Before you install e-Sword you must add these lines to the [DllOverrides] section of ~/.wine.config:
"msi" = "native"
"msiexec.exe" = "native"
Type wine setup752.exe to install e-Sword.
Type wine e-sword.exe in the installation directory to run e-Sword. [/B]

---

### Post by harty83 on 2006-03-28
There is one dll in the esword folder that needs to be configured as "native" in wine.  I'm not in front of my home computer so I can't tell you which one.  It starts with an "r."  Copy that to windows/system32 folder.  Run winecfg from a terminal.  Click on libraries.  Find that dll and click add.  Change it to run as native.  Then your addons will work EXCEPT for dictionaries.  I can't get the dictionaries to list the words.  It only lists one or two and that's it.  If you find a way to fix that, I would def appreciate you letting me know!

Alan

---

### Post by KansasJoe on 2006-03-28
you may want to try bibletime....very nice program with all of the same features as esword and it runs native

sudo apt-get install bibletime

i know a few preachers who use this and love it

---

### Post by wolfee on 2006-03-28
I'd love to try bibletime too but I payed $20 for NASB and I'm sure since it's copyright protected bibletime won't come with it.

---

### Post by darkmaze on 2006-03-28
for gnome there's gnomesword

---

### Post by wolfee on 2006-03-28
Still frozen when I try to install commentaries. I'm running wine 0.9.10 is this the latest? I added riched20dll to library and set it for native. the only way I found it was by running resource hacker from wine. I still can't load wine onto application menue like it ran on mandrake 10.2 limited addition.

---

### Post by harty83 on 2006-03-28
There is a newer version.  Go to [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

That is what I used to get it working.  Also, after updating to the latest, try running ebible from a terminal so you can see what is happening.  That is how I figured out that I needed to set riched20.dll to native.  

Also, do you have IE installed?

Alan

---

### Post by wolfee on 2006-03-28
no I don't know how since microshaft sets it up so I can't because it says I dont have the right version of windows

---

### Post by wolfee on 2006-03-28
[QUOTE=wolfee]I got this from Frank's corner but I don't know what he means. I love this Bible program and I woul love to be able to install NASB and other add-ons.
It did install without doing this tip he gave but it will not let me install add ons.

[B]Tested Wine Version: 20050111

Before you install e-Sword you must add these lines to the [DllOverrides] section of ~/.wine.config:
"msi" = "native"
"msiexec.exe" = "native"
Type wine setup752.exe to install e-Sword.
Type wine e-sword.exe in the installation directory to run e-Sword. [/B][/QUOTE]
[B][I][U]Also "msiexec.exe" does not exist!!!!
[/U][/I][/B]

---

### Post by harty83 on 2006-03-28
To install IE, use ie4linux.  You can download it from [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/). 

Sorry for misleading you.  For some reason I had it in my head that there was a newer version of wine than 0.9.10.

---

### Post by wolfee on 2006-03-28
[QUOTE=harty83]To install IE, use ie4linux.  You can download it from [http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/). 

Sorry for misleading you.  For some reason I had it in my head that there was a newer version of wine than 0.9.10.[/QUOTE]
Thanx for the info!!! I downloaded it and installed it It was my first terminal install tar.gz!!!!!!!!!!!!!!!!!!!! I got lucky because I could not open the help file so I typed 
ies4linux/ies4linux
and it gave me a cool install options message!!! I chose #1
will programs that say: "you must have ie5 or 6 to install" now install with wine?

---

### Post by bored2k on 2006-03-28
May I suggest **gnomesword?** It's probably my favorite eSword application.

[CENTER][IMG]http://img69.imageshack.us/img69/2557/21uk1.jpg[/IMG]
[IMG]http://img529.imageshack.us/img529/1219/19uw.jpg[/IMG][/CENTER]

> **Bible study with GNOME**
A bible study program for GNOME using the SWORD library.
Features:
 Search Bible and Commentary
 Search Personal notes
 Add personal notes to verses
 Bookmarks
 Parallel Page - Display up to five versions
 StudyPad for keeping notes
 Spellcheck for StudyPad and Personal notes (uses gnome-spell)
 Uses modules from the SWORD Project
 Support for Sword Bible, Commentary, Lexicon and General Book modules

---

### Post by wolfee on 2006-03-28
I will use it however I paid $20 for NASB download for esword and I don't think gnomesword has it since NASB is copyright protected 
( Imagine that God's Word !!!!!)

---

### Post by bored2k on 2006-03-28
[QUOTE=wolfee]I will use it however I paid $20 for NASB download for esword and I don't think gnomesword has it since NASB is copyright protected 
( Imagine that God's Word !!!!!)[/QUOTE]
Wao. This is going off-topic, but *shock* wao. Copyrighted? So that means that if that's the only Bible I happen to have at a certain moment I won't be able to copy/give to others because... it's copyrighted? Wao. Why even bother with it?

Note: I didn't even knew NASB existed because I mostly use spanish Bibles, although all my Bible commentaries are in English (at least the ones on my box).

---

### Post by wolfee on 2006-03-28
[QUOTE=bored2k]Wao. This is going off-topic, but *shock* wao. Copyrighted? So that means that if that's the only Bible I happen to have at a certain moment I won't be able to copy/give to others because... it's copyrighted? Wao. Why even bother with it?

Because it is one of the most literal from greek to english word for word translations out there. More upto date than king jimy (written in 1611 before dead sea scrolls and "older" manuscripts were found)

---

### Post by paulperson on 2006-10-02
Ok the thing is, is that this guide is a bit outdated. 
1) Make sure that you have your wine updated. 
2) You need to download the newest version of esword (which right now it is setup777.exe) and save it or move it to your desktop
3) Type in your Terminal "wine "/home/accountname/Desktop/setup777.exe""
*put your account name where it says accountname
4) let it run, put let it installl blah blah blah
5) You need to override the riched20.dll so put put in your Terminal "winecfg" and go to the library tab. Type in riched20.exe under "New override for Library" and press apply
6) Go back to your terminal and type "wine "/home/accountname/.wine/drive_c/Program Files/e-Sword/e-Sword.exe""
*put your account name where it says account name
(I actually made a Launcher for this and put the icon on my Desktop.)
7) Hooray! Your inside, but for some reason a blank popup comes up and crashes the program. So you need to go to Options and uncheck all those checked things. When you leave you have to go File>Exit.
8) Go back to your terminal and type "wine "/home/accountname/.wine/drive_c/Program Files/e-Sword/e-Sword.exe""
Then your in. You have esword.

9) **This step is the most important one.** You have to give me your firstborn, and a virgin daughter.

Your done, but for some reason commentary doesn't work and neither does dictionary. If you want to have more translations then go to your friends computer (which hass all the translations you want, copy thier entire esword folder in thier Program Files folder over "/home/accountname/.wine/drive_c/Program Files/e-Sword/". Replace all.
(.wine folder is hidden so you have to unhide it. When your in your accountname folder press **Ctrl-H** to unhide it.)

God bless,
Paulperson

---

