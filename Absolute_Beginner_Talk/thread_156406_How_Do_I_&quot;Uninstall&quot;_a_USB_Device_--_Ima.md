---
title: "How Do I &quot;Uninstall&quot; a USB Device -- Imation Disc Stakka?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-04-07
I have a USB device attached to my computer -- specifically an Imation Disc Stakka.  This device stores (does not read or write) 100 CDs/DVDs in a carousel hardware device.  A database keeps track of the discs and ejects them, selects them for return, and adds new discs through software that comes with the device.  It has no independent power supply other than the USB port.  I have no ability to simply unplug it every time I boot into Ubuntu.  When I do boot into Ubuntu this device will mechanically "cycle" during the entire time that Ubuntu is running.  I need a way to "kill" the process that is causing this.  Ideally, of course, I would like to automate the process so that when I boot into Ubuntu session I will not have any problems with this particular USB device.  However, in the short run I will settle for merely identifying what needs to be killed, shut down, or otherwise disabled through Ubuntu AMD 64 Breezy Badger 5.10.  Any advice, links, etc. will be greatly appreciated.  Until I complete this fix my ability to independently boot into and out of Ubuntu is virtually nil.  Thanks in advance for any responses.  -- Gene

---

### Post by catlett on 2006-04-07
This is a "crude" way but it should stop it from cycling while your in Ubuntu. This is like going into Task Mnager in Windows. I'm using the testing version Dapper Drake. The menu shoud be the same as I'm about to describe even if you are on 5.10 Breezy.
Go to the panel up top. Click on "Syatem". Scroll to "Administration". Box slides out. Scroll to "System Monitor". Click on it. Up will come the system monitor.
Click on the tab "Processes" (it shiuld by default be on processes). Scroll down to the process that is running the cycle. If you can't tell by description you can usually tell by the resources it is using. Most entries will say "sleeping". The "cycling" process should stick out. 
On the bottom right is a box "End Process". Click on the box and it will stop the process you have highlighted. This is just like ending a process with the Task Mnager under Windows.
This should work until you find a way to disable the process on starup. Regards, Catlett

---

### Post by da5id on 2006-04-07
I have tried that.  It doesn't work for me because even though the system monitor works similar to Windows Task Manager, suprisingly *all *processes are sleeping except system monitor itself.  I tried to kill everything with "USB" in its path/name and other likely suspects-- no luck.   I see no indication that a particular process is actually "killed" or disabled after I "End Process," rt-clk and explicitly "kill, etc.  I assumee I am actually doing something because I must enter my password to complete each action (chinging my password timeout is in my to do list.)  It (whatever I killed) still appears in the system monitor processes list.  There are no visual cues or other information that I can discern to show that a particular process has been killed or disabled.

Brought to you involuntarily by Windows. -- Gene

---

### Post by catlett on 2006-04-08
This thread looks like they have found a way to stop processes not involving the system monitor.[http://ubuntuforums.org/showthread.php?t=155798](http://ubuntuforums.org/showthread.php?t=155798)

---

### Post by da5id on 2006-04-08
There is no process to kill.  But:

"Hi Gene!

I'm glad to say that there is a simple solution :)

The basic problem is this: Once the Disc Stakka (DS, or just Stakka
from now on) has been acknowledged by the system it expects to be
polled ever so often (I think its 200ms from when it tells the OS its
'ready') So, when it doesn't get polled it believes that the OS must
have forgotten about it, and therefore resets. Quite annoying!

However, if you download and install my DS controller from sourceforge
this should fix the problem by talking to it when it needs to be
talked to. You will be able to grab a copy here.

[http://sourceforge.net/projects/disc-stakka-ctl](http://sourceforge.net/projects/disc-stakka-ctl)

You will need to build it yourself, but this shouldn't prove too much
of a problem (usually just a ./configure; make; make install - the
last part needs to be done as root)

AND

Ahh! Cool. Well in that case do an

apt-get install g++

and install most of the 'suggested' packages (particularly make). Then
just try running the commands in a terminal.

Oh...and you might need libusb. Do an apt-get search libusb to find
out which 'dev' package you should grab (probably libusb0-dev or
something like that...)

Hope that helps :)

Eddie
- Show quoted text -


/But, this is less than 'easy' for me ;-) -- see att'd.  Forgot, not in Gmail...no attatchments D-:

---

### Post by nanotube on 2006-04-09
[QUOTE=da5id]

apt-get install g++

and install most of the 'suggested' packages (particularly make). Then
just try running the commands in a terminal.

Oh...and you might need libusb. Do an apt-get search libusb to find
out which 'dev' package you should grab (probably libusb0-dev or
something like that...)

Hope that helps :)

Eddie
- Show quoted text -
[/QUOTE]

by the way, on ubuntu, you should just "apt-get install build-essential", and that would install the compiler, and make, and all the other tools - instead of doing them one by one. :)

---

### Post by da5id on 2006-04-09
Is a picture worth 1000 words:

[http://www.putfile.com/da5idubu](http://www.putfile.com/da5idubu)

---

### Post by da5id on 2006-04-09
The results are under nanotube:

[http://www.putfile.com/da5idubu](http://www.putfile.com/da5idubu)

-Gene

---

### Post by nanotube on 2006-04-09
hi
i guess we should have been clearer - you have to run apt-get with sudo. as follows:
```
sudo apt-get install build-essential
```
when it asks for your password, enter your user password.
try that again. :)

---

### Post by da5id on 2006-04-09
OK  That worked perfectly.  I DL the Stakka controller to my desktop, extracted and read this readme excerpt:

"Need to copy files in hotplug dir to /etc/hotplug/usb"

hotplug dir has no usb dir just 2 usb script and a usb text file.

But,* hotplug.d* has an empty usb *dir* -- works for me, but I can't paste into it -- paste grayed out.  Sounds like a rights/permissions issue -- sudo?  If so, how?

?sudo copy [biglongfilepathsourcename] [biglongfilepathdestinationname]?

For each file? -- just 2, tho.

When I finish that I still gotta 

"You will need to build it yourself, [COLOR=Red]but this shouldn't prove too much
of a problem [/COLOR][LOL!](usually just a ./configure; make; make install - the
last part needs to be done as root)"

Is this doable. ie, does it even make sense to you?

I'm reading your Ubuntu Wiki -- sudo .configure man gave me nada

-g

PS amaroK is *so* cool, makes MS Media Player look like crippled adware!

---

### Post by nanotube on 2006-04-09
[QUOTE=da5id]
?sudo copy [biglongfilepathsourcename] [biglongfilepathdestinationname]?

For each file? -- just 2, tho.[/quote]

yes, you have the right idea - only instead of "copy" the command is "cp".
alternatively, you can just launch a file browser as root (with "sudo nautilus"), and then you can use the gui to copy the files to your destination.

> When I finish that I still gotta 

"You will need to build it yourself, but this shouldn't prove too much
of a problem (usually just a ./configure; make; make install - the
last part needs to be done as root)"

Is this doable. ie, does it even make sense to you?

yes, that's the standard way to build stuff from source. but before you do that, you have to install the "build-essential" package, because that contains make, and the compilers, etc. to do that, use "sudo apt-get install build-essential".
once you have that, go to the directory where you put your sources, and run "./configure" then "make" and then "sudo make install". that should take care of it for you.

i dont know anything about the specifics of the software you want to install, but that's the general procedure for installing stuff from source. :)

---

### Post by da5id on 2006-04-09
yes, that's the standard way to build stuff from source. but before you do that, you have to install the "build-essential" package, because that contains make, and the compilers, etc. to do that, use "sudo apt-get install build-essential".


That went flawleslly, next I'll follow copy intructions. -g

---

### Post by da5id on 2006-04-09
"once you have that, go to the directory where you put your sources, and run "./configure" then "make" and then "sudo make install". that should take care of it for you."

OK, I think I'm almost there.  On my desktop is my source folder with folderss and files inside.  Only 2 seem relevant now.

src folder -- inside it is a "client" folder with 2 Python script files inside and a "server" folder with 4 C and C++ files

Makefile -- a kind of text file (code?)

Should I move these somewhere "permament," if so, where?

In terminaldo I type "./configure [what?]" ?

ditto for make and make install?

Thx -- g

---

### Post by nanotube on 2006-04-09
./configure, make, and make install do not require any further arguments, generally.

---

### Post by da5id on 2006-04-09
[QUOTE=nanotube]./configure, make, and make install do not require any further arguments, generally.[/QUOTE]

Responds "no such dir."  You can see it -- named correctly.  Any ideas?  Actually, I did a file search and failed to find configure.  Also terminal respons no file.

-Gene

---

### Post by Xzallion on 2006-04-09
That pic in your last post shows that you are currently in your home directory, but the Files are on your desktop.  change directory to your desktop
( cd dekstop ) 
and then change the directory to the folder the files are in (cd disk-stakka-ctl-0.04 )

do a dir and see if the files are there.  If they show, go ahead with hte ./configure, make, and make-install commands.

Good Luck!

---

### Post by da5id on 2006-04-10
[QUOTE=Xzallion]That pic in your last post shows that you are currently in your home directory, but the Files are on your desktop.  change directory to your desktop
( cd dekstop ) 
and then change the directory to the folder the files are in (cd disk-stakka-ctl-0.04 )

do a dir and see if the files are there.  If they show, go ahead with hte ./configure, make, and make-install commands.

Good Luck![/QUOTE]

I figured that out.  So, in the interest of comprehensiveness, I used the CD command about 50 (of course, *in different *places) times to run ./configure -- I always came up with the cryptic response of file or directory not found.  I began to suspect whether or not I even have they necessary tools  installed in my version of Ubuntu, i.e., whether there is a ./configure in my filesystem.  Of course after a lengthy search using different methods I finaIy got a prompt that said that a  / is never utilized in a file name.  Once I got this prompt, it made sense to me because a / is not used in in a filename (path, yes, of course, but not name) in DOS, Windows, or any other filesystem I have ever encountered.  I am also suspicious because in terminal when I entered "configure man" it basically said  bad command, no manual.  In other words, at least 3-4  people have addressed the issue of ./configure and never hinted that that wasn't real filename or suggested that I might want to try to figure out what the  ./ meant.  This confusion is infuriatingly included in the official documentation (or, more properly, the lack thereof) to Ubuntu which I'll get to in a moment -- oh yeah, RTFM lazy Windows user.Well, I can always look at the documentation right?

[https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall#head-755560985cee357ccfc7fa2092160a6a550930ca](https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall#head-755560985cee357ccfc7fa2092160a6a550930ca)

Reading this entire thread, can you honestly say that this link is of any use whatsoever?

This may have turned into a rant and I am frustrated but I never give up.  Even if I have to start new threads breaking down the issues into one simple question at a time, kind of like speaking to a five-year old.

-- Gene

If it is a Windows problem, it's gotta be the buggy software.  If it's a Linux problem, it's gotta be the lazy user.-- The Consensus Software Group

---

### Post by nanotube on 2006-04-10
hey
the ./ simply means "look for this file in the current directory". it is not part of the filename. so ./configure means, look for a file named "configure" in the current directory, and execute it.
that's why we have been telling you to cd to the directory where you extracted your tar.gz file - the relevant configure file should be located there. once you are there, issuing "./configure" tells the command line to execute the configure file that is in your current dir.
that link you posted to the ubuntu wiki - it's ok, but it skips over a lot of detail. 
since you appear to be having trouble with basic command line stuff, i would encourage you to read some tutorials on using the command line, first, before you continue playing with this. 
a couple of guides i would recommend to you are the following:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

p.s. hmm, of course it is possible that the file you are trying to install just doesnt have a configure script in it. could you post the link to the software you are trying to install - i can take a look at it myself. 

p.p.s. to get a manual page, the command is "man mycommand", not "mycommand man". but at any rate, since configure is not a system command, but just a script supplied with a source software distribution, it will not have a man page, even if you type "man configure". 

p.p.p.s. really, go through some of those basic linux commandline guides - you will be happy you did. :)

---

### Post by da5id on 2006-04-10
Nano,

I would appreciate it if you would take a look at the files.  This is the link that the developer e-mailed me and the archive that I downloaded.

[http://sourceforge.net/projects/disc-stakka-ctl](http://sourceforge.net/projects/disc-stakka-ctl)

I certainly do want to spin my wheels if something is fundamentally wrong with the source code?  Package?

I will spend some time reading the links that you have suggested before going further.

Thank you for your assistance.  -- Gene

---

### Post by nanotube on 2006-04-10
heh well, i took a look at the distributed source archive, and **there is no configure script**! 
so apparently, you are just supposed to do a "make" and "sudo make install"
no wonder configure would not run - it was not there. :)
of course, had you read your command line lessons before, you would have known to look in the directory to see whether it was there, and avoided the whole problem. ;)

so try cd to the directory where you unzip, and do the two make commands, and see what happens. post your results here.

---

### Post by da5id on 2006-04-11
Nano,

Thanks so much for the links.  The lights came on and my irritation ebbed away as I worked on the bash tutorials.  They *really* should be in the first sticky.  I consider myself OK in finding stuff w/ google, etc., but my first hits were admin tech guides.  I thought "Great, incomprehensible documentation too."  

Re "so try cd to the directory where you unzip, and do the two make commands, and see what happens. post your results here."  There are several dirs and subdirs in the top dir.  Just run the commands on/in top dir and they will drill down to find what they need?  I'll try everthing and post back here.  The developer gets back from holiday next week and said he'd help me when he got back -- if I get stuck, I'll just wait untill he returns.  I figure about 80% of what I do on my PC can be done in Ubuntu and I already prefer it to MS.  Again, thx for links; sorry about the rant.

-G

---

### Post by nanotube on 2006-04-11
hey
yes, as you can see in the top dir, there is a file called "Makefile". this file tells make what to do. so no need to drill down into the subdirs - do the "make"s in the main dir of the package. :)
getting help from the developer sounds like a good idea, too :)
good luck.

---

### Post by da5id on 2006-04-11
[QUOTE=nanotube]hey
yes, as you can see in the top dir, there is a file called "Makefile". this file tells make what to do. so no need to drill down into the subdirs - do the "make"s in the main dir of the package. :)
getting help from the developer sounds like a good idea, too :)
good luck.[/QUOTE]

Nano, the good news, it "made" -- the bad news, all errors.  Term txt file att. /G](*,)

---

### Post by nanotube on 2006-04-11
[QUOTE=da5id]Nano, the good news, it "made" -- the bad news, all errors.  Term txt file att. /G](*,)[/QUOTE]

hi, took a look at your error output.
looks like you dont have libusb. do you remember, in the readme file, it said "you need libusb". so... you have to go to Synaptic, and install libusb first, before you attempt to "make" :)

when you go to synaptic, and search for 'libusb' by name, you will get 4 packages. the one called "libusb-0.1-4" should already be installed. since the server there is made in c++, my guess is that the one you need is "libusb++-dev". install that one, then try the "make" again. (if that still fails, then try installing "libusb-dev" as well, and then try again. but it shouldn't fail, i think.)

p.s.
in your terminal, i noticed that from your home directory, you tried to "cd /Desktop" (which, of course, failed). so, a point on shell syntax for you. 

starting a path name with "/", means, look for this is the root of the drive. what you wanted to do, is "cd ./Desktop" - starting a path with "./" means, look for this in the current directory. its all about the subtle difference of one dot. :) i guess you didn't get to that yet in your shell lessons? ;)

---

### Post by nanotube on 2006-04-12
oh, and by the way
once you compile it with "make", instead of using "make install" command, i would recommend you use "checkinstall".
checkinstall registers all the installed files with the apt system, so you can uninstall stuff later, using sytaptic or apt-get. to get checkinstall, just install the "checkinstall" package with synaptic. 

and of course, don't forget to put "sudo" in front of "checkinstall" or "make install", whichever you decide to use.

---

### Post by da5id on 2006-04-12
[QUOTE=nanotube]oh, and by the way
once you compile it with "make", instead of using "make install" command, i would recommend you use "checkinstall".
checkinstall registers all the installed files with the apt system, so you can uninstall stuff later, using sytaptic or apt-get. to get checkinstall, just install the "checkinstall" package with synaptic. 

and of course, don't forget to put "sudo" in front of "checkinstall" or "make install", whichever you decide to use.[/QUOTE]

Nano,

I installed the development kit you suggested.  When I clicked on install a dialogue came up and said, basically, if you are going to install this then you need these are the two things and checked those.  Additionally, I checked the box regarding Python scripts since I saw those in the package.  I took a screenshot, unfortunately before and not after it showed the box's checked.  In any event, they seem to install without a problem.

However, after make, makeinstall just put up errors.  Moreover, checkinstall did not work -- bad command.  Have attached a screenshot of Synaptic and a textile of my terminal.  You will notice some more trial in their CD commands -- I did read the tutorial regarding how to navigate through the filesystem, but there are still lots of errors on my part.  I'm not really worried about that, I learn by trial and error.

Unless something [COLOR="Red"]jumps out at you[/COLOR], I'm going to put this aside until the developer gets back from holiday.  I'm not even sure after it installs what to do, unless it "magically" resolves the device's cycling problems just by itself.  I think the author said that it would, at least, do that.

As you can imagine, I have lots more stuff to do to make Ubuntu my Ubuntu.  I think I want to put this aside and work on some of the other issues.  Since Ubuntu is running more hours of the day now and Windows I have just unplug the offending device.  That works for me for a short while.  Thank you for your perseverance in this tedious matter.  I'll drop you a line next week after I, hopefully, receive some enlightenment from the author of this program.

My next project is porting my Microsoft Reader .lit e-book files to Ubuntu.  I understand it can be done and I have downloaded the conversion package, rather humorously titled "clit" -- you probably saw that on my desktop.  This package has a date of approximately 2002 so I am hoping it is more mature and installs with less problems then this Stakka program.  While certainly instructive, I must say that I would much rather install programs that are already in the Ubuntu repository, e.g., amaroK:)

-- Gene

---

### Post by nanotube on 2006-04-12
well, it looks like your make and make install (yea, you had to do the install with sudo) actually worked.
it did say "client not copied", but the client is just the python file, and not the stuff that has to be "installed" anyway.
so, you should try starting the server, and try running the .py client file... but that's getting into the specifics of the software, and i guess you better wait for the developer. :)

also, as to checkinstall - remember, i said that checkinstall also has to be installed from synaptic (just like you installed libusb stuff). otherwise it is not present on your system. but it's irrelevant now, since the plain "make install" already did its job.

yea, good luck, and post what happens if you have any success. :)

---

### Post by Ingo88 on 2007-04-29
Hi!

I recently bought a Disc Stakka and noticed its annoying behaviour under Ubuntu. Luckily I found this thread, and have now downloaded and installed dsControl. However, when I try running it I just get a bunch of errors. I have attached the log created with dsControl -l.

Thanks in advance :D

---

