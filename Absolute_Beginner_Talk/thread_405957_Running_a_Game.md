---
title: "Running a Game"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by NeroBloodfire on 2007-04-10
I am an avid gamer and I have a second computer devoted to Ubuntu. I need to know how to run my games on here before I convert my second computer to Linux.

I correctly installed Wine and installed Dungeons and Dragons Online but when I doubleclick the Icon to get started with the program nothing happened. I went into properties and clicked the run as program button in there. Then I even tried running it in terminal but it gave me a series of comments.

nero@Vendetta:~$ '/home/nero/Desktop/Dungeons & Dragons Online - Stormreach.desktop' 
/home/nero/Desktop/Dungeons & Dragons Online - Stormreach.desktop: line 1: [Desktop: command not found
/home/nero/Desktop/Dungeons & Dragons Online - Stormreach.desktop: line 4: Dragons: command not found
install the Windows version of Mono to run .NET executables
/home/nero/Desktop/Dungeons & Dragons Online - Stormreach.desktop: line 7: Files/Turbine/Dungeons: No such file or directory
/home/nero/Desktop/Dungeons & Dragons Online - Stormreach.desktop: line 7: Dragons: command not found

I tried installing mono but I don't believe it worked. Help with that would be appreciated as well.

Please give me any advice you can to help me figure this out.

---

### Post by Jussi01 on 2007-04-10
Your problem is nothing but the spaces in the command line. take out the spaces or replace them with _ and then try again. 

Hope this helps

---

### Post by NeroBloodfire on 2007-04-10
No that didn't seem to work it. In fact it seemed like It couldn't find the file when I removed the spaces.

---

### Post by Nedtlele on 2007-11-27
Bringing this thread back to life :)

Does anyone have Dungeons and Dragons Online running in Ubuntu 7.10 ?

Is it even possible?
Done plenty of searches for info,  all have come up empty.

If I can get that working I could uninstall windows !

---

### Post by OldTimeTech on 2007-11-27
Does the wine info say it runs D&D.....

Check this out and see if it answers your questions
[http://wiki.winehq.org/](http://wiki.winehq.org/)

---

### Post by yabbies on 2007-11-27
looks like a lot of work
but worth a shot and you might learn something

here you go

[DDO:StormReach]("http://cedegawiki.sweetleafstudios.com/wiki/Dungeons_and_Dragons_Stormreach")

---

### Post by Nedtlele on 2007-11-27
Excellent, thanks!

I was searching for DDO and Ubuntu.

---

### Post by Nedtlele on 2007-11-28
Wow it's complicated,
 quote"   I assume for ease of mind and ease of this install process that YOU have a CLEAN version of wine. And a CLEAN 

.wine directory. Another words, mv .wine .wine.org and wineprefixcreate BEFORE you attempt this 
operation.

Things needed: 1. DDO 2. Wine 0.9.17 (latest CVS) 3. Patience

  I am using Fedora Core 5 so please make sure to change your package manager on what ever distro you 
are using 
(ie emerge, yum, etc). Or get wine from cvs and build it from source."


......and I'm lost.:confused: :lolflag:

Its a shame that the only guides available,  seem to expect you to know what they're talking about with the likes of "get wine from cvs, and build it from source" or "change your packet manager" and "Another words, mv .wine .wine.org and wineprefixcreate"....


Same as this TV card I installed, took me four days of reading outdated over complicated guides that led me on a wild goose chase. To eventually  with some help of a kind person on #linuxtv,  narrowing down some basic steps, that let me install it and have it running in just a few minutes.


Well, a few weeks searching on how to do all these things, and I will post a guide, that new Ubuntu linux users can use to get their D&D up and running ASAP, 
if it is at all possible :)

Now off on my adventures!

---

### Post by Sethalos on 2007-11-28
I feel your pain. I've been trying to get PKR to work now for about 8 months and still no luck. I know this is not a Linux issue but that of the gaming companies not porting to any other OS than Windows, but it is frustrating for me to have to keep a dual boot of WinXP.

---

