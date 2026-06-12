---
title: "Very frustrated with Ubuntu, close to throwing the pc through the window"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-03-31
I've been tinkering around with Ubuntu for the past 24 hours and found it to be really frustrating. Some help, please, before I toss the pc through the window. 

With a little ingenuity and plenty of help from others(Pelo, ant, ljl, xtknight, y8llow, etc.), I was able to configure plenty of tools/utilities. However, I'm having problems with:

[LIST=1]
[*]write permissions. How on earth do I write to a file not within home/user ? I've read plenty of guides but I'm still quite confused at what I'm supposed to do. 
[*]having an advanced search tool. I installed Konqueror and attempted to search for a file within a directory that contains many sub-folders. What happened was that Konqueror was UNABLE to find the file. However, when the search field was left empty, Konqueror was able to list all the files within all the sub-folders. 

Example: 

filename =  250(please, please don't tell me that numerical filenames don't work with Konqueror Search tool. All the files I'm working with are numerically numbered.)
Search within file:////media/sda2/All-art Clone2/ 
Include Sub-folders checked. 
Use files index not checked. 
File-type: All files and folders


Results = 0 files found. 
(I also experimented with removing "file:////" and I got the same results.)

Does anyone know a workaround or another search tool? *groans* Why does a simple task like searching turn into "A trip to the past"? This is just nerve-wracking!

[/LIST]

---

### Post by aysiu on 2007-03-31
> **Lucifiel said:**
> 
write permissions. How on earth do I write to a file not within home/user ? I've read plenty of guides but I'm still quite confused at what I'm supposed to do. 
 I don't know anything about the Konqueror search tool, but this will help you with permissions:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, if you're feeling that frustrated, you might want to go for a walk (or run!), take in a movie, or nap... a little time away from the computer can help you not go crazy.

**Edit**: Okay. I don't know what's going on with your Konqueror, but mine's working fine. I just created a test file in /home/username/Desktop/test/250. Then I did a search for it, and the file came up. See the attached screenshot.

What filesystem (FAT32, NTFS, Ext3, something else) is /media/sda2, and is it an external or internal drive? Maybe that has something to do with it? Can you do what I did and create a test file within your home folder to see if the regular search function works okay? Just go to /home/lucifiel/Desktop and right-click and create a text file. Call it *250*. Then do a search in /home/lucifiel for *250*. If that works, it may have something to do with /media/sda2 specifically. If it doesn't work, something's wrong with your Konqueror or your indexing.

---

### Post by mikewhatever on 2007-03-31
You want too much in too 24 hours. Aysiu is right, leave if for another day. 
To right to a write protected file, you need to open it with admin previlages:
> sudo nano /full_path/file_name
sudo gedit /full_path/file_name


I've long given up on Ubuntu nautilus search function (haven't tried conqueror). Either I didn't know how to use it, or it is completely useless. I found that locate command works well
> locate file_name

---

### Post by aysiu on 2007-03-31
I prefer *gksudo gedit* to *sudo gedit*, for these reasons:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I also use *locate file_name* to find files, but don't forget that if it's a newly created file, you might have to do *sudo updatedb* first to index the file. Sounds as if Lucifiel might just be a little overwhelmed right now and throwing commands out like that might be intimidating...

---

### Post by picpak on 2007-03-31
Heh, I know exactly how you feel. I remember being so ticked off I wanted to personally meet Linus Torvalds and throw my computer in his face (I was so confused, I didn't even know who controlled my own distribution).

But, just like everyone else said: calm down! I know you're frustrated, but compared to the other abnormalties I see in this forum, your problems are relative. In fact, I'd go as far as to say that if THESE are your worst problems, I applaud you.

As for permissions: sudo is your man. If you're ever in the terminal and it tells you you don't have permissions, just prefix the command with **sudo** and you should be good to go. So if you want to throw the computer out the window...don't worry, sudon't have to (sorry, shoot me for that one).

Oh, and with the file searching...I can't speak for Konqueror, but I find file searching on Linux sketchy at best. Like aysiu, I do the locate+sudo updatedb thing. Of course, it may just be a problem with file indexing. Just wait and see.

---

### Post by Lucifiel on 2007-03-31
> **aysiu said:**
> I don't know anything about the Konqueror search tool, but this will help you with permissions:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, if you're feeling that frustrated, you might want to go for a walk (or run!), take in a movie, or nap... a little time away from the computer can help you not go crazy.

**Edit**: Okay. I don't know what's going on with your Konqueror, but mine's working fine. I just created a test file in /home/username/Desktop/test/250. Then I did a search for it, and the file came up. See the attached screenshot.

What filesystem (FAT32, NTFS, Ext3, something else) is /media/sda2, and is it an external or internal drive? Maybe that has something to do with it? Can you do what I did and create a test file within your home folder to see if the regular search function works okay? Just go to /home/lucifiel/Desktop and right-click and create a text file. Call it *250*. Then do a search in /home/lucifiel for *250*. If that works, it may have something to do with /media/sda2 specifically. If it doesn't work, something's wrong with your Konqueror or your indexing.

Oh, thank you so much for the link. :)

Yeah, I need some anger management therapy and meditation helps a lot. :P 

/media/sda2 is SATA and has NTFS partitions. It currently is read only, no write. 

I just tried out your method and no, 250.txt didn't show up in the search results. Heh... so it's Konqueror being cranky. I wonder if reinstalling the program will solve the issue.

---

### Post by picpak on 2007-03-31
Have you tried searching through Kfind?

---

### Post by Lucifiel on 2007-03-31
> **mikewhatever said:**
> You want too much in too 24 hours. Aysiu is right, leave if for another day. 
To right to a write protected file, you need to open it with admin previlages:


I've long given up on Ubuntu nautilus search function (haven't tried conqueror). Either I didn't know how to use it, or it is completely useless. I found that locate command works well

Aha, thank you for the commands. Well, it isn't too much, I think, to be able to configure some simple things.However, given the complexity of this issue, I might've got a bit too demanding and over-emotional. =P 

Oh dear, I kinda need a gui interface 'cos I'm dealing with thousands of files. As a result, looking at the thumbnails helps to narrow down the results. Geez... lol. :)

---

### Post by aysiu on 2007-03-31
> **Lucifiel said:**
> I just tried out your method and no, 250.txt didn't show up in the search results. Heh... so it's Konqueror being cranky. I wonder if reinstalling the program will solve the issue. Hm. That's bad. Something's wrong then. I don't think reinstalling Konqueror would make a difference. Unfortunately, I don't know what *will* make a difference. Maybe a KDE guru will step in...

---

### Post by fdrake on 2007-03-31
did you try this?:
sudo chown <user> -R /media/sda2
sudo chmod 755 -R /media/sda2

on <user> write down your username.

---

### Post by aysiu on 2007-03-31
You can't *chown* an NTFS partition.

---

### Post by fdrake on 2007-03-31
didn't know. ops.. :P

---

### Post by JNowka on 2007-03-31
In Konqueror the search utility in the upper right corner will only search for files in the directory that you are currently in.  There is a "Find file" option under the Tools menu if you want to continue using it.  If you want a complete search throughout your system then you are wanting kfind.  I expect that the search utility in the tools menu is the same as kfind though, so you may already have it, but check.  I hope this helps.

---

### Post by aysiu on 2007-03-31
FYI: The search I did in the screenshot was just by pressing Control-F while in my home directory, and the search went two folders deep (/home/username/Desktop/test/250)

---

### Post by JNowka on 2007-04-01
I would also like to say that if you want to write to a ntfs drive then you will want to install ntfs-3g.  It give linux the ability to write to ntfs without messing it up, at least not to date.  You can use the following tutorial to install it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

hope this helps.

---

### Post by Lucifiel on 2007-04-01
> **JNowka said:**
> In Konqueror the search utility in the upper right corner will only search for files in the directory that you are currently in.  There is a "Find file" option under the Tools menu if you want to continue using it.  If you want a complete search throughout your system then you are wanting kfind.  I expect that the search utility in the tools menu is the same as kfind though, so you may already have it, but check.  I hope this helps.

Hm? What search utility in the upper right corner? I didn't see it, sorry.

The "find tool" I was using can be found under the category: Applications.

---

### Post by scoon on 2007-04-01
Hey there, 

Open up a terminal (kterm in kde) and try this: 

```
find /media/sda2/All-art Clone2/  -name '*250*'
```

find is a command line tool, you can read the manual page about it by also opening a terminal, I think you may be able to use konqueror as well, and type **man find**

-scoon

---

### Post by Lucifiel on 2007-04-01
> **picpak said:**
> Heh, I know exactly how you feel. I remember being so ticked off I wanted to personally meet Linus Torvalds and throw my computer in his face (I was so confused, I didn't even know who controlled my own distribution).

But, just like everyone else said: calm down! I know you're frustrated, but compared to the other abnormalties I see in this forum, your problems are relative. In fact, I'd go as far as to say that if THESE are your worst problems, I applaud you.

As for permissions: sudo is your man. If you're ever in the terminal and it tells you you don't have permissions, just prefix the command with **sudo** and you should be good to go. So if you want to throw the computer out the window...don't worry, sudon't have to (sorry, shoot me for that one).

Oh, and with the file searching...I can't speak for Konqueror, but I find file searching on Linux sketchy at best. Like aysiu, I do the locate+sudo updatedb thing. Of course, it may just be a problem with file indexing. Just wait and see.

Haha, well... in retrospect, Ubuntu isn't as bad as when I got my very first computer: that was way back in 1992 and everything was ms-dos. I was feeling really helpless back then. However, frustration and helplessness aren't really the same thing. :)

Huh, why'd you want to appluad me? 

And okay, I'll give Kfind a try. :)

---

### Post by Lucifiel on 2007-04-01
> **aysiu said:**
> Hm. That's bad. Something's wrong then. I don't think reinstalling Konqueror would make a difference. Unfortunately, I don't know what *will* make a difference. Maybe a KDE guru will step in...

Uh oh... I tried to reinstall Konqueror and this is the issue I received when trying to reinstall konq-kim:

E: konq-kim: subprocess post-installation script returned error exit status 2

From Terminal: check the attached image.

Oh, I could remove konq-kim but not install it. =/ Also, I tried rebooting and it didn't help the issue either.

---

### Post by Lucifiel on 2007-04-01
> **fdrake said:**
> did you try this?:
sudo chown <user> -R /media/sda2
sudo chmod 755 -R /media/sda2

on <user> write down your username.

Ah well, since it's been learnt that chown can't be used on NTFS volumes, it's okay anyways. Btw, what do these commands do? :)

---

### Post by Lucifiel on 2007-04-01
> **JNowka said:**
> I would also like to say that if you want to write to a ntfs drive then you will want to install ntfs-3g.  It give linux the ability to write to ntfs without messing it up, at least not to date.  You can use the following tutorial to install it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

hope this helps.

Yes, I actually tried out that tutorial but stumbled into some issues. =/ You can see my post at the end of the thread. :p

---

### Post by Lucifiel on 2007-04-01
> **scoon said:**
> Hey there, 

Open up a terminal (kterm in kde) and try this: 

```
find /media/sda2/All-art Clone2/  -name '*250*'
```

find is a command line tool, you can read the manual page about it by also opening a terminal, I think you may be able to use konqueror as well, and type **man find**

-scoon

Oh, don't worry, I know what Terminal is. It's the equivalent of cmd.exe or what you'd call a command prompt window that's run within Windows. :)  And I do know what "find" is but thank you for your help anyways. :)

These are my results from using that command and I think that explains something, that maybe there's problems with the spacing in "All-art Clone2" and thus, it's "bouncing" into "All-art" directory(which also exists). I'm confident, therefore, that once I manage to get ntfs-3g working, I'll be able to rename the directory and change the spacings into underscores.

~$ find /media/sda2/All-art Clone2/  -name '*250*'
/media/sda2/All-art/ART/forest/250.gif
/media/sda2/All-art/ART/forest/allforest/250.png
/media/sda2/All-art/ART/forest/allforest/edits/250.pcx
/media/sda2/All-art/ART/forest/allforest/edits/250.png
/media/sda2/All-art/ARTFINAL/Backgrounds/250.gif
find: Clone2/: No such file or directory

---

### Post by Albi on 2007-04-01
> **Lucifiel said:**
> Oh, don't worry, I know what Terminal is. It's the equivalent of cmd.exe or what you'd call a command prompt window that's run within Windows. :)  And I do know what "find" is but thank you for your help anyways. :)

These are my results from using that command and I think that explains something, that maybe there's problems with the spacing in "All-art Clone2" and thus, it's "bouncing" into "All-art" directory(which also exists). 

~$ find /media/sda2/All-art Clone2/  -name '*250*'
/media/sda2/All-art/ART/forest/250.gif
/media/sda2/All-art/ART/forest/allforest/250.png
/media/sda2/All-art/ART/forest/allforest/edits/250.pcx
/media/sda2/All-art/ART/forest/allforest/edits/250.png
/media/sda2/All-art/ARTFINAL/Backgrounds/250.gif
find: Clone2/: No such file or directory

Spaces should have a backslash ( \ ) before them, so it looks like this
 find /media/sda2/All-art\ Clone2/  -name '*250*'

Also, if you want a graphical way of making files etc on system directories just type 
"gksu nautilus" in the terminal
and it will open up the file browser with root priveleges.  be very careful though.

---

### Post by Michl on 2007-04-01
Just used
Places -> Search for files
and found things on all hard drives, including the NTFS drive.
Maybe this is too obvoius, but it is a mistake I made:  You
need to put in the right folder.  If you want to search the whole
computer, click on filesystem.

The psychocats site helped me very much.   How to mount
windows, load flash 9.  And the edit piece is the best.
Alt F2 gksudo nautilus (I think that's how that goes) is a
great shortcut. 

I will say this, ubuntu was and is frustrating for me.  I have been
running it on three computers for almost a  couple of months now, and
I still have big and little wrinkles I cannot iron out.  Some of them are bugs
(e.g. dialup in network-admin) that nobody is interested in fixing; some 
of it is a mystery (screensavers sometimes work and sometimes don't),
some of it is upstream somewhere in linux universe -- Evolution and
MS Exchange, printer drivers that only handle networks and not LPT1
and so on.  My wife says it's just a little buggier than MS, but there are
other payoffs:  control, speed, flexibility  and plain old coolness.

I only worry if I can keep ubuntu at work.  At home I can tinker, but at work I
need an OS I can count on and don;t have to think about. and I don;t know
if I can get it into that shape.  The other day I spent a whole day unsuccessfully
trying to get the printer to work, and I can't waste time like that at work.

Michael

---

### Post by fdrake on 2007-04-01
> **Lucifiel said:**
> Ah well, since it's been learnt that chown can't be used on NTFS volumes, it's okay anyways. Btw, what do these commands do? :)


sudo chown <user> -R /media/sda2 #sets the owner of the file to <user>
sudo chmod 755 -R /media/sda2   #sets the privileges. 
user: RWX-user-group&everyonelse:RX
R=read
W=write
X=execute

---

### Post by scoon on 2007-04-01
Hey there, 

wrap your path in single quotes.

-scoon

---

### Post by JNowka on 2007-04-01
What version of ubuntu do you have?  Edgy or Dapper?

---

### Post by Lucifiel on 2007-04-01
> **JNowka said:**
> What version of ubuntu do you have?  Edgy or Dapper?

I'm using 6.06 dapper drake(OOOps... It's not edgy, it's dapper.). Yeah, I really should've got 6.10 instead. 

Oh well... I'll stick with this for now and then upgrade when Fawn comes out, provided my o/s doesn't have any problems then.

---

### Post by Lucifiel on 2007-04-01
> **scoon said:**
> Hey there, 

wrap your path in single quotes.

-scoon

Will give it a shot.

For now, I'm going to read a book and listen to some music... maybe ES posthumus or X japan or something else. 

Thank you for all your help, so far. :)

---

### Post by kvonb on 2007-04-01
I believe the problem with Gnome's find tool is that it doesn't seem to follow symlinks, I couldn't find a file that was in a linked folder in my home folder.

The other problem seems to be a throwback to the Microsoft way of doing things, ie to get a list of all .jpg files, you would use: ***.jpg** as your search criteria, whereas in Linux (maybe just Gnome), we need to use only: **jpg** in the search field.

Oh and don't forget to change the "Look in folder...." box to the best location, I use "Filesystem", that searches the **whole** computer.

One failsafe backup I use when I give up on the GUI searches is this beauty:

```
cd /
sudo find . -name '*.jpg*'
```
You can put anything between the single quotes, it will take ages, but is guaranteed to find what you are looking for :).

Regards, Kev :)

---

### Post by Lucifiel on 2007-04-01
OMG... I finally got ntfs-config to work. And the reason for it not being able to install was 'cos of one thing(please don't laugh!): I accidentally put in the urls for Edgy into sources.list when my ubuntu build was Dapper. =P

Okay go ahead and laugh, I was laughing anyways... ;p 

And now, as for the search tool, don't laugh but ... I think I've resolved it too. It turns out I wasn't looking hard enough: the search tool in "Places" was good enough. Omg... next time, I'm going to work less and relax more. :p

But still, I'd really like to use Konqueror and wonder how I can fix the konq-kim error. I've only just started looking into that issue but so far, haven't found anything pertaining to this issue. :) Btw, what KDE components need to be installed for Konq-kim to work? I only just realised that perhaps, I might've not installed all the required plugins, etc.

Also, is there some sort of recommended software list for Ubuntu? This is 'cos well, I want to look around a little but don't want to keep bugging the Ubuntu forums all the time. :)

---

### Post by Lucifiel on 2007-04-01
Oh and just one more thing: I've a faulty onboard lan chip which can't be disabled via BIOS. Thus, the only alternative was to disable via WinXP.

However, in Ubuntu Network manager, my 2 network cards show as eth0 and eth1. Anyone knows what command will give me more details about them? 'Cos I'm starting to lose my internet... again. :(

---

### Post by Lucifiel on 2007-04-01
Bah, X crashed for the second time. I don't really recall what I was doing the first time round.

The second time, I was looking at history.dat via a Document editor. And I also had plenty of Firefox tabbed windows open. 

From syslog

Mar 31 22:09:34 lucifiel gconfd (lucifiel-5112): Received signal 15, shutting down cleanly


Apr  2 11:13:43 lucifiel gconfd (lucifiel-5118): Received signal 15, shutting down cleanly
Apr  2 11:13:43 lucifiel gconfd (lucifiel-5118): Exiting
Apr  2 11:13:43 lucifiel gdm[4680]: Error reinitilizing server

This is what I've done so far:

Disabled all power management software.

Checking the logs.

Trying to disable faulty onboard lan chip. It cannot be disabled via bios, and I've no idea how to do so in Linux. Have checked Device manager and Networking: no option to disable device. Have tried looking at ifconfig  but not too sure what to do with the information displayed. It is not a wireless card so iwconfig doesn't work.

I also understand that certain ATI cards might have various issues with Ubuntu but I've not looked into this part yet.

Hmmm... it also seems that crontab might be another potential culprit.

---

### Post by Lucifiel on 2007-04-02
Bah, more and more problems just keep piling up. =(

This time round, I can't access "Disks" from "System". So, in the end, a lot of people's advice boils down to this: try a different flavour. I don't know if it's really worth the effort or if I should just go back to WinXP. :( 

I wonder if I'm talking to myself. Oh well... :(

---

### Post by kvonb on 2007-04-02
> **Lucifiel said:**
> Bah, more and more problems just keep piling up. =(

This time round, I can't access "Disks" from "System". So, in the end, a lot of people's advice boils down to this: try a different flavour. I don't know if it's really worth the effort or if I should just go back to WinXP. :( 

I wonder if I'm talking to myself. Oh well... :(

Yeah, go back to WinXP, Linux is too hard :).

If the computer is randomly crashing then I would suggest that you have a hardware problem.  Linux doesn't just crash for no reason, and dodgy hardware is the first place to look.

Check the memory first, maybe slow it down in the BIOS, and do a memory test when you first boot.  Also do a full scan of the hard disk.

Linux uses memory a lot more aggressively than Windows and any slight problem will show up big time, usually as lockups.  Windows XP can chug along quite nicely on dodgy RAM, it really doesn't care, so Win might run (or seem to run) whereas Linux is a lot more picky.

Also check your mainboard for popped capacitors.  I know I keep repeating myself on this one, but it is a VERY common problem.  If Windows was crashing on you as well then the mainboard might be the culprit.

Seeing as you have nothing to lose at this stage, why not download and try "Feisty" instead of "Dapper"?  It's very nice but you will need to download nearly 300 megs of updates!

Regards, Kev :)

---

### Post by eentonig on 2007-04-02
I can double on Kev's post.

Install Feisty. It's beta, but it's stable and has a lot going for it. For me, everything worked from the beginning without any troubleshooting on exotic HW drivers. 

Take your time with Linux. It's very hard in the beginning. Especially if you're used to be a 'power user' in Windows. Just accept (and try to enjoy) the learning curve. Once you get started, it goes faster and faster. Don't think "X is better than Y". Just accept "X is different then Y. And that's why I don't get to do this basic ****!"

If you've got the time and feel like it. Read through the help.ubuntu.com website, take a look at the howto's on this forum, check the repsonse people get on their questions, ... and you will start to understand how exactly L differs from Ms. Some things are better, some are worse.

There are some MS features I miss. But I wont go back to Ms for my home system (actually, I installed VMware with an XP in it, so I'm cheating on this one.). Point is. I was once like you. Now I'm a convert. And not because I'm a geek. I'd rather go for a walk with my dogs than spending my time troubleshooting stupid configs.

---

### Post by zvacet on 2007-04-02
Commands for yours cards 
```
ifconfig
```

and

```
gksudo gedit /etc/network/interfaces
```

---

### Post by Lucifiel on 2007-04-02
> **kvonb said:**
> Yeah, go back to WinXP, Linux is too hard :).

If the computer is randomly crashing then I would suggest that you have a hardware problem.  Linux doesn't just crash for no reason, and dodgy hardware is the first place to look.

Check the memory first, maybe slow it down in the BIOS, and do a memory test when you first boot.  Also do a full scan of the hard disk.

Linux uses memory a lot more aggressively than Windows and any slight problem will show up big time, usually as lockups.  Windows XP can chug along quite nicely on dodgy RAM, it really doesn't care, so Win might run (or seem to run) whereas Linux is a lot more picky.

Also check your mainboard for popped capacitors.  I know I keep repeating myself on this one, but it is a VERY common problem.  If Windows was crashing on you as well then the mainboard might be the culprit.

Seeing as you have nothing to lose at this stage, why not download and try "Feisty" instead of "Dapper"?  It's very nice but you will need to download nearly 300 megs of updates!

Regards, Kev :)

Nah, not going back to using WinXP full-time!!! :P Never!!! :P 

Okay, the "Disks" issue and some syslog SCSI errors I got seem to be related to the card reader in my printer. Somehow, Linux's seeing the card reader as a hard disk and it's trying to access the "non-existent" data.

Huh... those're some interesting explanations.

Well, Linux isn't crashing. Instead, something's shutting down Ubuntu. Someone mentioned crontab(supposedly related to cron jobs) and I intend to follow up on that lead.

No, there isn't much wrong with my hardware. The only thing dodgy is the on-board lan on my motherboard. 

And the reason why WinXP was crashing was primarily 'cos of some software conflict. 

So, do you mean to just reformat Dapper and use Feisty right away? As in: no upgrading from Dapper to Edgy and then to Feisty? 

Heh... 300 mb of updates.

---

### Post by Lucifiel on 2007-04-02
> **eentonig said:**
> I can double on Kev's post.

Install Feisty. It's beta, but it's stable and has a lot going for it. For me, everything worked from the beginning without any troubleshooting on exotic HW drivers. 

Take your time with Linux. It's very hard in the beginning. Especially if you're used to be a 'power user' in Windows. Just accept (and try to enjoy) the learning curve. Once you get started, it goes faster and faster. Don't think "X is better than Y". Just accept "X is different then Y. And that's why I don't get to do this basic ****!"

If you've got the time and feel like it. Read through the help.ubuntu.com website, take a look at the howto's on this forum, check the repsonse people get on their questions, ... and you will start to understand how exactly L differs from Ms. Some things are better, some are worse.

There are some MS features I miss. But I wont go back to Ms for my home system (actually, I installed VMware with an XP in it, so I'm cheating on this one.). Point is. I was once like you. Now I'm a convert. And not because I'm a geek. I'd rather go for a walk with my dogs than spending my time troubleshooting stupid configs.
Hmmm...Feisty, huh? 

Well, from what I've gathered so far: 

Linux uses a central package manager which takes care of almost 90% of all installations you'd ever need. And as opposed to opening up .log or .txt files separately, any error messages can be viewed directly. There's the very basic Add/Remove control, the more advanced Synaptic package manager and finally, the very sophisticated method of using command line to download, configure, install, etc., via Terminal. 

An advantage about Linux is its' focus on open-source, non-proprietary software which is very beneficial for all who need software with moderate features. However, the downside is that a lot of open-source software can't always meet the needs of those who're accustomed to or require very advanced features for their work. Much like the console vs pc argument, hell has been raised and razed many times over, when arguments are made for and against proprietary software. 

And well, I already know that Linux is rather different from Windows. :) The problems for me, aren't getting used to Linux but rather, smoothing out any kinks so the o/s is in good, working condition. After all, one might lose her work if Ubuntu shuts down on her. :) And actually, I'd prefer not to upgrade yet. My reasoning is that I should spend some time to flattening out any kinks as my hardware configuration has always had some issues with drivers, etc. , etc. in Windows. =/

---

### Post by Lucifiel on 2007-04-02
> **zvacet said:**
> Commands for yours cards 
```
ifconfig
```

and

```
gksudo gedit /etc/network/interfaces
```
Oh, thank you for those commands. Though I've tried them already, it doesn't hurt to tinker around again. ^___^

*goes to read the hardware addresses*

Aha!!!! Viola... I've figured it out. Muhwahahahahahaha... you pesky little imp, I've gotcha!!!! :twisted:

---

### Post by Lucifiel on 2007-04-03
Hmmm... as of right now, only Firefox and gnome-system-monitor have crashed. Will monitor the issues carefully. 

For konq-kim, I decided to try doing "sudo aptitude install konq-kim". Fascinatingly enough, there haven't been any error messages while installing. I wonder if installing via Synaptic created that issue. 

Well, at least this hasn't been the pure nightmare situation I faced with WinXP about 2 years ago. The installation seemed fine but after downloading and installing the hotfixes, etc., many of my applications went berserk. It took a reinstallation to fix all that and I discovered the cause was some cpu-related issue caused by a hotfix that Microsoft hadn't fixed yet. Because of that problem, many of my applications started hitting 100% cpu. 

Now, it's all right for a game to do so because it consumes plenty of system resources(even the really old ones do that these days on the faster cpus) but for a common, normal program like MS WordPad, it was wholly unacceptable.

Edit: Using sudo aptitude reinstall gnome-system-monitor, I was able to successfully reinstall the program.

Now, let's see if it continues to crash. ;)

Edit again: Carried out the same procedure for Firefox. =P *shakes a wrench at Firefox* Let's see if you dare to crash now!!!!

---

### Post by Europa2010AD on 2007-04-03
For your file searching issues... you might want to take a look at this program:

[Meta Tracker]("http://www.gnome.org/projects/tracker/index.html")

*note* I haven't tried this program myself, but I came across the webpage today and thought it might be something that'd be useful for you. I might give it a try myself when I have time.

---

### Post by raptor2552 on 2007-04-03
Lucifiel, I feel your pain, really

If I may make a suggestion while you're cooling off maybe take a peek at this starter guide: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) although of course this won't help with your NTFS problem but you'll have a better understanding of what's going on when your typing all those weird commands and such.

---

### Post by pallukucchu on 2007-04-03
Hi lucifel nice to see you online:)

---

### Post by Lucifiel on 2007-04-04
Thank you, Europa2010AD, for the recommendation. :)

To raptor2552 : 

I'll give it a careful read. 

To pallukucchu: 

Thank you for the welcome. Sorry if I'm being rude but who're you? I'm not "Lucifel" from #ubuntu, btw. ^^;; 

Meanwhile, I'm downloading Feisty and I intend to do a fresh reinstall by the end of this day. There're way too many issues here and re-installing things via command-line didn't work. It seems that many things're broken: both Gnome and Kde. 

Somehow, though, perhaps the live cd has some problems that weren't detected by "detect cd for errors". I really wish that the cd would double-check the files on the cd during the installation process for errors and also double-check the installed o/s after everything is done installing.

---

### Post by ndefontenay on 2007-04-04
Lucifiel, do this:

```
vim 250
```

In the vim console, type this:

```
:help!
```

Finally, just do it! ^^

---

### Post by Lucifiel on 2007-04-04
To ndefontenay:

vim 250 did this?

> E325: ATTENTION
Found a swap file by the name ".250.swp"
          owned by: lucifiel   dated: Wed Apr  4 13:51:37 2007
         file name: ~lucifiel/250
          modified: YES
         user name: lucifiel   host name: lucifiel
        process ID: 7137 (still running)
While opening file "250"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r 250"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file ".250.swp"
    to avoid this message.

Swap file ".250.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (Q)uit, (A)bort:


I typed in :help! and got this? O_o;; 

> 

E478: Don't panic! 


---

### Post by esodin on 2007-04-04
Good call on going for Feisty. I had an  issue that was linked to my mem-card reader with Edgy: Ubuntu would not boot if Ubuntu was the last OS run. I was so tired of fixing things (I got all to work - much thanks to posts and HOW-TO's in this forum) and I just could get no where with the mem-card USB problem. My work around was to unplug the internal mem-card reader or make certain I booted XP before I booted Ubuntu (how ironic - I needed to run XP to run Ubuntu.

I am getting to the point: When upgrading to Feisty the USB and mem-card reader issues vanished. Stick with it - I am all but a full convert (still need XP for CSS) :)

---

### Post by Lucifiel on 2007-04-04
Hmmm... it really seems that xorg-server-core is corrupted. 

Ah well..

---

### Post by kvonb on 2007-04-04
> **Lucifiel said:**
> Hmmm... it really seems that xorg-server-core is corrupted. 

Ah well..

You can re-install just about anything by running Synaptic from the menus, then search for the app you want to re-install, in this case "xorg-server-core", (maybe just type in "xorg" as a partial search), then right click on the one you want and select "re-install".

Apply and it should download and overwrite your current version.

If it doesn't download, but just goes straight to re-installing, you will need to delete the cached file from /var/cache/apt/archives.  You will of course need sudo privileges for doing that, ie:

```
cd /var/cache/apt/archives
sudo rm 'xorg-*'
```

All the files in /var/cache/apt/archives are the actual files that were downloaded and installed, as in updates and things you installed.  It **IS** safe to delete everything in there, it will **NOT** damage your system.

I usually make a backup copy of anything that I am about to change/delete just in case I stuff things up.

Once you have deleted the xorg-* files, run synaptic as above.

Regards, KEv :)

---

### Post by Lucifiel on 2007-04-04
Well, I already tried reinstalling xorg-server-core by doing > gksudo aptitude reinstall xorg-server-core

However, Ubuntu wouldn't let me. Something about not enough permissions. In fact, in Synaptic, you can't reinstall it. And I wouldn't remove it unless I want the whole o/s to crash on me. 

Edit again: Here's the result from running the above command.
> 
Fontconfig error: "~/.fonts.conf", line 1: no element found
Reading package lists... Done
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Well, I could spend hours more trying to troubleshoot this but I could just do a clean reinstall. There's not much to back up and I've only configured themes and my splash screen and some other stuff. Besides, I'm at my limit. What I really wanted was something that'd at least install well, not something that requires extensive researching/re-compiling/re-installing, etc. of libraries/components, etc.

Man, right now, I feel like I've been thrown through some crash course on how to troubleshoot Ubuntu. -__-;; That ought to be something you'd learn like a few weeks or months after installing an o/s, not on Day One. :(

---

### Post by zvacet on 2007-04-04
Do you have something else runing,like synaptic or update manager at the same time when you try to reinstall with terminal?

---

### Post by Lucifiel on 2007-04-04
No, nothing else's running at all, only Terminal is, apart from the other required processes/files/commands, etc. which're needed to keep Ubuntu running. In any case, I'd rather reformat, ya know, 'cos this sounds like a massive problem with multiple files, not just xserver-xorg-core .  I really don't want to repair a certain file, only to find out I need to fix many other files as well. And in this case, it seems like multiple files are corrupted. It's frustrating since I actually installed Ubuntu Dapper again and had made sure to reformat all the selected partitions. 

Anyways, if Feisty doesn't work... boy, I dread going back to WinXP.

---

### Post by Lucifiel on 2007-04-04
Okay, I'm running the Feisty installer now. It took me three tries to get it to run.

First time, it hung 'cos I kept clicking on the "edit partition" button. Second time, it hung on the "detecting disks" section.

This time round, it seems to be going well.

I'll post back if Xorg is giving me any problems. 


Thank you all for your kind support and advice. :)

Edit: I'll test the installation by installing Koffice and other programs. If they don't show up in my menu, it means xserver-xorg-core is broken.

---

### Post by Lucifiel on 2007-04-04
Finally!!!! There have been 2 "black screens"(okay, I mistook them to be crashes) so far but at least, I can install programs without any errors, using Synaptic.

---

### Post by kvonb on 2007-04-04
Please remember, Feisty is BETA and there will be lots of updates to come.

I would recommend NOT enabling desktop effects OR the restricted video driver just yet, as each update can and most likely WILL mess those up making it not boot back to the desktop.

If you do have a problem getting the desktop back, here are a few suggestions:

1) After an update and before rebooting, on the main menu under System->Preferences, select "Sessions" and in the "Startup Programs" tab, temporarily disable any programs you have in there (apart from the default ones) to run on boot, especially Beryl (which you shouldn't have anyway), just to be on the safe side.  You can re-enable them once you have successfully booted.

2) If you get a nasty text screen that says the Xserver couldn't start, just run this command:  sudo dpkg-reconfigure -phigh xserver-xorg.  That will create a new default xorg.conf.

But above all, **be prepared for breakage** with each update as we get closer to the final release.

Alternatively, If Feisty is working well for you now, just ignore the updates as Feisty will be in final release in a week or so anyway :).

Regards, KEv :)

---

### Post by Michaelt74 on 2007-04-04
Lucifiel, Linux & Ubuntu serves the needs of most users, but not all. Maybe Ubuntu isn't for you?

[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

---

### Post by Ptero-4 on 2007-04-05
Welcome Luci. For future reference a couple things, before burning a CD check the md5 code of the downloaded iso image, this allows you to ensure that the image didn`t got corrupted during the transfer (due to common transfer issues or a dodgy phone/ethernet cable), use sudo when using command line apps and gksu in GUI ones, and use nano when editing files in the shell (vim and emacs are quite complex for beginners).

And enjoy the stay.

---

### Post by medad on 2007-04-05
Kudos for sticking with Ubuntu! You sure went through a lot more than I did.  My video card gave me the most problems (motherboard p4m800).

I was wondering if you ever tried to run your system with only with the original ethernet card installed.  After installing Feisty, did you have any further problems with your connection?

Also you mentioned using Konqueror.  It is based off of KDE.  Have you thought about maybe trying the Kubuntu version.  I actually have both Ubuntu and Kubuntu currently running (this is my goof computer).

Wish you the best of luck with your system.

---

### Post by Lucifiel on 2007-04-05
> **kvonb said:**
> Please remember, Feisty is BETA and there will be lots of updates to come.

I would recommend NOT enabling desktop effects OR the restricted video driver just yet, as each update can and most likely WILL mess those up making it not boot back to the desktop.

If you do have a problem getting the desktop back, here are a few suggestions:

1) After an update and before rebooting, on the main menu under System->Preferences, select "Sessions" and in the "Startup Programs" tab, temporarily disable any programs you have in there (apart from the default ones) to run on boot, especially Beryl (which you shouldn't have anyway), just to be on the safe side.  You can re-enable them once you have successfully booted.

2) If you get a nasty text screen that says the Xserver couldn't start, just run this command:  sudo dpkg-reconfigure -phigh xserver-xorg.  That will create a new default xorg.conf.

But above all, **be prepared for breakage** with each update as we get closer to the final release.

Alternatively, If Feisty is working well for you now, just ignore the updates as Feisty will be in final release in a week or so anyway :).

Regards, KEv :)
Updates, huh? Somehow, I didn't get to install any updates when I started into Ubuntu the first time. Though, given that I downloaded the very latest .iso via BT, my bet is that all fixes have already been compiled and "inserted" into it.

Heh... I even left the pc on while I went to sleep and no, it didn't break while I slept. :p

Mmmm... when Feisty reaches final release, does this mean that I'll have to reinstall the o/s?  I think I'll likely wait a few days after the final release 'cos I know that even "fixes" released after a product is now final, have the potential to break a computer. :p
Oh yeah, I've lived through Microsoft's patches... they do far more damage to your soul than a week of troubleshooting Ubuntu. :p

---

### Post by Lucifiel on 2007-04-05
> **Michaelt74 said:**
> Lucifiel, Linux & Ubuntu serves the needs of most users, but not all. Maybe Ubuntu isn't for you?

[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

Hmmm...yes, I'm a novice to Linux. :) However, I've lived through worse and don't worry, I was prepared for a certain level of breakage and problems(though not on the level I faced). :p And oh yeah, before I made the switch to Ubuntu, I already made sure to at least seek out some replacements for the programs I needed to use. :) Whenever I make a transition to a new o/s or have to replace a list of programs, I always take care to compile a list of different alternatives should something break. ^^;; 

Anyways, Feisty has been doing quite well so far, except for a bit of sluggish performance while minimising and maximising windows. :)

Well, we'll see what happens to Feisty in a few days' time. :D

---

### Post by cantormath on 2007-04-05
> **Lucifiel said:**
> I've been tinkering around with Ubuntu for the past 24 hours and found it to be really frustrating. Some help, please, before I toss the pc through the window. 

With a little ingenuity and plenty of help from others(Pelo, ant, ljl, xtknight, y8llow, etc.), I was able to configure plenty of tools/utilities. However, I'm having problems with:

[LIST=1]
[*]write permissions. How on earth do I write to a file not within home/user ?[/LIST]

I feel your pain and want you to fix your problem.  With that I must say that in the future of your linux experience, you will see why this post is as funny as it is.  I see some really top notch folks commenting in here so I will not give advice except to remember that your are not using windows anymore..........and that is usually the answer to the why....

Welcome to the family.

---

### Post by cantormath on 2007-04-05
> **Lucifiel said:**
> Hmmm...yes, I'm a novice to Linux. :) However, I've lived through worse and don't worry, I was prepared for a certain level of breakage and problems(though not on the level I faced). :p And oh yeah, before I made the switch to Ubuntu, I already made sure to at least seek out some replacements for the programs I needed to use. :) Whenever I make a transition to a new o/s or have to replace a list of programs, I always take care to compile a list of different alternatives should something break. ^^;; 

Anyways, Feisty has been doing quite well so far, except for a bit of sluggish performance while minimising and maximising windows. :)

Well, we'll see what happens to Feisty in a few days' time. :D

If you like virii and spyware, you keep on not using linux........

---

### Post by Lucifiel on 2007-04-05
> **Ptero-4 said:**
> Welcome Luci. For future reference a couple things, before burning a CD check the md5 code of the downloaded iso image, this allows you to ensure that the image didn`t got corrupted during the transfer (due to common transfer issues or a dodgy phone/ethernet cable), use sudo when using command line apps and gksu in GUI ones, and use nano when editing files in the shell (vim and emacs are quite complex for beginners).

And enjoy the stay.

Oh, i checked a lot of things:

- md5 checksum of image
- data was burnt at low speed
- data verification

And so on. :) 

Nano? Errrr... what do you mean by "editing in shell"? I thought that you could edit everything by pressing Alt-F2 while in Terminal mode and by using gksudo gedit pathname followed by filename , one could edit various system files? :)

---

### Post by cantormath on 2007-04-05
> **Lucifiel said:**
> Oh, i checked a lot of things:

- md5 checksum of image
- data was burnt at low speed
- data verification

And so on. :) 

Nano? Errrr... what do you mean by "editing in shell"? I thought that you could edit everything by pressing Alt-F2 while in Terminal mode and by using gksudo gedit pathname followed by filename , one could edit various system files? :)

its crtl+alt+f2 in ubuntu and shell is terminal.........one is just not running inside a gui desktop manager.....

---

### Post by Lucifiel on 2007-04-05
> **medad said:**
> Kudos for sticking with Ubuntu! You sure went through a lot more than I did.  My video card gave me the most problems (motherboard p4m800).

I was wondering if you ever tried to run your system with only with the original ethernet card installed.  After installing Feisty, did you have any further problems with your connection?

Also you mentioned using Konqueror.  It is based off of KDE.  Have you thought about maybe trying the Kubuntu version.  I actually have both Ubuntu and Kubuntu currently running (this is my goof computer).

Wish you the best of luck with your system.

Oh, I wasn't about to pull out the network card 'cos mmm, it's been way too long since I ever removed something from a computer.  

After installing Feisty, I immediately disabled my onboard lan card. I really ought to prevent the drivers from loading as well. Note to self: stay away from Via in the future.

From reading up, don't people use a variety of Gnome + Kde applications? Well, it definitely suits me and the mixture is good for me. :)

---

### Post by Lucifiel on 2007-04-05
> **cantormath said:**
> I feel your pain and want you to fix your problem.  With that I must say that in the future of your linux experience, you will see why this post is as funny as it is.  I see some really top notch folks commenting in here so I will not give advice except to remember that your are not using windows anymore..........and that is usually the answer to the why....

Welcome to the family.

Oho, lol... I already find it amusing 'cos after cramming in so much info about Linux, I think I understand why you're not allowed to edit anything past /home/user with the exception of gksudo gedit or some other command: It's the reason why plenty of users manage to screw up their Windows system files. :D  And another reason why virii can run mess up your entire Windows installation. :p 

Disabling write permission to critical system files ensures a healthy system and also prevents users from accidentally "deleting" or "modifying" a file by mistake. :p I remember once, when I was tinkering around with certain Win98 system files... gee, did I break the o/s! And all I did was add in just three lines.

---

### Post by cantormath on 2007-04-05
> **Lucifiel said:**
> Oho, lol... I already find it amusing 'cos after cramming in so much info about Linux, I think I understand why you're not allowed to edit anything past /home/user with the exception of gksudo gedit or some other command: It's the reason why plenty of users manage to screw up their Windows system files. :D  And another reason why virii can run mess up your entire Windows installation. :p 

Disabling write permission to critical system files ensures a healthy system and also prevents users from accidentally "deleting" or "modifying" a file by mistake. :p I remember once, when I was tinkering around with certain Win98 system files... gee, did I break the o/s! And all I did was add in just three lines.

open terminal

```
sudo -i
```

gedit anything you want........

or
```
sudo gedit 
```
anything you want.

windows is just bad stuff, that is why all of those problems occur. Its never a solution, its just a patch.

---

### Post by Lucifiel on 2007-04-06
> **cantormath said:**
> open terminal

```
sudo -i
```

gedit anything you want........

or
```
sudo gedit 
```
anything you want.

windows is just bad stuff, that is why all of those problems occur. Its never a solution, its just a patch.

Thank you for the tips. :)

I just booted into WinXP. There's one thing I'll miss: the stability of WinXP. :( Ubuntu really needs to do something about cupsys and its' kernel issues if it wants to stop behaving like Win98. Oh, WinXP did sometimes give me registry issues and its' security issues were also a problem too. However, I was able to run most of my programs without having to troubleshoot. Of course, problems on Feisty are understandable but on an LTS like Dapper? 

Oh well. And judging by the 1000 over bugs on Feisty, I suspect they won't be included in Feisty but in the next build. =/ Geez.

---

### Post by Michl on 2007-04-06
There are several ways of editing as root.  One is:
  Alt-F2
   gksudo nautilus

(JUst did it in Feisty.)
Then you can edit as root in a window without using the terminal.  You will
 open a gedit window, for example, if you open a conf file and you can edit
the file then.

Make sure you exit when done and do not remain in that mode.

Ctrl-alt-f2 is something very different!  That gets you into recovery mode.
Of course you can edit there as well.  But that is much less pleasant and
after that you need to reboot.

M

---

### Post by Nekiruhs on 2007-04-06
I had the same problem with permissions and I found a very helpful answer:

Open a terminal and type:

gksudo nautilus

(Assuming your running Gnome, Its probably gksudo konqueror for KDE)

It opens the file manager with root permissions.

That should do the trick, i made a Launcher for it, for gnome, (not certain for KDE) right click the desktop  > Create Launcher and in the command field type in "gksudo nautilus" (without the quotes of course) and save it.

Hope this helps.

---

### Post by Ptero-4 on 2007-04-06
> **Lucifiel said:**
> Oh, i checked a lot of things:

- md5 checksum of image
- data was burnt at low speed
- data verification

And so on. :) 

Nano? Errrr... what do you mean by "editing in shell"? I thought that you could edit everything by pressing Alt-F2 while in Terminal mode and by using gksudo gedit pathname followed by filename , one could edit various system files? :)

Luci. By shell I meant the terminal mode. I recomended the nano text editor b/c sooner or later you`ll end up with a broken xserver (the GUI doesn`t start up), and you`ll need to edit files from the terminal (it usually happens to people whose computer uses an ATI or NVidia video card, those with Intel integrated video hardware doesn`t suffer from this).

---

### Post by Lucifiel on 2007-04-09
> **Ptero-4 said:**
> Luci. By shell I meant the terminal mode. I recomended the nano text editor b/c sooner or later you`ll end up with a broken xserver (the GUI doesn`t start up), and you`ll need to edit files from the terminal (it usually happens to people whose computer uses an ATI or NVidia video card, those with Intel integrated video hardware doesn`t suffer from this).

Ooh right... bah... lol. 

Why do I get the feeling that I'd have been better off using Windows for now(because I can't afford the time to keep tinkering around with system files all day) but that I'd likely regret sticking with Windows and then come back scrambling to Ubuntu? :p

Oh well, and on a note of irony: my computer just sorta died. The machine's going to be hauled off to the hardware shop tommorrow. The problem seems to be the psu again.

---

