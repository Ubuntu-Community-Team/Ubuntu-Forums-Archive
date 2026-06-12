---
title: "Epson CX3800 ink level indicator data?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by PhilOSparta on 2006-06-10
I have an Epson CX3800 series "all in one" printer.  Dapper senses it and has the necessary driver etc.   It prints well, scans properly etc., but one of he ink LEDs is flashing to indicate that one of the 4 ink cartridges is empty.

Is there a way to find out which ink cartridge is empty?  All the colors are printing on a test sheet.  

The properties menu items list resolution, paper size and various color adjustments, but I can't find anything that would tell me I'm out of ink.

---

### Post by PhilOSparta on 2006-06-12
[QUOTE=PhilOSparta]I have an Epson CX3800 series "all in one" printer.  Dapper senses it and has the necessary driver etc.   It prints well, scans properly etc., but one of he ink LEDs is flashing to indicate that one of the 4 ink cartridges is empty.

Is there a way to find out which ink cartridge is empty?  All the colors are printing on a test sheet.  

[/QUOTE]
EDIT/ADD:  Found!  :D 
There is a program "escputil" available to download via Synaptic.
It is a Command Line Interface (CLI) program.  Run it in a terminal.
I used this command to see if the program would work.  It timed out so I powered off then on the printer and it worked.
~>sudo escputil -d -r /dev/usblp0
EPSON Stylus CX3800

This command generated the ink levels.
~>sudo escputil -i -r /dev/usblp0
         Ink color       Percent remaining
              Cyan                      76
            Yellow                      77
           Magenta                      77
       Photo Black                       0
~>
Check out the man page for all the commands.

Good luck!
Phil

---

