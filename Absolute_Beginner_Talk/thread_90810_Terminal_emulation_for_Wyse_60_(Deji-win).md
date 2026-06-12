---
title: "Terminal emulation for Wyse 60 (Deji-win)"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by fundy on 2005-11-15
Hello
We have been using windows with "Ice Ten" (with "deji-win") as a terminal emulation program to replace workstations such as Wyse 60, Wyse150 using a serial connection thru a digi-board.
Any suggestions on programs that could be used in Ubuntu to achieve the same effect? Or any experience using with Wine?
Thanks

---

### Post by Tomy on 2006-01-29
[quote=fundy]Hello
 We have been using windows with "Ice Ten" (with "deji-win") as a terminal emulation program to replace workstations such as Wyse 60, Wyse150 using a serial connection thru a digi-board.
 Any suggestions on programs that could be used in Ubuntu to achieve the same effect? Or any experience using with Wine?
 Thanks[/quote]  
 Hi, 
Just ran across your post today. We also have used "Ice Ten" for a serial connection thru a digi-board and are switching to Gnu/Linux. I have found two solutions that work but each has it's challenges.
 
1. Century Software sells "Term 4 Linux" (retails for $500 for a site license). This works after you figure out how to program the shifted function keys.
 
 2. There is a FOSS solution that also works for the wyse 60 emulation. 
 ```
$ sudo apt-get install ckermit
$ sudo apt-get install wy60
```  
 and then something like this:
 ```
$ wy60
$ kermit configFile

```  
 where configFile looks like this:
 ```
set modem type none
set line /dev/ttyS0
set speed 38400
set flow none
set carrier-watch off
connect
```  
 or you can  do it all on one line ( this is also how you can set up a launcher with  your company logo as an icon )
 ```
$ wy60 -c kermit configFile
```  
Getting this working may depend on the font you use ( I use Andale Mono from the msttcorefonts package). Some mono fonts cause the lines around boxes and some text to get garbled when the screen repaints. This is also related to the wyse60 entry in your termcap file. I assume you are logging into a unix server. 
 
Success may also depend on the terminal program you use to start term4linux or wy60/kermit. If you need the shifted-F10 key to work for your legacy apps you cannot use gnome-terminal because there is no way to disable the default binding of Shift-F10 in gnome-terminal ( don't waste your time - I even asked Havoc ). I use Ubuntu with Gnome but have installed KDE Konsole to run the terminal emulation. This also allows me to play with the Konsole schemas for the font colors and background.
 
One last problem I have run across -- this only works with Ubuntu 5.04 Hoary Hedgehog. Breezy and Dapper have some bug/feature that cause the lines around boxes and some text to get garbled when the screen repaints. If I upgrade a working Hoary system to Breezy or Dapper the terminal emulation is no longer useable. This happens with gnome-terminal and KDE konsole so I assume it has something to do with the way the operating system handles the serial connection or perhaps how the fonts are rendered. Fixing this is way beyond my skills because I am just an end user not a programmer.
 
 Tomy

---

### Post by quad-u on 2007-11-18
Any ideas on how to get this to work on a LAN connection via telnet which would allow you to set a terminal ID / terminal-type string?

---

### Post by Tomy on 2007-11-23
> **quad-u said:**
> Any ideas on how to get this to work on a LAN connection via telnet which would allow you to set a terminal ID / terminal-type string?

[COLOR=Black]```
wy60 -c telnet 192.168.1.110
```I set the terminal ID/type using a login script on the Unix file server. The user selects the Wyse 60 from a list of login choices. I think you may be able to send the Terminal ID using telnet options -- here is part of the telnet man page:

[/COLOR]```
$ man telnet 
....
environ arguments...
                The environ command is used to propagate environment variables
                across the telnet link using the TELNET ENVIRON protocol
                option.  All variables exported from the shell are defined,
                but only the DISPLAY and PRINTER variables are marked to be
                sent by default.  The USER variable is marked to be sent if
                the -a or -l command-line options were used.
....

```

---

