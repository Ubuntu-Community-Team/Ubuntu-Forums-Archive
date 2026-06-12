---
title: "Upgrading hoary to breezy - help :)"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by TikkiRo on 2006-01-05
[FONT="Comic Sans MS"][SIZE="3"][COLOR="Purple"]Had hoped the info in the Installation section might enlighten me, but couldn't figure out this bit even:

Through Synaptic Package Manager

   1.      Open up Synaptic Package Manager
   2.      Change your repositories to look for Breezy
          
              From

                     URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
                     Distribution: hoary
                     Sections: main 
              To
                     URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
                     Distribution: breezy
                     Sections: main restricted

   3.      Click on "Reload"
   4.      Click on "Mark All Upgrades"
   5.      Click on "Apply"

Perhaps I'm just truly DUMBO here but I couldn't figure out where to head to change the repositories - looked everywhere in Synaptic but nothing looked remotely close to somewhere I could put this lot in.  I've already downloaded the package as a Cd install, but no means of sticking it ON a CD to install it - DUHH.  Thought it might just run somehow from within Hoary and update itself (as windows does nicely!).  Anyone enlighten me on the better way to do this one perhaps.  And while I'm here, thanks SO much to all those who've already helped over the past week and stopped me from just giving up entirely - instead I'm finding myself spending more time in linux than windows and eager to learn more :D [/COLOR][/SIZE][/FONT]

---

### Post by FLeiXiuS on 2006-01-05
sudo apt-get update
sudo apt-get dist-upgrade -y -f
sudo apt-get upgrade -y -f

A combination of the above lines should do the trick.  I run them a few times to just make sure every APPLICATION is updated.  If there is a more simpler way, have at explaining.  This is the easiest to me :-)

---

### Post by Gustav on 2006-01-05
It's under settings -> repositories?(I'm not sure mine is in swedish)

Or you can edit the file /etc/apt/sources.list and change all hoarys to breezys and then
```
sudo apt-get update
sudo apt-get dist-upgrade
```
in the terminal

---

### Post by Yleeyas on 2006-01-05
Hello TikkiRo,

I went through this just last night, and as with you I had problems deciphering the instructions. Here's what they mean, ie; the parts they left out:

 1. Open up Synaptic Package Manager

Select the 'System' button in the main toolbar at top of screen.
Select 'Administration' from dropdown menu
Select 'Synaptic Package Manager' from that dropdown menu
This opens the SPM

 2. Change your repositories to look for Breezy

Select the 'Settings'  from main menu at top of SPM
Select 'Repositories' from dropdown menu; a window with a list of 'hoary' repositories opens
At bottom of that window select 'Settings' which opens a settings window
Check the 'Show disabled software sources' and Close

Ignore the CD entry for now.
Select each Repository inturn and edit all instances of 'hoary' to 'breezy'
(Don't forget to go back to settings later and uncheck the 'show disabled' )

 3. Click on "Reload"
4. Click on "Mark All Upgrades"
(Somewhere in here I selected the 'Smart Upgreade' or something like that)

5. Click on "Apply"
Note that when you get the 'Apply Changes' window, be sure to toggle the little 'Terminal' selection near the bottom of the window, this lets you watch whats going on, and incase there is any dialogue to respond to

Hope this helps, the whole upgrade took me less than an hour.

Yleeyas

By the way, this downloads everything from online , so you won't need the CD for this.

---

### Post by TikkiRo on 2006-01-05
YO - success of sorts - at least it's in the process of just downloading around 1200 files so presuming so.  Thanks SO much for your info Yleeyas - it let me see that I had misinterpreted the instructions in the guide - I was looking for a means to cut/paste the info - didn't realise it meant me to manually edit each entry as you showed much more clearly (perhaps you should send in your response to the Wiki!! - way more understandable for me at least!).   So we'll see how far it gets this time - suspect I'll run into some other problems at some point up ahead yet, but so far so GOOD :). Thanks again TKR

---

### Post by Yleeyas on 2006-01-05
Hello again TikkiRo,

Glad to be of some help. I'm a total newbie at this as well, but I couldn't resist responding to your query, because that's exactly what I felt when I started the upgrade last night.  I won't critisize the wiki writer, cuz I've done the same, that is just assumed too much prior knowledge/experience on the part of the reader.

1200 files?  I can't remember how many I got but that sounds right.

I'll stay tuned here if I can be of any other help. I'm just in the process of using Synaptic to get Thunderbird installed. Well good luck to both of us:smile: 

Yleeyas

PS, I'm guessing there is an easier way to edit the repositories, probably using the gedit of sources.list, for example, then running synaptic. Oh well, live, stumble and learn.

---

### Post by TikkiRo on 2006-01-05
Ok - got that bit done - do I take it the next step now is to reboot?   Still a few error msgs floating around in Synaptic which now won't load the repositories manager so am hoping a reboot's the answer BUT before I make that move wanted to see what you did next?

---

### Post by Yleeyas on 2006-01-05
Hello TikkiRo,

Well, I didn't try to load the repository manger before I rebooted, so I can't say about that.

I assume you were watching the terminal window in the 'apply changes' window, and that's where you saw the synaptic errors.

Well all that's left is a reboot, I guess.
I hope someone more knowledgable than me is watching us, and will speak up soon;) 

The breezy boot sequence is different (more professional) than the hoary, so that will be your first hint of success, or not.:smile: 

Go for it, and good luck
Yleeyas

PS: I'm gonna signoff for awhile, got some chores to do, but I'll be back.

---

### Post by TikkiRo on 2006-01-05
[COLOR="Purple"]Oh heck - sounds like it could indeed be fun then.  Just as well it's not my primary OS eh?   Just really playing about in it for fun, but have spent a long time setting up packages like Firefox etc.  Have you come across a good calendar/task manager similar to Outlook's offering by any chance.  I know Evolution does the lot just as I want BUT it's email editor is dire to say the least in my opinion, so unless perhaps I've options on improving that section separately some way I'd need to find another solution.  Thunderbird has great email options but that's it obviously, so I need something to combine the two  - fussy aren't i?  Doing some other stuff just now, so not quite ready to reboot as yet, and it's gettin glate now too so I may well just leave all until I boot up tomorrow to see what happens :).  Thanks again so much for your input tho - been a HUGE encouragement I can tell you.  TKR[/COLOR]

---

### Post by Yleeyas on 2006-01-05
Hello TikkiRo,

Well I don't use a 'calendar/taskmanager' of any sort, but you might want to look into extensions for Firefox or Thunderbird. Also check out [http://www.mozilla.org/download.html](http://www.mozilla.org/download.html)

They have a calendar project in developement, but I don't recall what it's called. If I think of it, or run across any info I'll keep you in mind.

I'll catch you later.

Yleeyas

---

### Post by TikkiRo on 2006-01-06
S'okay - just going to work with Evolution for now and make the most of it somehow or other.  Did get my upgrade working fine except for the fact that Automatix doesn't seem to recognise it annoyingly.  BUT I'll figure that one out yet.   THanks again for all your input.  Got another problem now with Real Player so you'll no doubt spot that query shortly. :)

---

### Post by Yleeyas on 2006-01-06
Hello TikkiRo,

Glad to hear your up and running.  Yes, I'm in the process of getting all the little bells and whistles going here too, so I'll see you around. :smile: 

Yleeyas

---

