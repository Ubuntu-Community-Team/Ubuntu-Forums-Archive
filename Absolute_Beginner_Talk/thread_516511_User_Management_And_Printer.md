---
title: "User Management And Printer"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by rutz on 2007-08-03
Actually When Tryin to install ma printer when i used to click on the install.sb file it use to give me an error u need an root access permission so i went to user management and changed ma group to "root" from rutwik  ....  so i again tried to change it back to normal so was gettin the foll. error ..... and anyways the printer driver installation did not start ......i have an Samsung SCX-4100 Printer (laser printer and scanner combo) which is connected to a pc runnin windows XP and m runnin kubuntu on ma laptop .....so was tryin to share the printer on the LAN 

i downloaded foll. driver from samsung site 

```
20070725084555687_UnifiedLinuxDriver.tar.gz
```


M gettin foll error in user management : Screenshot below 


[IMG]http://img411.imageshack.us/img411/1147/snapshot3nj0.jpg[/IMG]


Plz help me to solve the problem ....

thanxxx in advance 

regards
rUTz!! :guitar:

---

### Post by thefoolisme on 2007-08-03
I don't see the screenshot.

---

### Post by nitro_n2o on 2007-08-03
don't change your group and run your program from the konsole and type sudo before the name that is sudo install.sh then enter the password.. there is another specific command to run gui aps with root privileges for kde but i forgot it

---

### Post by Hospadar on 2007-08-03
yeah if you need to run things as root you should use sudo or **kdesu** (kdesu does the same thing but in a graphical way, good for launchers, gui apps).  you don't want to change your group because this is going to monkey with a lot of file priviledges is ways you probably don't want.

sudo and kdesu will ask for a password, the one you want to use is your user password (not the root password).

so, to run your printer drivers, open up a terminal window (konsole) and cd to where you have the driver saved, something like ```
cd ~/Desktop
``` (if it's on your desktop)
then do ```
sudo <the filenamename of your driver>
``` if it's a script (as opposed to an executable, you might have to use "sh" to run it ```
sudo sh <the filename of your driver>
```

you can probably find more detailed instructions on exactly what command(s) you should use to run the driver install from their website.

---

### Post by rutz on 2007-08-03
actually had changed the group already ....................

now tryin to change it back its not happnin .............

actually when i try to enter the administrator mode to modify ma group its givin foll error

how can i change it back to normal 

here r screenshots of ma user management 

[IMG]http://img386.imageshack.us/img386/816/snapshot3nv6.jpg[/IMG]

[IMG]http://img365.imageshack.us/img365/5286/snapshot4rl7.jpg[/IMG]


[IMG]http://img365.imageshack.us/img365/5199/snapshot5rp2.jpg[/IMG]

[IMG]http://img369.imageshack.us/img369/4139/snapshot6yr8.jpg[/IMG]
plz help me as soon as possible ............

---

### Post by apswartz on 2007-08-04
Did you try logging out and back in?
The others have given you very good advice on installing the drivers and with the problem with using su.

One way you might fix the problem is to open a terminal and issue the following command...
```
sudo passwd
```
and issue a password for root. That should allow for a dialog to open up asking for that password in administrative mode. But, I would do the other stuff first to see if that solved the problem.

---

