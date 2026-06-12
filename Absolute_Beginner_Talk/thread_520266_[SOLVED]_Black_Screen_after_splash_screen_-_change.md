---
title: "[SOLVED] Black Screen after splash screen - changed login details- help Urgent!!"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ChrisNZ on 2007-08-08
Previous session after latest updates etc I wanted to add/change permission for my login/user name and the Kids so I could have root privilage and the rest would not.

I entered the User manager (two users present, one was root the other 'chris') and changed the permission somehow - cant remember what it was but I'm sure it was someting that had 'root' access on my user name.

Next day my dual boot hard drive would select Ubuntu OK, then start the splash screen loading it, then go blank except for the mouse icon which showing the circle timer etc.

Now I'm not familier how to undo or edit that file...if possible.. to login again!

I need files saved in that part of the directory and not in windoz 98 urgently!:mad:

TIA

Chris

---

### Post by aquavitae on 2007-08-08
Reboot and start in revocery mode.  When you get to the console, login as your user name and type ```
groups
```.  It should list the groups you belong to.  You can add a group by using ```
usermod -a -G <comma separated list of groups>
```
If you post the output of the groups command, we should be able to advise on what to change.

---

### Post by anubhavrocks on 2007-08-08
once you  are on the login screen,press 
```
CTRL+ALT+BACKSCPACE
```

If this does not solve the problem press

```
CTRL+ALT+F1
``` 
Now login with your regular username and password.

---

### Post by ChrisNZ on 2007-08-08
> **aquavitae said:**
> Reboot and start in revocery mode.  When you get to the console, login as your user name and type ```
groups
```.  It should list the groups you belong to.  You can add a group by using ```
usermod -a -G <comma separated list of groups>
```
If you post the output of the groups command, we should be able to advise on what to change.

Hi Thanks for the help - 
Logged in under the ubuntu "recovery" option,
 
root@chris-desktop:~$

typed groups

root adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin power erdev admin

type     usermod -a -G 

result is the options list, what should I have tried, and how do I copy the DOS type output to paste in this Windows 98 system? Will it still hold the copy? 

TIA

ChrisNZ

---

### Post by ChrisNZ on 2007-08-08
> **anubhavrocks said:**
> once you  are on the login screen,press 
```
CTRL+ALT+BACKSCPACE
```

If this does not solve the problem press

```
CTRL+ALT+F1
``` 
Now login with your regular username and password.

Hi Thanks for the help - 
CTRL + ALT + F1 works fine for getting into the DOS type screens, however I need to edit something in users or admin or ... to fix the login in screen blanked out problem...

Cheers

CHrisNZ

---

### Post by anubhavrocks on 2007-08-09
okay now try this command 

```
sudo dpkg-reconfigure gdm
```

and then type
```
sudo /etc/init.d/gdm restart
```

---

### Post by aquavitae on 2007-08-09
Your list of groups is the same as mine, so I doubt thats the problem.  Try anubhavrocks' suggestions:
> **anubhavrocks said:**
> okay now try this command 

```
sudo dpkg-reconfigure gdm
```

and then type
```
sudo /etc/init.d/gdm restart
```
> DOS type screens
Its called the console in linux:)

---

### Post by ChrisNZ on 2007-08-10
> **aquavitae said:**
> Your list of groups is the same as mine, so I doubt thats the problem.  Try anubhavrocks' suggestions:


Its called the console in linux:)

Thanks guys,

Ok so in root "Console" :) I 'll type these in and let you know the results.

If it's any help in this situation I've got a live Disk as well, I could load and view all the files, however was unsure what and how to fix this issue.

Back soon

Cheers

ChrisNZ

---

### Post by ChrisNZ on 2007-08-11
tried this command 

```
sudo dpkg-reconfigure gdm
```

Output = *Reloading GNOME display manager confg...
                *Changes will take effect when all current X sessions have ended.
                  inokes -rc .d: initscript gdm, action "reload" failed
                  root@chris-destop:~#

I then typed
```
sudo /etc/init.d/gdm restart
```

this put me back into the startup session, however still a black screen, icon timer and erratic HDD lights on system activity.

Used Reboot button of sys box, entered the dual boot screen loaded ubuntu and fingers crossed! No still not doing anything visibly different!

Ok - so let's eliminate what the problem isn't...? 
In causing this problem - suppose I set the "splash screen to a different AND and changed the user permissions to include "root" somehow... should the commands we have tried so far have made a difference _visually_ to at least get a login in screen again??

Is it not possible to boot from a Live CD of Ubuntu, access the affected files in the loaded version and edit them to fix this problem? So which files and do we/I need to be a progammer! :guitar:

Any other ideas out there?

Thanks all

---

### Post by anubhavrocks on 2007-08-12
change your /etc/gdm/gdm.conf to enable auto login.

---

### Post by ChrisNZ on 2007-08-13
> **anubhavrocks said:**
> change your /etc/gdm/gdm.conf to enable auto login.

Please tell me what I need to type to edit a file...?

CHeers

Chris

---

### Post by anubhavrocks on 2007-08-14
Okay edit your 
 ```
/etc/gdm/gdm.conf-custom
``` file make it look like this 

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=anubhav

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
```

and off course change "anubhav"  to to your user name.

---

### Post by aquavitae on 2007-08-14
> **ChrisNZ said:**
> Please tell me what I need to type to edit a file...?

CHeers

ChrisBoot in recovery mode, and type
```

sudo nano /etc/gdm/gdm.conf-custom

```
This will open the file in a text-based editor.  From there you shouldn't have any problems.

---

### Post by ChrisNZ on 2007-08-14
> **anubhavrocks said:**
> Okay edit your 
 ```
/etc/gdm/gdm.conf-custom
``` file make it look like this 

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=chris



[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
```

and off course change "anubhav"  to to your user name.

Daemon Was GtkModulesList+gail:atk-bridge:/user/lib.gtk-2.0/modules/libkeymouselistner:usr/Lib//gtk-2.0/modules/libdwellmouseListner
Add Gtkmodules=true

Qestion? What have I lost or really changed??:confused:

CHeer's this fixed the problem straight away. Thansk for all your help. Chris

---

### Post by ChrisNZ on 2007-08-14
> **aquavitae said:**
> Boot in recovery mode, and type
```

sudo nano /etc/gdm/gdm.conf-custom

```
This will open the file in a text-based editor.  From there you shouldn't have any problems.

This command enabled me to edit the file directly

Cheers Problem FIXED

Thank for all the help - Chris:popcorn:

---

### Post by anubhavrocks on 2007-08-14
> **ChrisNZ said:**
> Daemon Was GtkModulesList+gail:atk-bridge:/user/lib.gtk-2.0/modules/libkeymouselistner:usr/Lib//gtk-2.0/modules/libdwellmouseListner
Add Gtkmodules=true

Qestion? What have I lost or really changed??:confused:

CHeer's this fixed the problem straight away. Thansk for all your help. Chris

Please post the ```
 /etc/gdm/gdm.conf
```  file.I think some thing is wrong with it.Also since you have multiple users logging in to the box,this is at best a temporary solution.

---

