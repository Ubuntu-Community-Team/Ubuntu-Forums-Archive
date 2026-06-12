---
title: "running windows only programs"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by chach man on 2007-01-07
Ok so ive got an ubuntu box setup now i want to run some "windows only" programs (right now primarly worms armagedon) ive looked at winex, and cedega but as far as i can tell i have to buy both of them and since this is just for me to play with on a computer i threw together id much rather not pay for them.

ive looked at vmware but for space reasons i dont want to have to install windows ontop of ubuntu ....(i will when i get the money and build a TIVO). is there an all linux solution

if not can i get a link to the best walk through

---

### Post by tuxcantfly on 2007-01-07
wine is what you want

winehq.org

---

### Post by tuxcantfly on 2007-01-07
walkthrough here:

[http://appdb.winehq.org/appview.php?iVersionId=1744](http://appdb.winehq.org/appview.php?iVersionId=1744)

---

### Post by tuxcantfly on 2007-01-07
as for installing wine, see here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by chach man on 2007-01-07
ok i was on that site before i found the link this time i downloaded it and all i got a dependencey error i went in and updated wine in symnptic . then went to install the file i just downloaded it told me there is already a newer version running i went into termanl and got

chach@chachman:~$ wine wa.exe
wine: creating configuration directory '/home/chach/.wine'...
Failed to open the service control manager.
wine: '/home/chach/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\wa.exe": Module not found

is what i updated in symntic the same thing as what i downloaded. and what did i do wrong

worms was installed on an windows xp machine so i coppied the floder over to a usb thumb drive then onto the desktop of the ubuntu machine but it since it isnt getting started with the program i dont think thats the problem

---

### Post by jem7v on 2007-01-07
I'm not sure what to do to get Wine working in the first place (because it has always hated me), but once it is...

To use a windows program in Wine you'll actually have to *install* it in Wine. I wish you could just read installed programs off your old hard drive, but you can't.  To install it in Wine?  Um, you pretty much run the installer through wine (the syntax for which is probably something like: wine [installerfilename] ) and THEN you can try to run it in wine.  And you probably have to put the installation files some place that Wine can find them, which is probably somewhere inside your ~/.wine folder (wherein resides a mock Windows installation).

So I can't give you many details about what you'll be doing, but at least I can tell you the steps you'll have to take! I just can't explain How to do them.

---

### Post by chach man on 2007-01-07
ok i just downloaded winamp and ran the setup file everything worked there i got a bad sound driver but whatever ill figure that out later but im betting i just need to get the disk off my bro. thanx

---

### Post by chach man on 2007-01-07
ok i tested winamp it looks fine under applications>wine  it shows up 
now i tried to install a program off of a disk specificly for windows 95 i did winecfg changed it to windows 95 first off will i need to change that each time i want to run the program (I'm assuming i will)

next the file doesnt apear under applications>wine would it for some reason appear somewhere else

---

### Post by jem7v on 2007-01-07
Well, I think the Win95 program would Probably still run under "different versions" of Windows, but if it's really fussy it might not.  Regardless, I think there's a setting somewhere in winecfg that you can use to set what "version" of "Windows" each program uses when you run it.  I seem to remember something like that, back when I was trying to use it.

---

### Post by houstonbofh on 2007-01-07
First, this is not a Wine support forum, so information may be limited.  Try WineHQ for better info if you get stuck.

Second, what version of Wine?  Are you using the Wine repositories at Budget Dedicated?  If not, do so.  The Ubuntu version is way behind. [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

You can set version based on application.  Try reading [http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index) as there is A LOT of stuff Wine can do.

Last, what program?  To load a program you have to do a thing.  Without specifying, that is as good as it gets.

---

### Post by chach man on 2007-01-07
yea i know its not a wine forum (is there one) i really appriciate the help. 

i went into winecfg and looked around on the "c:" theres a folder called westwood and then red alert and theres some .exe files in there but i cant get any of them to run. (im trying to get command and conqure red alert to work) so i think its installed.   

i am reading through that link thanks

---

### Post by houstonbofh on 2007-01-08
Not a real forum, but they do have [http://groups.google.com/group/comp.emulators.ms-windows.wine](http://groups.google.com/group/comp.emulators.ms-windows.wine) and [http://www.winehq.com/site/irc](http://www.winehq.com/site/irc) for support.

Also, you never said what version you are running.

---

### Post by chach man on 2007-01-08
its version 0.9.28

---

### Post by houstonbofh on 2007-01-14
> **chach man said:**
> its version 0.9.28
This was the latest version 5 days ago. :)  It is at 0.9.29 now...  Anyway, you will probably have to do some special things to get these programs going.  Usually it means adding DLLs.  I would search the gaming forum for these games by name.  If you don't find them, ask there.  Also google for the name of the game and wine.

---

### Post by chach man on 2007-01-14
alright sounds great i'm making headway... i think i am anyway

---

