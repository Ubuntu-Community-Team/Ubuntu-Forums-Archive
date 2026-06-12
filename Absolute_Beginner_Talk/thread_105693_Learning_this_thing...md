---
title: "Learning this thing.."
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Niz972 on 2005-12-19
alright.. so ive just switched from windows xp to this.. ive heard its a lot more flexible and such. Which i dont use the computer all too often.. when i do i limit myself to playing a game whenever im bored, which is world of warcraft or something of the sort. Which i am currently trying to get help with.. if you're willing to help me, give me a hollar, i have aim(jmej0rado) and skype (niz972). 

ok, first problem, im used to just pulling up c:program files/program/music blah blah.. how the heck do i do anything like that on this ubuntu? I have installed Amule to get mp3s, but a problem.. where did they save to? i dont understand.. lol. and how do i load them to mplayer? if anyone is willing to help out a complete newb.. please let me know. aim me, skype me, anything.. just need some guidance. Thanks in advance.

---

### Post by adie273 on 2005-12-19
Unless you changed the settings in Amule, all your Music you download via it should go to...

/home/YOUR USERNAME/.aMule/Incoming/

however, when you goto your home folder, this folder might not show up because it may be hidden, to see it goto your places menu on the taskbar ---> Home Folder ---> Then when it opens goto 'View' -----> And select 'Show Hidden Files'

This should now let you see the '.aMule' folder.

I don't use mPlayer for my music, didn't know you could, but i've only used ubuntu for a few months. Although I do use XMMS, and would recommend going into synaptic and installing XMMS. If you do, just goto Applcations ---> Sound & Video ---> XMMS ---> Then in the very top left hand corner of XMMS is a tiny button ---> Press it and select 'Playlist Editor'. This will open the playlist that will list all the music you add to XMMS. At the bottom of the playlist editor is a small button that says file. If you press it and hold it down, the button will expand to show 3 options (File, Dir and URL).----> If you select DIR and then browse for the /home/YOUR USERNAME/.aMule/Incoming/ directory, it will add all your current music to XMMS.

All you need to do then, is select the song you want to play.


Hope that helps in some form.

Good Luck

---

### Post by canadianwriterman on 2005-12-19
I don't use aMule at all, but I know in LimeWire, you can set your own default download directory. Assuming that aMule has the same option, you can create a new folder in your Home directory, then set it in aMule's preferences or options.

---

### Post by markosus on 2005-12-19
Hello i new here in Ubuntu.I just install Ubuntu and i think by the first steps,it is ok.Till now i was Windows user.But now is time to move forward.I have a question.Is amule only p2p program who support ed2k links?Because i have access to web site who share best ed2k links and i need any good program to download that.I am try to install amule but no go,so far.

---

### Post by Niz972 on 2005-12-20
hmm.. when i try to play the music on mplayer.. i have no sound.. nor on any other player.. am i missing something that i need to install..? or is it because im runing skype?

_edit. Ok.. well i've figured out it only lets me play the music when im not on skype.. is there anyway to configure it to play music while on skype with someone?

---

### Post by adie273 on 2005-12-21
I've never used Skype, and since i'm relatively new to linux, I don't know a great deal about how the sound works yet. But maybe Skype's sound settings is upsetting everything else when its in use may be the problem, i'm not sure.

All I can say is to take a look at...

[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

and see if it helps any in sorting the sound. ESD is the Gnome default.

Adie

---

### Post by lleb on 2005-12-21
[QUOTE=Niz972]alright.. so ive just switched from windows xp to this.. ive heard its a lot more flexible and such. Which i dont use the computer all too often.. when i do i limit myself to playing a game whenever im bored, which is world of warcraft or something of the sort. Which i am currently trying to get help with.. if you're willing to help me, give me a hollar, i have aim(jmej0rado) and skype (niz972). [/quote]

visit [www.transgaming.org](www.transgaming.org) and sign up for Cedega.  it will run you $5 per month with the first 3 months being in one lump sum.  It runs WoW great.  I use it all the time for playing WoW and get better performance out of my Debian box then i did running Windows on this exact same hardware...  Ubuntu is now one of the top favorite distros for running Cedega.

> 
ok, first problem, im used to just pulling up c:program files/program/music blah blah.. how the heck do i do anything like that on this ubuntu? I have installed Amule to get mp3s, but a problem.. where did they save to? i dont understand.. lol. and how do i load them to mplayer? if anyone is willing to help out a complete newb.. please let me know. aim me, skype me, anything.. just need some guidance. Thanks in advance.

*grins*  yes the linux file system is very different then windows.  first off there is a HDA1 icon on the desktop (default for edubuntu, sorry have not messed with ubuntu or kbuntu) when you double click on that icon you will get something that is as close to the windows explorer as you will get.

from there you can navitgate around a bit.  most things that you download will be saved in the following directory:

/home/user_name  were user_name is the user you are loged in as.

as you are running ubuntu you do not have to worry about being loged in as root so that is a nice plus for security.

once you are in the /home/user_name directory you can navigate that just like you would via the windows explorer and it should be rather intuitive once you click on a few directories and folders to get the hang of it.

now if you are using the terminal you will be using the GUI and that will be a big differance then your windows experiance as odds you have have not used DOS in many years.

few basic bash commands (command line or CLI) to get you started

ls = list the directory
ls -l = long list  
ls -la = long list with all details.  examples:

```
ls
3rd_quarter.htm.html     eme2040             projects.html
activities.html          evaluations.html    projects.html-1
activities.html-1        homepage.html       sidekick.html
autobiography.html       homepage.html~      tbrunkow.jpg
background.jpg           index.html          test.html
background.txt           index.html-1        test.rtf
class_schedule_8-05.pdf  journal#5_4214.sxw  tracy_pic.html

```

```
ls -l
total 1128
-rw-r--r--  1 ray ray   9732 2005-07-16 12:25 3rd_quarter.htm.html
-rw-r--r--  1 ray ray    717 2005-07-23 19:48 activities.html
-rw-r--r--  1 ray ray   2442 2005-07-10 15:25 activities.html-1
-rw-r--r--  1 ray ray   2791 2005-07-23 19:50 autobiography.html
-rw-r--r--  1 ray ray    959 2005-07-10 15:51 background.jpg
-rw-r--r--  1 ray ray    287 2005-07-10 16:47 background.txt
-rw-r--r--  1 ray ray 365781 2005-07-16 20:13 class_schedule_8-05.pdf
drwxr-xr-x  6 ray ray   4096 2005-07-29 15:50 eme2040
-rw-r--r--  1 ray ray   1353 2005-07-23 19:57 evaluations.html
-rw-r--r--  1 ray ray   5019 2005-07-24 19:33 homepage.html
-rw-r--r--  1 ray ray   4984 2005-07-24 19:33 homepage.html~
-rw-r--r--  1 ray ray    607 2005-07-10 16:30 index.html
-rw-r--r--  1 ray ray   2497 2005-07-10 15:01 index.html-1
-rw-r--r--  1 ray ray   6729 2005-10-25 12:39 journal#5_4214.sxw
-rw-r--r--  1 ray ray   1216 2005-07-23 19:51 projects.html
-rw-r--r--  1 ray ray   2897 2005-07-10 15:04 projects.html-1
-rw-r--r--  1 ray ray   3407 2005-07-10 17:34 sidekick.html
-rw-r--r--  1 ray ray 679589 2005-07-24 19:21 tbrunkow.jpg
-rw-r--r--  1 ray ray    522 2005-07-23 19:59 test.html
-rw-r--r--  1 ray ray   2518 2005-07-10 15:35 test.rtf
-rw-r--r--  1 ray ray     47 2005-07-10 16:12 tracy_pic.html

```

```
ls -la
total 1136
drwxr-xr-x   3 ray ray   4096 2005-10-25 12:24 .
drwxr-xr-x  78 ray ray   4096 2005-12-21 11:55 ..
-rw-r--r--   1 ray ray   9732 2005-07-16 12:25 3rd_quarter.htm.html
-rw-r--r--   1 ray ray    717 2005-07-23 19:48 activities.html
-rw-r--r--   1 ray ray   2442 2005-07-10 15:25 activities.html-1
-rw-r--r--   1 ray ray   2791 2005-07-23 19:50 autobiography.html
-rw-r--r--   1 ray ray    959 2005-07-10 15:51 background.jpg
-rw-r--r--   1 ray ray    287 2005-07-10 16:47 background.txt
-rw-r--r--   1 ray ray 365781 2005-07-16 20:13 class_schedule_8-05.pdf
drwxr-xr-x   6 ray ray   4096 2005-07-29 15:50 eme2040
-rw-r--r--   1 ray ray   1353 2005-07-23 19:57 evaluations.html
-rw-r--r--   1 ray ray   5019 2005-07-24 19:33 homepage.html
-rw-r--r--   1 ray ray   4984 2005-07-24 19:33 homepage.html~
-rw-r--r--   1 ray ray    607 2005-07-10 16:30 index.html
-rw-r--r--   1 ray ray   2497 2005-07-10 15:01 index.html-1
-rw-r--r--   1 ray ray   6729 2005-10-25 12:39 journal#5_4214.sxw
-rw-r--r--   1 ray ray   1216 2005-07-23 19:51 projects.html
-rw-r--r--   1 ray ray   2897 2005-07-10 15:04 projects.html-1
-rw-r--r--   1 ray ray   3407 2005-07-10 17:34 sidekick.html
-rw-r--r--   1 ray ray 679589 2005-07-24 19:21 tbrunkow.jpg
-rw-r--r--   1 ray ray    522 2005-07-23 19:59 test.html
-rw-r--r--   1 ray ray   2518 2005-07-10 15:35 test.rtf
-rw-r--r--   1 ray ray     47 2005-07-10 16:12 tracy_pic.html

```

cd = change directory

```
ray@p4ssmahome:~/tracy2$ cd ..
ray@p4ssmahome:~$ cd tracy2

```

as you can see that took me out of the /tracy2 directory and back to my home directory.  then i cd back into the tracy2 directory.  the ".." puts you UP one level.  

the linux file system is like a tree that goes backwards from what you would thing.

/

is the base or lowest level thus it is called ROOT  everything comes off of the / directory.

so / is the first then you have many others off of that like /usr or /home or /var  those are all different directories, now that can do deeper so /home can have its own set of directories like /home/user1  or /home/user2 etc...  under those you can have more.

most of what you will do will be in your /home/user directory.  things you download for yourself or work with will be there.

now things you use apt-get to install will be handled by apt and put in the proper path for the user to access so you do not need to really worry about that.  for started sticking with apt to handle your installs of software will be the easiest way to deal with things and require the least amount or learning curve.

that should get you started, good luck, and keep posting here and i also sujest finding a local LUG (linux user group) as well as becoming a member of [http://www.linuxquestions.org](http://www.linuxquestions.org) as it has loads of members that know their stuff around linux too.

---

