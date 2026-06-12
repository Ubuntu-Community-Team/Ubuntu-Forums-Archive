---
title: "wine questions"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by ecstatic on 2006-02-24
Ok, I've had Ubuntu on my system for a little while now and just installed wine about a week ago.  I removed C: drive from there for some reason (some stupid reason) and figured I could always add it later.  Now I can't.  I click on Autodetect and it comes up with a C: drive, but it never stays whenever I close Wine.  I click Apply and Ok and when I start winecfg in the Terminal and click on Drives, a popup message tells me that there is no C: drive available.  It does the same thing with audio when I click on Apply to install an audio driver, it's not recognized next time I start winecfg.
Why does this happen and is there any way to remedy the audio?  Do I need the C drive?
The current drives now are D, E, F, G, and H.  
I guess my other question is: how do I run a program using wine now?  Perhaps my problem is because I do not have a C: drive.  I downloaded an application, firstclass, and now I don't know how to run it with wine.  I downloaded it to the C: drive also before I removed it.  I'm all screwed up, new to Linux and Wine, and cannot find answers for any of my questions anywhere.
Any help at all would be appreciated.  Thanks.

---

### Post by xhie on 2006-02-25
Well when you install something with wine it puts it in a c drive that it creates in .wine/drive_c/  and it installs to .wine/drive_c/Program\ Files/  
As far as running stuff with wine goes, wine appname always works. 

Other then that you have some sort of problem mounting another hard drive you previously removed, is that it?

---

### Post by ecstatic on 2006-02-25
Sorry about not explaining myself fully.  
Yes, I have a problem not being able to mount my c: drive again once I removed it.
I realized that wine downloads programs to the c: drive, but exactly where would that be in Ubuntu if I'm looking for it?  What exactly is the path location to find the files?
I have one hard drive, but two partitions.  One with Windows XP installed and the other with Ubuntu.  The Windows partition has the NTFS format.
I ran diskmounter through the terminal, I had read this on another forum, to check for my drives.  Now, I have a CDROM drive, a Floppy, an hda1, and an hda5.  The hda1 drive looks to be my Windows XP drive.  Now, is this my c: drive that I removed and when I remounted it Ubuntu changed the label to hda1?  
And on a side note, could somebody explain to me exactly how I can copy an executable file over from my Windows drive to my Ubuntu drive and run it with wine?  I copied over a program and Ubuntu placed a lock icon on it and I can't seem to access the folder through the terminal whatsoever.

I'm confused, as you can all tell.  Help me?
I've read all the posts and documentation from wine hq that I can find and nothing seems to explain things to a newb Ubuntu/Linux user at all.

---

### Post by bluevoodoo1 on 2006-02-25
[QUOTE=ecstatic]I realized that wine downloads programs to the c: drive, but exactly where would that be in Ubuntu if I'm looking for it?  What exactly is the path location to find the files?[/QUOTE]

As xhie says "Well when you install something with wine it puts it in a c drive that it creates in .wine/drive_c/" 
This "c drive" (which is just a folder) is like a virtual drive rather than a physical drive. It should be in your .wine folder (.wine is a hidden folder in your home directory. Hit Ctrl+h to see it within nautilus). 

You should not have to do anything with your Ubuntu drives (hda, hda1, hdb etc.). I've never had to do anything like that. 

Copying things over from your Windows drive... you will first have to mount your windows drive. See here for mounting windows partition (first question) [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by ecstatic on 2006-02-25
Ahhh, perfect voodoo, thank you.  I did not realize that the .wine folder was hidden in my Home folder.  Odd why it would be installed this way in Ubuntu.  Doesn't seem to make sense why a folder that you would use often and is not pertinent to your system, be hidden.  Ahhh, well, I found it and that's what matters.
It's odd that the drive_c folder is there but when I run winecfg through Terminal, the drive_c doesn't show up under my Drives tab.
Also, when I run wine (Program name), all I get is this:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

Warning: could not find DOS drive for current working directory '/home', starting in the Windows directory.
wine: cannot open (null)

Now, I see the Firstclass folder in drive_c and it has within it the fcc32.exe program, yet when I go to 'wine fcc32.exe" in the Terminal, the above is what is displayed.
Perhaps it's too early in my Linux experience for me to be toying around with Wine.  I would really love to have some Windows programs up and running under Ubuntu so I could reside on my Ubuntu drive more often than my Windows.  It's fun to learn and play around with Ubuntu, but it seems that you're not able to do as much with the GUI aspect of Ubuntu and must rely mostly on the Terminal and its commands to get around.  And to somebody who is not familiar using just command line instructions, it's somewhat daunting.  Not to mention frustrating, as much fun as it is to learn.

---

### Post by ecstatic on 2006-02-25
Ok, in my .wine folder, under dosdevices, I have d: e: f: g: and h: drive folders that are working correctly, but I also have c: folder, but under Type it says link (broken).  So I'm guessing this is a problem??  Of course, but how do I remedy this?  It isn't a matter of unmounting and then remounting is it?
I searched through a number of posts somewhere else and came across one where somebody said you have to remove the folder and replace it with a new one.  Is this what I need to do?  And if you could tell me exactly how I do that, it would be great.
Thanks!

---

### Post by bluevoodoo1 on 2006-02-25
[QUOTE=ecstatic]Ok, in my .wine folder, under dosdevices, I have d: e: f: g: and h: drive folders that are working correctly, but I also have c: folder, but under Type it says link (broken).  So I'm guessing this is a problem??  Of course, but how do I remedy this?  It isn't a matter of unmounting and then remounting is it?
I searched through a number of posts somewhere else and came across one where somebody said you have to remove the folder and replace it with a new one.  Is this what I need to do?  And if you could tell me exactly how I do that, it would be great.
Thanks![/QUOTE]

Nope no mounting. There should also be a "drive_c" folder in your .wine folder too.  Did you install wine with Synaptic? If you did you could mark it for complete removal, then 
```

rm -rf $HOME/.wine
``` which will remove your entire .wine folder (everything in your .wine folder will be gone). Then install wine again. Perhaps that will remedy your "lost" c drive.

(By the way, you can learn how to get the latest version of wine with Synaptic here... [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb))

hope that helped.

---

### Post by BeatBoxRocker on 2006-02-25
First of all you should run wincecfg, then select the tab on the left next to Audio (i dont know what its name in english) and then use AutoDetect. This will help you to create the folders that you need in your system with the devices you already have in your pc (like cd rom drives for games).

Saludos!

---

### Post by ecstatic on 2006-02-25
Ok bluevoodoo, thanks!  I don't know why I didn't think to do that myself, but I guess that's why the community is here.  I reinstalled wine and now I don't have any errors when I run winecfg.  Wine is now installed in my usr/bin directory.
Now, can I run a .exe program from anywhere on my system using wine or do I have to have the program residing on drive_c?  I've tried double clicking on a number of .exe programs in my Home folder and it just tells me that I cannot open them.  
However, I use the Terminal, go to the path where the .exe resides and run wine [program name] and the program starts (I'm trying to use the FirstClass client, fcc32.exe).  But I don't see anything after the startup screen.  There's no login screen or anything, it just shuts down seems like, but the Terminal doesn't quit out and I can't type any new commands for it to execute.
Now, is this perhaps because I went into my Windows XP partition and ran Wine from that program file directory?  I didn't actually install it in Ubuntu, so I thought maybe there were some registry changes or something that are initially installed on the system and this is what I'm missing on my Ubuntu partition.
Also, what is this winesys icon in the upper corner of my desktop about?  I can't seem to interact with it whatsoever except to move it around.
Slowly but surely, I'm still pushing on with this.  I thought I would have given up a long time ago with Wine.

---

### Post by bluevoodoo1 on 2006-02-25
[QUOTE=ecstatic]
Now, can I run a .exe program from anywhere on my system using wine or do I have to have the program residing on drive_c?  I've tried double clicking on a number of .exe programs in my Home folder and it just tells me that I cannot open them.  [/quote]

That shoud be fine. If you have an .exe file in your home folder, when it's installed it should install to your drive_c folder. If you click on something and it doesn't work.. right click and select 'open with' select wine (if it's there). If it's not, there should be a command at the bottom of the screen (I'm not on gnome now so I remember the exact name)... but it will let you do a custom command, simply type 'wine'

> 
However, I use the Terminal, go to the path where the .exe resides and run wine [program name] and the program starts (I'm trying to use the FirstClass client, fcc32.exe).  But I don't see anything after the startup screen.  There's no login screen or anything, it just shuts down seems like, but the Terminal doesn't quit out and I can't type any new commands for it to execute.

try adding an ampersand to the end of the command.
```

wine fcc32.exe &
```

You can do that with most application commands... "firefox &," "gaim &" etc. etc. "sudo synaptic &" won't work, but "gksudo synaptic &" will work. That will let you open a program yet still work from that terminal. 

> 
Also, what is this winesys icon in the upper corner of my desktop about?  I can't seem to interact with it whatsoever except to move it around.

hmmm I'm not sure about the icon... that never happened with me.

---

### Post by ecstatic on 2006-02-26
Thanks once again bluevoodoo.  It's great to have people like you in the community to help newbs like me out.  I didn't notice the Custom Command box at the bottom of Open Application With.  That works good.  
The Wine-Systry seems to open everytime I run an executable program with Wine, so perhaps it just needs to be there.  No clue really.
I get to play with something new!  After all the hours of frustration :evil:

---

### Post by bluevoodoo1 on 2006-02-26
[QUOTE=ecstatic]Thanks once again bluevoodoo.  It's great to have people like you in the community to help newbs like me out.  I didn't notice the Custom Command box at the bottom of Open Application With.  That works good.  
The Wine-Systry seems to open everytime I run an executable program with Wine, so perhaps it just needs to be there.  No clue really.
I get to play with something new!  After all the hours of frustration :evil:[/QUOTE]

:) :D :mrgreen: :KS

---

