---
title: "Wine cannot find MS apps (HELP!!!)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by rqbook on 2007-01-21
Hi,
I am new to ubuntu. Today, after successfully installed wine-0.9.29 on ubuntu 6.10, when I typed "wine C:\\Program\ Files\CDE\CDE.exe", the terminal always showed "wine: cannot find 'c:\program files\cde\cde.exe'. 
When I try another, wine "C:\Program Files\\Macmillan\\English Dictionary -Am\EAA001MA.exe", the same condition happened again, wine cannot find that .exe
Worse, I cannot MS Internet Explorer 6.0sp2 by wine on linux.

However, when I lauched Microsoft WindowsXP notepad via "wine notepad", it DID work, the MS notepad showed up without any problem.

Can anyone tell me what's wrong with wine???
Thanks a lot!!!

---

### Post by Shatrat on 2007-01-21
Have you tried "wine /home/yourname/.wine/drive_c/Program\ Files/CDE/CDE.exe"?
Are you sure you have this stuff installed on your wine virtual drive?

---

### Post by rqbook on 2007-01-21
Thx for ur fast reply,
but i don's know what you meant. do i have to install something to let my MS apps work? how to do it??? why MS notepad doesn't need some stuff? The wine manual said wine "path name\\appname.exe" will launch MS apps.

Thx a lot

---

### Post by iver2435 on 2007-01-21
Just like in "real" Windows, before you can run a program in Wine, you have to install it.

So, you could just have to install the app you're trying to run first, and then it will work fine.  

I also agree with Shatrat about trying the .wine directory under your home folder....

---

### Post by oilchangeguy on 2007-01-21
i'm guessing you're dual booting right? other than the dictionary program and IE, what else do you need? there is dictionary software available in ubuntu in several languages. and why would you need access to IE in linux?? firefox is already loaded and works great on 99.9% of the websites out there. if you're trying to run windows apps on linux you might as well stay with windows, and forget about linux.

---

### Post by rqbook on 2007-01-21
yes, i have dual-boot system( MS + Linux ). I need to run electronic English dictionaries( such as Macmillan, Cambridge, Oxford etc ) for MS on Linux since Linux free dictionaries are poor and without sound. 

Can someone explain in detail how I can resolve my problem? 
How to install "wine /home/yourname/.wine/drive_c/Program\ Files/CDE/CDE.exe"???
Sorry, Its my 1st time trying linux 2 days ago.

Thx a lot.

---

### Post by oilchangeguy on 2007-01-21
not sure if this is available for ubuntu (it is for xandros linux) and that's a program called crossover. this program will let you run just about any program written for windows. it's free with some of the paid xandros versions, and a 30 day trial is included with the open source version.

---

### Post by jvc26 on 2007-01-21
Hi there just a few thoughts:

Dictionaries aside, you dont need IE for linux (as you already have Firefox, which in many ways you should use on windows anyway (as oilchangeguy said) and you dont need ms notepad as:
1/ Linux already has a good solution, in the form of gedit, which also does syntax highlighting (should you be a programmer)
2/ In terms of windows use notepad is also inadequate as you dont get syntax highlighting (to my knowledge) so I'd use notepad++ anyway (or one of the other open source alternatives)

Not every application will work in wine, that is a definite case. It may well just be that your dictionary apps are not working because they can't - do the dictionary companies out there not produce linux versions of the dictionaries? If they don;t your next options are crossover office ( a proprietary app to allow you to run most windows apps in linux) You may just find alas that you can't get them to work as they just arent designed for linux systems.

Il

---

### Post by rqbook on 2007-01-21
execuse me, you might misunderstand my point. i dont need IE, notepad, other MS apps except commercial english dictionaries such as macmillan, collins, oxford, cambridge. 

my point is that the wine doc said after installed wine, i can run MS apps via a single command: wine "C:\Program Files\....\app.exe".  For example, typing wine "c:\program files\microsoft office\office11\excel.exe" will run MS Excel and wine official website did show such a screeshot for running MS Excel by wine on Linux. 

My concern and question is that why "wine always cannot find my app.exe". except notepad, wine cannot find IE and all MS apps. What I have to do to launch MS app by wine??? What command? setup? configuration setting or anything else???

PLEASE tell me in detail about my question, Many thanks for all ur help.

---

### Post by machoo02 on 2007-01-22
Hi...I think that I understand your post, as did a few of the posters above.  Wine can be confusing to new users.  You cannot run the programs that you have already installed on your Windows partition directly in Wine; that is not how Wine works.  Wine cannot find them because, in the way that Wine is set up, you do not have them installed.  Wine comes with its own version of notepad, so when you typed in "wine notepad" you saw Wine's version, not MS's version.  Try typing in the line you posted earlier to open up Excel...it should give you the same error message.  In order to use Window's programs with Wine, you will need to install them into Wine.

Ok, let's try to get your program working.  Do you still have the cd's for your dictionary programs?  If so, pop one of them into your cd drive.  When the window pops up asking you what you want to do, select 'open in a new window'.  This will open up a window with the contents of the cd.  Look for the installer program, probably called 'setup.exe' or something similar.  Open up a terminal and enter ```
cd /media/cdrom
ls
```The same installer program should be listed.  Next, enter ```
wine setup.exe
``` replacing 'setup.exe' with whatever the installer is.  This should start installing the program within Wine's virtual C: drive.  When it is finished, try starting the program through the terminal by ```
wine /home/username/.wine/drive_c/path_to/your_app/your_app.exe
```replacing username with your username, and /path_to/your_app/ with where you installed the application to.

Don't get discouraged...sometimes it takes a little bit of work to get programs running smoothly in Wine.  Don't forget to check out [http://appdb.winehq.org]("http://appdb.winehq.org"), which is a database of applications that are know to work/not work with Wine, as well as tips and tricks for getting applications working.  I hope this helps!

---

### Post by Lexyboy on 2007-01-22
Are you trying to run programs installed on your Windows partition?  In this case using "C:\blah" won't work as "C:" refers to the wine virtual drive.  Assuming your Windows partition is mounted (as hda1), you could try

> wine "/media/hda1/Program Files/program_name/program.exe"

Though not sure this would work for everything - just quickly tried it and it worked for me, but if your programs depend on other files on the windows partition then they might not work.  Best to install fresh using wine from the off.

---

