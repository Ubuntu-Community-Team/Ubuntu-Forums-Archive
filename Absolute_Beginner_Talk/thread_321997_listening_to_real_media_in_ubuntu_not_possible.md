---
title: "listening to real media in ubuntu not possible?"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-19
how to listen to songs from

[http://www.musicindiaonline.com/musi...strumental/10/](http://www.musicindiaonline.com/musi...strumental/10/)

i have installed real player . but i couldn't listen. if you can listen in ubuntu pls reply.

---

### Post by macogw on 2006-12-19
Um, can you post the whole link?  That's a broken one.  The ... is literally showing up in the URL

Does it pop up this:
> Firewall Check
Port
	
Can Access?
554
	
No
RealPlayer might not work! 
1755
	
No
Windows Media Player might not work! 
???

If so, 
```

sudo apt-get install firestarter

```
and use that to open up Port 554 of your firewall.

---

### Post by tony2 on 2006-12-19
macogw thanx for pointing it 

> 
[http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/](http://www.musicindiaonline.com/music/ut/s/hindustani_instrumental/10/)


---

### Post by macogw on 2006-12-19
I just went to the main site and picked a random song to get that to pop up.

---

### Post by tony2 on 2006-12-19
good. but were you able to listen to any of the songs?

---

### Post by macogw on 2006-12-19
See earlier response.

---

### Post by tony2 on 2006-12-19
ok i assume you were able to listen. can you tell me why i am not able to listen ? i have real player installed .

---

### Post by macogw on 2006-12-19
I didn't edit my firewall to listen, but it seems that the firewall is the problem.  If you re-read my first response, you'll see instructions for installing firestarter which is a front-end to your firewall.  Follow those, then type "sudo firestarter" in the terminal.  Just click "next" a few times.  When you get a window with 3 tabs in it, go to "Events" then try listening.  See what happens when you click to listen.

---

### Post by tony2 on 2006-12-19
hi now only i read [this]("http://www.ubuntuforums.org/showpost.php?p=1908392&postcount=2") and i am installing the firestarter.

it installed. now what do i do?

i installed but i don't see firestarter in the applications menu

---

### Post by tony2 on 2006-12-19
> and use that to open up Port 554 of your firewall.

how to do this?

---

### Post by macogw on 2006-12-19
I haven't used it before but I *think* (from looking at some documentation) that if you click on the listen thing, an event will appear on your firestarter events menu.  Double-click or right-click on that event (I think) and I think this option is the one you want:

Allow Inbound Service for Source
This action allows only this specific source to access the service in question. This is known as stealthing, no other host except the source will be aware that the service even exists.

By the way, if you don't have the visuals of it yet, you open the terminal and type in "sudo firestarter" and click next a bunch then there's an "events" tab.

---

### Post by Sef on 2006-12-19
> type in "sudo firestarter"

Type in "gksudo firestarter" (without the quotes.)

From [Root/Sudo]("https://help.ubuntu.com/community/RootSudo"):

>     *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.



---

### Post by macogw on 2006-12-19
Sef, sudo works too.  At least, it worked for me.

---

### Post by tony2 on 2006-12-19
macogw, sef - under events it is showing blocked connections. i installed and run firestarter successfully.

---

### Post by macogw on 2006-12-19
When you try to play one of the files, does a new blocked connection appear?  If so, tell it to allow that connection.

---

### Post by tony2 on 2006-12-19
when i click on a song popup comes with the player embedded in it. and then it says 

> ERROR: Methods missing

and in the firestarter under events tab it is showing 

> Blocked Connections

see the attached screenshot [here]("http://img367.imageshack.us/img367/8986/screenshotti4.png")

---

### Post by tony2 on 2006-12-19
pls see the screenshot attached in the previous post

---

### Post by macogw on 2006-12-19
It's not listing any blocked connections, so I'll just try to figure out how to open up the port for ya.

Real Media files will play in general, by the way, it's just the streaming that isn't working.

---

### Post by tony2 on 2006-12-19
yes u r right the streaming media is not working. how to rectify it? thanx.

---

### Post by tony2 on 2006-12-19
did u find a solution for this problem?

---

### Post by macogw on 2006-12-19
Try going into firestarter and clicking Policy.  Click Add New.  Type 554 into "port" and mark "IP, host or network".  In the box next to that type [http://musicindiaonline.com/](http://musicindiaonline.com/) and in the Name choose "HTTP"

hopefully that should work

---

### Post by tony2 on 2006-12-19
no use. i did as you said created a policy applied it in firewakk,  its showing errors: methods missing.

---

### Post by TooRight on 2006-12-20
How did you install real media? I mean, what method did you use? Did the install work? Have you checked it using downloaded .rm files?

---

### Post by macogw on 2006-12-20
TooRight, it pops up saying that port 554 is closed and is needed for RM to stream.

---

### Post by Arschbohrung on 2008-07-09
Hello Mates!

I got Ubuntu 8.04 installed only yesterday and I am having the precise problem. I have not meddled the firewall settings as yet. (sshh... SKIVING!)

please let me know if you got this problem solved.

cheers!

---

