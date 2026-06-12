---
title: "adding application with a script or alacarte"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Threbus5 on 2006-09-21
Hi,

I am using Dapper Drake.

Regarding two programs: nmap and wifi-ranger. They both run ok from a terminal window. Wifi-ranger requires sudo and nmap executes from a non administrative or "ordinary" terminal startup.

It would be elegant to be able to run them from a menu icon, like the rest of ubuntu.

The alacarte options lead me to believe that it should be possible to add an icon to the start menu that executes a terminal window program. This forum's discussions indicate that some sort of script should work.

SOLUTION

I used information from a post by darrenm about BASH scripting to build a script. The script displays the nmap help files in a terminal window and opens an xterm window under the user name in which one may execute nmap commands. The sudo restricts the script to function under adminstrative control. (using sudo may be a good idea as one probably wants to keep nmap activites under strict control)

Script -

sudo touch /bin/netmap
cd ~
cd /usr
nmap
xterm
#!/bin/bash
exit

The implementation to configure the system with a menu icon that launches the nmap app -

open the text editor and type (or paste) the script

save the script in the home directory (I chose to save it as filename netmap)

open a terminal window and type:
    chmod 700 netmap    
then press:  
    enter  
(this chmod gives the owner read/write/execute permissions over the file netmap) {you may close the terminal window after you press enter}

from the ubuntu menu, open the alacarte menu editor (it is in 'accessories')

select system tools (one may select any of the sub-menus or the top level menu - your choice - I wanted nmap in the submenu 'system tools')

on the top menu bar of the alacarte, select file and choose newfile (to add your file to the menu)

the file add widow will popup

in the file add window

choose an icon

select browse and go browse to your file (when you find it select 'open', you will see a path entered into the file name)

select text message and type in the pop-up scroll over message that you want

select to run in terminal

select OK

close the alacarte app

Clicking the icon in the ubuntu launch menu (if you placed it a submenu, you will need to go to that submenu) will launch two windows, one displaying nmap help and one with the user name ready to accept commands.

Hopefully my experience helps others of us newbies.

Oh, the wifi-ranger app actually installed itself as an app accessible from the unbuntu internet menu.

Take care,

---

