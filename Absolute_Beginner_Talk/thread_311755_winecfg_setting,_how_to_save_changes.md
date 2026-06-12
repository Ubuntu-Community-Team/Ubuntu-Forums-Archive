---
title: "winecfg setting, how to save changes"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-03
how do you save your setting changes in winecfg, every time i enter winecfg and try to change the screen size 640x480 to 1024x768 and exit out and then go back into it it's back to the 640x480

also i installed a game starcraft just to see if i could get it to work and it does but how do i put a short cut on my desktop, can not find where it got installed to,can not find anything that gets installed,i need to find my program folder i thing:mrgreen: 
thanks

---

### Post by WalmartSniperLX on 2006-12-03
When I do winecfg I just hit "apply" then "ok"

As far as startcraft, if you didnt change the dir when installing it should be in    /home/<username>/.wine/drive_c/Program Files

Remember when you use the terminal use "\" before spaces. EXE: /home/ron/.wine/drive_c/Program\ Files

---

### Post by broekskw on 2006-12-03
thanks for your reply.ok went back into winecfg but the apply button is not showing,need to resize my screen tried to drag it up but still no go:mad: 
ok used the tab key and hit enter, worked like a charm :cool:

---

### Post by WalmartSniperLX on 2006-12-03
> **broekskw said:**
> thanks for your reply.ok went back into winecfg but the apply button is not showing,need to resize my screen tried to drag it up but still no go:mad: 
ok used the tab key and hit enter, worked like a charm :cool:

Im glad you got that worked out 8)  What about saving the settings? Was that your main problem? (that 'appy' wasnt showing)

---

### Post by broekskw on 2006-12-03
ok tried the command to find my program file for starcraft but no luck, please if you can take a look at my screen shot and tell me what i am doing wrong. thanks

---

### Post by WalmartSniperLX on 2006-12-03
you use the wine command to launch any windows program (.exe) through wine.

What you're doing is using an unknown command ;) (exe) and your only typing in the directory inwhich starcraft is in, not the .exe. I launch starcraft like this:

```
 cd /home/patrick/.wine/drive_c/Program\ Files/Starcraft\ Broodwar
 wine Brood.exe 
```

I find is usefull to navigate to the folder where the .exe is first, then use the wine command and launch the .exe

You can find this folder in your file browser by going to "places/Home" and hitting Ctrl+h (to show hidden folders) and click on .wine 

Let me know if you're confused or need more help :D

EDIT: Dont copy what I use to lauch SC exactly because my files/apps may be named different. Do what i said above and goto the .wine folder using the file browser and go to drive_c/Program Files and you should find your starcraft folder there. Click it and find the .exe. That is the .exe you will be using on the "wine" command.


Oh and another thing here are your basic commands for this task (incase you need them)

 cd               = navigates/changes directory  EXAMPLE: cd /usr/local/ would then change to the /usr/local folder
 wine             = executes any windows .exe or app using wine
 wine --version   = tells you what version of wine you are using
 winecfg          = edits/configures wine

---

### Post by broekskw on 2006-12-03
hey man thanks.ctrl h works great now i see everything:D :D 
this site rocks big time:mrgreen:

---

### Post by WalmartSniperLX on 2006-12-03
> **broekskw said:**
> hey man thanks.ctrl h works great now i see everything:D :D 
this site rocks big time:mrgreen:

No problem :D :D 

If you still need any help whatsoever just post it here, Ill be glad help 8)

---

### Post by broekskw on 2006-12-03
hey WalmartSniperLX I have another problem. trying to install a game c&c but keep getting this error every time i run the exe file from the disc using wine. some other people here are trying to help also in a diff post, one person told me to check to make sure it's executable under permissions. how do i check this out have no clue what he is trying to tell me](*,) 
again thanks:mrgreen:

---

### Post by broekskw on 2006-12-03
I also get this error

---

### Post by WalmartSniperLX on 2006-12-03
try doing 

```
 wine Setup.exe 
```

If that doesn't work try lower casing setup.exe since the terminal IS case sensitive :P

And remember you must cd to the directory first :D

Also if you arent sure about the dir name of the cd, just do this in the terminal 

```
 nautilus /media 
``` 

and find the command and conquer disc. Then when you figure out the path (should be like /media/cdrom/<whatever> or /media/cdrom0/<whatever>), cd to that in the terminal before doing wine Setup.exe

---

### Post by broekskw on 2006-12-03
sorry for so many questions but how do you " And remember you must cd to the directory first"  
here is what i get when i do a wine Setup.exe
also when i do nautilus /media i get this screen up cdrom cdrom0 floppy and floppy0
so both cdrom and cdrom0 have all the c&c files in them
so i must first cd rom in terminal and then wine setup.exe correct](*,)

---

### Post by houstonbofh on 2006-12-03
cdrom is a link to cdrom0, so they are the same.  Get into cdrom from the terminal.  Type "ls" and look for setup.exe or Setup.exe, or something similar.  Then type "wine ./setup.exe" and you should be off.  Also, [http://www.frankscorner.org/](http://www.frankscorner.org/) is a site you may find useful.

---

### Post by WalmartSniperLX on 2006-12-03
To cd to a directory means to navigate to it in the terminal

```
 cd /media/cdrom0/<whatever folder Setup.exe is in> 

```

once you do that, it should just go to the next line in the terminal. Then type in the wine command to launch the .exe

```
 wine Setup.exe 
```

PS dont feel sorry for asking so many questions :D Thats what the forums are for :P

---

### Post by broekskw on 2006-12-03
thanks houstonbofh for your info and yes i did get the cd command
cd /media/cdrom and then enter to get /media/cdrom$ then i did ls to get everything listed an saw a autorun.exe or a setup.exe file but both times it starts to load and then i get both error as posted before. setup error window that i have to x out and then the terminal error message agian.did go to the site that you gave me a link to and type in command and conquer error and fond a post from 2004 but no one responder to that one.same problem as i have](*,) ](*,) will keep trying.have another computer with ubunto on will try that one and see if i get the same problem. that site that you gave me had c&c as a game that runs no problem, it give you the command to run it also.so not sure how come it will not work for me:mrgreen:

---

### Post by broekskw on 2006-12-03
ok on my other system same thing happens. setup error and then terminal error.
so it must be something in ubuntu setup.SOMEONE here must of run into this before,have to tell you something good about this problem, i sure am getting better at typing commands in the terminal window:)

---

### Post by houstonbofh on 2006-12-04
Sounds like C&C does not want to work and play well with others. :D  Another site to check is the Wine Application Database at [http://appdb.winehq.org/](http://appdb.winehq.org/) but it is down at the moment.  Some more hints at [http://www.winehq.com/site/howto](http://www.winehq.com/site/howto) and instructions to install the latest version at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) might help you.  You also might try Gaming and Leasure at [http://www.ubuntuforums.org/forumdisplay.php?f=93](http://www.ubuntuforums.org/forumdisplay.php?f=93) for more help.  It looks like this is a C&C specific problem.  Good luck!

---

### Post by broekskw on 2006-12-04
thanks will look at all. have been reading and reading, lots of other programs to run games on, dosbox is one but then you need to install other aps to get this to work, my mind is ready to explode:-? ](*,)

---

### Post by broekskw on 2006-12-04
ps are you from houston (bc canada) like i am:mrgreen:

---

### Post by houstonbofh on 2006-12-06
> **broekskw said:**
> ps are you from houston (bc canada) like i am:mrgreen:
A little further south... ;) 2882.53 miles from mapquest.

---

