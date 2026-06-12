---
title: "Linux version of Windows Media Center"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Miikee on 2008-04-09
So, this is my first post on this website,  I installed Ubuntu Feisty on my laptop not too long ago as a dual boot with XP.  I am amazed and absolutely loving it, pretty much never use XP.  I always see this website when I google little tweaks I need and fixes, and decided to join.  I'm trying to use and learn commands through the terminal as much as possible.  Anyhow...

I was walking past my roommate with Vista talking about how great I think Linux is.  And he's watching live TV on it with media center!  I don't have that yet.  I need it.

And so I started googling again.  Found MCE and watched a video on it:
[http://www.downloadsquad.com/2007/03/21/linux-mce-looks-hot/](http://www.downloadsquad.com/2007/03/21/linux-mce-looks-hot/)
I didn't really watch the entire thing or listen too much, but that looks sweet!

However it's an entirely new OS.  I don't really want to go through installing a third OS + kubuntu  (I'd like to hang onto XP just a little while longer for some programs).  But I want most of the perks of MCE (live TV, DVR, Organization, etc. --Maybe even home control later on.)  Plus would like to be able minimize whatever I would be doing in MCE and use my Ubuntu set up.

**My question: **
What program or programs could/should I get to emulate an install of MCE.
Or is there a way to install MCE on Ubuntu so that I can minimize and use Ubuntu?
I found 'MythTV' how similiar to MCE is this... what would it be missing, etc.?

I would generally Just google the hell out of something like this, but I got a LOT of homework and would like to try watching some TV in my room after I'm done (will be really late).  So any advice would help me mellow after a night load of Physics and Calculus.

Thank you in advance.

---

### Post by Tatty on 2008-04-09
All MCE appears to be is a linux distro with MythTV installed by default.

Mythtv is available in the ubuntu repos, and with the mythbuntu package it is really easy to install.  This link will guide you through installing: [https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

I use MythTV in my room as part of my main media-box.  You can watch TV, record TV and stream live or recorded shows to any computer in your house.

---

### Post by miesnerd on 2008-04-09
MCE isnt really my area, but first off, congrats dude. 
Welcome to the other side.
Per the MCE thing, if you're looking to add MCE, you can. 
This website below says that MCE is an add on for ubuntu (another hint is that its in vesrion 0710 (like ubuntu 7.10), right?
[http://www.linuxmce.org/](http://www.linuxmce.org/)

Someone on here might know the commands exactly, but I'd imagine you'll have to do two steps basically:
**1. Add the repos.** If you're only a few days into using Ubuntu, I wont bog you down with the details of using repos, but suffice to say that right now, your machine doesnt know to go out and look for software at the MCE repo. You need to add a line in your /etc/apt/sources.list file.
Since you said you're new at the terminal you'll go into the terminal, as a normal user and type:
sudo gedit /etc/apt/sources.list
then your password for root access.

you'll add something that will look like this:

# Remastersys
deb [http://www.remastersys.klikit.org/repository](http://www.remastersys.klikit.org/repository) remastersys/

(i just took the bottom two lines of mine-- remastersys is a program for backing things up; the top line (with the # symbol tells apt-get that that line is not a source; to ignore itl the second line will tell apt-get, and synaptic to go to that site and look for files possible for downloading.

2. Find out what packages you need.  Someone on a forum such as this one (below)
[http://forum.linuxmce.org/](http://forum.linuxmce.org/)
can probably tell you exactly what it should be, but, I'd imagine from the terminal, after following step 1 (which they can also probably help you with) you can "sudo apt-get install package1 package2 package3... and so on. You should be good then.

Good Luck, and congrats on the switch.

---

### Post by miesnerd on 2008-04-09
as a second option, if you dont want to go through all of that, you can just download Linux MCE (like the .iso file) and mount it (using a program called Gnome mount iso) and use VMware to give it a try.
Both of those programs, to my knowledge, are in Ubuntu's main repos, so you should be able to use the add-remove GUI to select and install those.

---

### Post by MrFSL on 2008-04-09
You like Ubuntu? You like MythTV? 

Try MythBuntu: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by Miikee on 2008-04-09
I'm liking both the mount idea along with the mythbuntu idea.  I havn't read too much on the mythbuntu yet, because I'm already reading too much on this MCE stuff as it is while doing this homework. 
What would I be losing in comparison to MCE by just going with the the mythbunbtu idea?

Also everywhere I scan through on the MCE forums says it doesn't work on straight ubuntu, that I need kubuntu (except for MCE 1.0, i guess the newest is 1.1).  They also say that 1.0 modify's Ubuntu's configuration alot... bad because I'm stupid and can't fix things like that.

Still, I would like to understand the mounting idea.   By mounting would it be running as if it were installed?

Thank you for your quick responses.  I am leaning more toward Mythbuntu and would like to know what I'd miss out on, if it's too much stuff I might try to go the mounting method.  But by mounting it seems like I'd have to install KDE to get it to run without problems.  Please let me know your suggestions.

This forum is nice I'm gonna use this more often!

---

### Post by Miikee on 2008-04-09
So, I read a little more into the Mythbuntu idea and I guess that is an entire distro as well.  I'm really just looking for and add-on to ubuntu that is similar to MCE.  I guess it might be kinda dumb to try and find an add-on that has same features as entire distros.

Anyhow, I think I may just go with MythTV for now.  Any suggestions about how to get more features of MCE added onto my Ubuntu would be greatly appreciated.  Thank you for your help.

If anyones wondering, I'm screwed for tomorrow's homework.

---

### Post by Mazza558 on 2008-04-09
Try Elisa. It's in the early stages at the moment, but it's getting there.

If you want to try something for XP, try Media Portal, which has more functionality than vista's media center.

---

### Post by MrFSL on 2008-04-09
>  So, I read a little more into the Mythbuntu idea and I guess that is an entire distro as well. I'm really just looking for and add-on to ubuntu that is similar to MCE.

It can be installed as a distro or it can be installed from the repos (read closer)

I re-read your post and perhaps you are looking too far - from the original post:
> I was walking past my roommate with Vista talking about how great I think Linux is. And he's watching live TV on it with media center! I don't have that yet. I need it.


You don't need a Media Center application to play live TV. You can play live tv using mplayer without all the extra. - Mplayer can be installed from the repos.

---

### Post by mgmiller on 2008-04-09
If all you want to do is watch live TV, assuming you have a TV tuner card in your machine, why not try installing tvtime?  It will scan for channels the first time you run it and then you can watch TV in a window or full screen easily.
You can search for it in synaptic or you can install it from the command line:
```
sudo apt-get install tvtime
```

---

### Post by wolfen69 on 2008-04-09
some cards will not work with tv time. that is why i use vlc for tv. post back if any problems.

---

### Post by kodiakcb on 2008-04-10
LMCE is actually much more than Windows MCE.  It is a whole house media, security and automation system.  It is based on Kubuntu 7.10 but you can add it on to your current installation but you will need to add the kubuntu  desktop.

MythTV sounds more to what you want.  It can also be added from the repos but will require some setup to get to work.

If all you want is live tv, as suggested in a previous post, go with vlc.  It will require less fiddling with and is very useful for other things.

Whichever you will decide on, you will need a tv capture card if you do not have one already.  I highly recommend the PVR150 as it will offer the most flexibility.  It is one of a few cards with built in mpeg2 hardware encoding so it requires less cpu time for most applications.

I am currently setting up a LMCE system as I build my home theater so I can integrate my media server, X10 system and security cameras.  

Later  :popcorn:

---

### Post by mgmiller on 2008-04-10
> If all you want is live tv, as suggested in a previous post, go with vlc. It will require less fiddling with and is very useful for other things.

I will have to disagree with you on this point.  Vlc is a very useful application, but for watching TV from a tuner card it requires a fair amount of poorly documented fiddling to set up.  It also lacks, as far as I know, the ability to easily change channels from the keyboard.

Tvtime, on the other hand, is very easy to set up and very intuitive to use.  Especially if you have a well supported tv tuner/capture card, like the PVR 150 that you mention in your previous post.  The program will almost configure itself and scan for all available channels during the install process.

On the other hand, if he really wants to learn a lot about configuring his system, a myth or LMCE install will give him the opportunity to dig deeply into the nuts and bolts of the OS.  

My take on reading the forums for myth tv is that it almost never goes smoothly and can require many hours of fiddling to get working, and, once it is working, you are rolling the dice every time you do any kind of system update.  Also, although mythbuntu is in the repos, AFAIK, it's been broken from the beginning and does not work.

Admittedly, the last time I looked seriously at this was about a year ago, so maybe it's become a bit more user friendly since then.

---

