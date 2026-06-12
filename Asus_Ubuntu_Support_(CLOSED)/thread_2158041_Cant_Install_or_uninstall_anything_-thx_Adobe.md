---
title: "Cant Install or uninstall anything -thx Adobe"
date: 2013-06-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by H15 on 2013-06-27
[COLOR=#000000]Ok I posted this in gen help but am getting advice that I have already tryed and was thinking it might be an ASUS problem so heres were I am at PLS HELP!!!

** ******************
OK i searched the web and found a few sites that talk about this problem and the all seem to have the same problem but they either dont post the solution or the posted solution dosnt work for me...When I try to install adobe flash player (Witch is suposed to come with crome) it soped mid install i had searched the web for a .deb pakage and found a bad one i guess so I tryed to reinstall it to no avail, so I tryed uninstalling software update and this is the problem:::[/COLOR]

[COLOR=#000000]me@noneofyourbiz:/home/me1$ sudo apt-get remove software update[/COLOR]
[COLOR=#000000][sudo] password for me: [/COLOR]
[COLOR=#000000]Sorry, try again.[/COLOR]
[COLOR=#000000][sudo] password for me: [/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree [/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR]
[COLOR=#000000]:::[/COLOR]

[COLOR=#000000]I need help i cant use softwarecenter at all and i cant perg or even force perg it says there is no file by that name when i look up the logs there is an .postinst and a .premp log but i at best can only read them when I try to delet even as admin i am told i dont have rights. Do i need to unlock Root ?[/COLOR]

[COLOR=#000000]FYI am useing ubuntu 12.04 LTS 64bit
****************************************************************************************************************
[/COLOR][COLOR=#000000]H152@minenoturz:~$ su -- H15[/COLOR]
[COLOR=#000000]Password: [/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$ sudo apt-get install adobe-flashplugin[/COLOR]
[COLOR=#000000][sudo] password for H15: [/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree [/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$[/COLOR]
[COLOR=#000000]************************************************** ****************************************[/COLOR]
[COLOR=#000000]I am useing Ubuntu 12.04 I was as up to date as of the time of the issue but now when I try to update I get....[/COLOR]
[COLOR=#000000]************************************************** ******************************************[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$ yum update[/COLOR]
[COLOR=#ff0000]The program 'yum' is currently not installed. You can install it by typing:[/COLOR]
[COLOR=#ff0000]sudo apt-get install yum[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$ update[/COLOR]
[COLOR=#000000]No command 'update' found, did you mean:[/COLOR]
[COLOR=#000000]Command 'xupdate' from package 'libxml-xupdate-libxml-perl' (universe)[/COLOR]
[COLOR=#000000]Command 'uupdate' from package 'devscripts' (main)[/COLOR]
[COLOR=#000000]Command 'lupdate' from package 'qt4-linguist-tools' (main)[/COLOR]
[COLOR=#000000]Command 'lupdate' from package 'qt3-dev-tools' (main)[/COLOR]
[COLOR=#000000]update: command not found[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$ sudo apt-get install yum[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree [/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H15$[/COLOR]
[COLOR=#000000]************************************************** ***************************************[/COLOR]
[COLOR=#000000]I cant install up date or remove anything without getting this reply.[/COLOR]

---

