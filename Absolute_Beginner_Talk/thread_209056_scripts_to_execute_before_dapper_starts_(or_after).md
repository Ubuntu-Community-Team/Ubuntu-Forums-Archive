---
title: "scripts to execute before dapper starts (or after)//need something like autoexec.bat"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by ungaro on 2006-07-04
i need the equivalent of  autoexec.bat or startup folder in windows.

i want to start compiz xql after gnome starts. i have a script ready that i manually execute from terminal window

it's something like /usr/bin/thefuture 

also

i want to disable the shift + backspace combination (worst feature of dapper as of yet IMHO) with this script 

everytime dapper starts i manually execute this line

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"


thanks

---

### Post by Kilz on 2006-07-04
[QUOTE=ungaro]i need the equivalent of  autoexec.bat or startup folder in windows.

i want to start compiz xql after gnome starts. i have a script ready that i manually execute from terminal window

it's something like /usr/bin/thefuture 

also

i want to disable the shift + backspace combination (worst feature of dapper as of yet IMHO) with this script 

everytime dapper starts i manually execute this line

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"


thanks[/QUOTE]
System >Preferences >Sessions, click on the Startup programs tab.  Click add, then browse to the script. I would suggest placing it where you wont move it first.

---

