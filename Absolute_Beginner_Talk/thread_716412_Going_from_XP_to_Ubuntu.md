---
title: "Going from XP to Ubuntu"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by spartanreborn on 2008-03-05
Alright, I have been seriously considering installing Ubuntu on my pc for quite some time now, but there are a couple issues that I worry about not being able to do.
I use Visual Studio quite a bit for school. What are the chances of me getting it to run through WINE? From what I understand (dumbed down quite a bit, I imagine), I would simply install WINE, then stick the VS installer through that and go from there? Yes, I realize there are alternatives, but for the most part, i have become accustomed to VS's GUI/IDE. Although, if there is an alternative on Linux that can produce similar effects, I'll try those out.

Would the same apply to the various PC games I play?

And, as a sort of general question, for the most part, what in XP will I not be able to do in Ubuntu?
I realize that I will have to do more command-prompt-ing than I did in XP to get most things working, but, as I am a (rather inexperienced) programmer, that really does not bother me.

---

### Post by Dr Small on 2008-03-05
Have you tried out the LiveCD to make sure it works properly and there are no quirks on your hardware?

Dr Small

---

### Post by NightwishFan on 2008-03-05
Do not compare Linux to Xp it is more different than that. As of wine, if it will run in it, it will run mostly the same way. 2 games that work in WINE are Starcraft and Morrowind. Starcraft playing online is tricky. At any rate welcome. I am sure someone more experienced with windows applications can help you find a way. I recommend Linux, but that is because I strongly support free software. If Xp works for you stick with it. Or dual boot. Dual booting is easy just check this page.

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by stevescripts on 2008-03-05
Hmm... do you have a reason not to dual boot?

Also, have you tried the livecd on your box?

Hope this helps.

Steve
(Although I haven't tried it, I doubt that Visual Studio under Wine is much of a solution)

---

### Post by Ptero-4 on 2008-03-05
Except for heavy gaming (but that's what the Wii is for anyway). There's nothing useful that windows have ubuntu doesn't.

Also as for VS, you can use Gambas or MonoDevelop which are very similar IDE's which works with mono (linux equivalent of VB).

---

### Post by spartanreborn on 2008-03-05
Yes, I have tried the Live CD, and everything (seems to) work fine.  
Also, I have considered Dual-booting, but for that, I was considering a larger hard drive. My current is about 70GB, but, for now, I was considering giving Ubuntu 50GB (for my day to day stuff), and giving XP the last 20GB or so (for whatever refuses to work in Ubuntu). Think this sounds like a reasonable ratio?

So I take it most PC games can be difficult to run in Ubuntu?

Edit:
beaten by ptero
Alright, Thanks for the info about Gambas, Ill check that out. 
Also, lets say, hypothetically, how hard would it be to install and run , say, Crysis (or some other big name game) under Ubuntu?

---

### Post by FrozenFox on 2008-03-05
Wine cannot run Crysis. Or at least, playable. It is rated Bronze by Wine's appdb, which means it's possible to run, but not really playable. You have to consider what you are asking: WINE is made by a bunch of developers who are overall not being paid for it to completely (and mostly blindly) recreate the microsoft mega-corporations' Windows libraries open source from the ground up without using the actual windows libraries themselves for the most part and minimal to no references on how to do so. It is not so easy to make everything install and run properly simply because it is not actually from microsoft. It as of yet supports some dx9, but extremely little to no dx10, and heavy stuff like Crysis you are better left forgetting entirely for some time. However, that is not to say it's impossible or will take years, considering wine already plays CoD4 nicely, but as the disclaimer in the wine section says, do not expect it to work. You should also expect a slight performance hit (added on top of the fact that Crysis takes a ridiculous amount of resources) from the games played in wine. I'd guess ~5 fps for opengl games. Large losses for DirectX-only games, between 5-15, sometimes more. Also note that just because someone lists all sorts of complicated things to do in order to get it to work does not necessarily mean you will have to do so, and vice versa.

If you want to see a list of games/programs running and how well they are running and what work is required to run them, please see [http://www.winehq.com](http://www.winehq.com) 's appdb database. Note however that many, many, many of the entries are out of date there and may not accurately reflect the current wine version 0.9.56. 

Cedega is another option, a commercial spinoff of wine designed to run games (5$ a month for a minimum of 3 months. That gets you the program for life and upgrades for 3 months). [http://games.cedega.com/gamesdb/](http://games.cedega.com/gamesdb/)  When you view a game's page, please click "view this game's rating statistics" for an accurate reflection of how well the game plays in cedega, because the original star count on the game and listing page gives an average, not the best rating of all versions of cedega. Ie, its often poor for games nearly perfectly playable that were only recently made working.

---

### Post by spartanreborn on 2008-03-05
Ah. Thats kinda what I figured. 
I am interested in giving Linux a try, but there are a couple things I am not quite willing to give up on.
Thank you all for the information.

Edit:
Ah, so Cedega is similar to wine, but more designed for getting games to run? I'll look into that as well.

---

### Post by SunnyRabbiera on 2008-03-05
well there lies the purpose of a dual boot, linux can do a lot but there is still a lot going against it.
None of it linux's fault but there are some trouble spots.

---

### Post by NightwishFan on 2008-03-05
Remember Linux isn't less, just different. I do agree that there are some apps a few would need to use from Windows, but as I am not a gamer I am pretty much fine.

---

### Post by thane1 on 2008-03-05
Welcome to linux.  If its not a problem, might you consider adding a new hdd?  They're getting really inexpensive these days.  Then you can multi-partition your new drive to accomodate Ubuntu (after a short while you definitely won't regret installing it) and have one or more partitions for backups, storing your data, whatever...  You will even have an available partition to reload Win-duh into, when it gets glitchy as it always does after a relatively short period of time (why do they need so many copies of the same dll's, etc as time goes on?).  After the next time you reinstall Windoze, you can multipartition the old drive to accomodate the next incarnation of ubuntu, Winduh, personal files, backups, etc.  As one other responder alluded to you can then dual boot for the few programs, that are only available (unfortunately) for Win-duh.  This last irritation is the price, that all of us linux users have to bear (IMHO).  In a short period of time I'm pretty sure you'll boot by default into Ubuntu and will resent needing the dual-boot feature to access the occasional Windoze-based program.  Really worth getting into linux  ;-D

---

### Post by sawjew on 2008-03-05
I am not a games player but I have been involved in beta testing for Crossover Office.  Crossover Office is a commercial version of wine specifically designed to run microsoft office and other productivity software.  What I am getting around to is that I have just been invited to participate in beta testing of a new app from Codeweavers (the makers of Crossover Office) called Crossover Games.  This is due for release in the next few weeks.

Here is the announcement given to beta testers;
> CrossOver Games lets you use your favorite OS and still be able
to play the best of PC games, all without having to reboot or use a
different computer.

The plan is for CrossOver Games to be more 'bleeding edge' than CrossOver itself.
That is, we will release early and often to bring the very latest in games
to our users, while keeping the main CrossOver releases on a more stable timetable
so that we continue to focus on stability and reliable use of productivity
applications in CrossOver itself.

We are very excited by the many games that CrossOver Games can play right now.
We are particularly focused on the Steam game download environment, and the many
many games that are available through Steam.  That includes games such as
Half Life 2, Portal, Team Fortress 2, Civilization 4, Peggle, and many, many others.
Our goal is to run every single game available through Steam.

We are also supporting the popular multiplayer online games, including World of
Warcraft and Guild Wars.

Of course, we also hope that many other games will 'just work'.  In theory, any game
using DirectX (up through version 9) or OpenGL can be run with CrossOver.
Sadly, many games may fail due to copy protection systems that do not yet work in CrossOver.  
We are pleased to see that some software developers are now providing 'no-cd' patches for older
games; those patches may enable games to run in CrossOver that wouldn't otherwise work. 

So if you wait a little while you may have another very viable option.  If you want to give Crossover Office a try you can go [here]("http://www.codeweavers.com/products/") and download the trial version.  A license for Crossover Office costs $39.95US so I would assume Crossover Games will be similarly priced.

Have fun with ubuntu :biggrin:.  Once you've started it's very hard to go back to windows, particularly if you're forced to use Vista.](*,)

---

### Post by NoSmokingBandit on 2008-03-05
> **Ptero-4 said:**
> Except for heavy gaming (but that's what the Wii is for anyway). There's nothing useful that windows have ubuntu doesn't.


Completely wrong. Photoshop. 'nuff said.

There are pro's and cons of each system. Try them both and see what works.

---

