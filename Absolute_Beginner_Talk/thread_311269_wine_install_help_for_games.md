---
title: "wine install help for games"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-02
](*,) ok trying to install command and conquer on ubuntu 6.10 .now i have read and tried to install wine 0.9.25 and i think i did but have some error after installing.
/home/broeks/Desktop/Screenshot.png

ok are there other programs that i need also to install??
after i get it going(some time soon i hope)how do i install the game??
have been reading on so many form sites my head is about to explode:evil: 
some sites say install this way and others this way. then go into winecfg and make changes also install winetools also install Jasmin 3D Color Changer 4 and DisplaySet but can not open files as directed. 
so i hope everyone here is kind to me (44 old dutchman) trying out new thinks. :D 

thanks and hope to here from you all sometime soon;)

---

### Post by broekskw on 2006-12-02
sorry tried to link my error screen here but did not work ,took a screen shot of my error can someone tell me how to post it in this message

thanks

---

### Post by broekskw on 2006-12-02
ok did some more reading and installed more programs and also got Jasmin 3D Color Changer 4 and DisplaySet  working(so simple select the exe file and then open with other application and then use custom comand then type wine in that command line and hit enter). now every time i load the cd and click on the autorun.exe or install.exe file and select open with other program and then custom and type wine its starts to install then gives me a error message "setup warning" unable to locate necessary files: please run setuo.exe fromthe cd-rom disc. ok thats what i did selected the exe file from the did](*,) any one have a solution for me thanks:mrgreen:

---

### Post by Shatrat on 2006-12-02
To post a screenshot you need to attach the file or link to a file that is uploaded to some server somewhere.  Just putting the address of where it is on your computer doesn't help, since we aren't using your computer.

There is an attachments button at the bottom of the advanced posting view.

As to running things in wine, im not sure exactly how you're doing it but you should try using a terminal window.  Wine is used like this, ```
wine /address/to/windows/executable.exe
``` where /address/to/windows/executable.exe is the path to whatever windows program you want to run in wine, like '/home/broeks/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe'  or whatever.  Running something from a CD you would want to go to /media/cdrom to look for the setup.exe or whatever you need to run.  
Sometimes theres problems running things that way and you might want to copy the whole thing to some directory in your home.  

From the error you got, it sounds like maybe your working directory needs to be wherever the setup file is.  So you would want to ```
cd /media/cdrom
``` or ```
cd /home/boeks/thisiswhereiputthestuffonthecdlol
``` depending on wherever you copied your setup files and then run wine setup.exe

Hope this makes sense.

---

### Post by broekskw on 2006-12-02
thanks for you reply. did try the command cd/media/cdrom and it tried to load again but keep getting this error about the cdrom also here is my first screen shot showing my other errors, but i installed alsa program so i think i am good to go. still trying to install command and conquer???
8)

---

### Post by broekskw on 2006-12-02
ok so here is the error message i get in terminal mode after cd/media/cdrom hit enter then  win ./setup.exe. help help thanks;)

---

### Post by Shatrat on 2006-12-02
Check this link out.  Its the wine app database entry for C&C Red Alert. The very first comment has the same problem you're talking about.  Apparently you need to add the cdrom as a dos device in wines dos devices configuration.  The replies to the comment explain the process.
Good luck.
[http://appdb.winehq.org/appview.php?iVersionId=727](http://appdb.winehq.org/appview.php?iVersionId=727)

---

### Post by broekskw on 2006-12-02
thanks again for this link,but after reading this not to sure as how to fix this problem:confused: 

Installer fails in current CVS (2006/04/08)
by Bernhard Rosenkraenzer on Saturday April 8th 2006, 6:09
wine autorun.exe works and gives the setup splash screen. Clicking "Install red alert" results in "Unable to locate necessary files. Please run Setup.exe from the CD-ROM disc." (the disc is mounted at /mnt/cdrom, which is also pointed to by ~/.dosdevices/d: - wine d:\\autorun.exe behaves identically).

Launching setup.exe (and the various setup.exes in subdirectories) results in this output on the console:

$ wine SETUP.EXE
Usage: winevdm.exe [--app-name app.exe] command line
 
what does this all mean.sorry but trying so hard to understand.](*,) 

thanks

---

### Post by Shatrat on 2006-12-02
Well, apparently this guy is saying that he is still getting the problem with his CDROM configured as d: in wine, and running wine d:\\autorun.exe and running wine /media/cdrom/autorun.exe are doing the exact same thing.  d: would the be windows way of addressing /media/cdrom.
The dosdevices are links in .wine/dosdevices which tell wine what to use as C: and D: and other such drives when windows applications are looking for stuff.
I'll read through the thread and see if I can figure it out.

---

### Post by broekskw on 2006-12-02
great thanks allot man;) i will keep trying and reading also, trying to switch from xp to ubunto will have to go threw some learning curves 
thanks man again :cool:

---

### Post by broekskw on 2006-12-02
ok now what have i don, can not detect my cdrom drive. i have a cdrom drive in my file system but every time i try to open this it is blank, nothing in it, but i do have the game in my cdrom, not showing???? ](*,) ](*,) ](*,)

---

### Post by Shatrat on 2006-12-02
You might want to go into your winecfg and in the drives tab click the autodetect button.  This should set up all your drives including your cdrom properly.
also, apparently wine is supposed to run in windows 98 compatiblity mode for C&C, but it seems thats for ra95.exe after you've got it installed.  You might want to just try changing the default version of windows from XP to windows 98 and try it.

---

### Post by broekskw on 2006-12-02
thanks did go into winecfg and did auto detect and then installed starcraft with no problem, except can not find my c: drive and program folder to put a starcraft icon on my desk top, also after installing this game i ran game but the creddn was a box in the center of my screen,could not make it got to full screen must be very simple to make it the full screen??
ok i do understand that c&c is a ra95.exe file and in winecfg i have selected win98 before i try to install this game but can not install, so should i go back to win95 in winecfg or xp and then try again??:mrgreen:

---

### Post by broekskw on 2006-12-02
in winecfg, after you make a change what is the command or how do you save and exit,keep switching to win2000 or xp or win95 and then close out and then come back in and it's back to win98???

---

