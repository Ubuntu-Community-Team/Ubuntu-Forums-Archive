---
title: "HELP! Ubuntu hangs on loading screen"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by quicksilver1024 on 2007-06-17
Okay. I have managed to install Ubuntu with my partitioning plan. However, the problem was that there were bad sectors on my HD and thus the windows partition couldn't be resized. I have used the resize with bad sector option and it worked fine.

After I have installed Ubuntu and have restarted, GRUB worked perfectly but once Ubuntu was selected to run. It hangs after a few seconds on the loading screen. After, the screen shows a MS-DOS like interface (is this the terminal?) and after a few lines that scrolls too quickly to follow, I am asked for user name and password. I type it in (same as what I had done during the install) but it says permission denied (or something on those lines since the screen scrolled too quickly to follow).

I have tried the noapic option and it didn't work. Then, I removed quiet and splash from kernel so that I could get a clearer understanding of what was happening behind the loading screen.

I get this warning many times throughout the loading:

warning: fake start-stop-daemon called, doing nothing

Here are a few lines just before the loading hangs:

*Starting deferred execution scheduler atd
warning: fake start-stop-daemon called, doing nothing

*starting periodic command scheduler crond
warning: fake start-stop-daemon called, doing nothing
.
.
.
.
*Running local boot scripts (/etc/rc.local)

The last line seems to last indefinitely....

Can someone please help me?!

I'm almost there!

EDIT: Sometimes this line appears over and over again as well:
-bash: /dev/null: Permission denied

---

### Post by quicksilver1024 on 2007-06-17
bump

---

### Post by quicksilver1024 on 2007-06-18
The problem seems to be when the system tries to load the hardware drivers...it says [failed] beside "Loading hardware drivers..."

All the other steps taken to load Ubuntu seems to be alright.

Can anyone please help me?

---

### Post by johndoe75 on 2007-11-16
I'm having a same problem with the latest ubuntu server edition (7.10). 
I get the same warning. I can succesfully login as user in DOS mode, unforunately I'm not yet familiar with 
the commands. 

I was hoping to see a GUI, but that's not the case. 
Or is it normal that the Ubuntu server edition always starts up in this DOS-like mode?

_Extra info:_

I have checked the install cd for errors. result= *'The cd-rom integrity test was succesful. The cs-rom is valid'*
I have tried the "Rescue a broken system" option, but without success. It starts the same routine and end up with the same warning.

When going in recovery mode, I still get the error message, but this time after prox 4 minutes(when the hardwaredrivers are loaded) I'm logged in as the *root@myUsername*.

[edit]
I found out what 'my' problem is..

> 
[SIZE="4"]**[COLOR="Sienna"]System Requirements[/COLOR]**[/SIZE]
[I]
Ubuntu 7.10 Server Edition supports three (3) major architectures: **_Intel x86, AMD64, and PowerPC_**. The table below lists recommended hardware specifications. Depending on your needs, you might manage with less than this. However, most users risk being frustrated if they ignore these suggestions.[/I]


I've installed the server edition on a system with an  old Atlhon XP 2000+...

[/edit]

---

