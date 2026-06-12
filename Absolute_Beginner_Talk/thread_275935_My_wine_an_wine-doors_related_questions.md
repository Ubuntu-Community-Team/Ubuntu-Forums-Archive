---
title: "My wine an wine-doors related questions"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by trommas on 2006-10-12
I want to run my windows apps on ubuntu (surprise!), so I have been paying attention to winehq.org for a long time. Now it's time to try it out! Here are my queries:

1. I have a lot of applications installed on my windows drive. Do I need to install my windows applications *within* wine, or can I just execute the application (ex. Stronghold.exe) from my windows drive?

2. This is the best guide I've found: [http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)
But it seems extremly large (and maybee outdated?), also it uses wine-tools which is a discontinued project. Is wine doors: [http://www.wine-doors.org/](http://www.wine-doors.org/)
better to use? Have anyone tried this?

3. My primary need is for games to work. Maybee I should rather use Crossover or Cedega? (I must admit that the wine project does appeal more to me)

Any feedback would be greatly appreciated!

---

### Post by Sirkent on 2006-10-12
I'm no expert on Wine, but hopefully I can give you some pointers from my experiences.

1. As far as I know you have to reinstall the windows applications on your fake C drive. I believe this is so that wine can properly emulate .dll's and other windows components, as well as setup registry entries.

2. That Wine guide does seem very thorough! I've seen some good HowTo's in the Howto forum:
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)
Just do an advanced search in that forum only and I'm sure you'll find plenty of info.

3. Getting games to work - this really depends on the games you want to play. If you're thinking of playing new games (released in the last year) then from personal experience I suggest you keep your windows installation around - just for games. 

Cedega isn't bad (and it's always getting better), but a lot of games only get 'fixed' to work on Cedega some weeks (or months) after release and the performance is never as good as you get in Windows, for obvious reasons. Most new games are taxing enough when running in Windows, let alone being emulated in Linux.

Crossover isn't for games, it's for desktop applications. I don't believe if emulates DirectX (which is what Cedega does). It'll play some really basic, old games, but nothing even relatively recent.

Wine will play some games, but only 2D games and it can take a lot of work and know-how. I've played Starcraft on Wine and it's not bad, but the mouse lagged which made the game difficult to play.

If you want to play older games or don't mind cranking down the graphics/resolution settings in newer games then you could give Cedega a try, but if you already have a windows installation surely it's just easier to boot into it?

---

### Post by Magnes on 2006-10-12
Some applications from Windows partition will run without reinstallation but some not.

---

### Post by trommas on 2006-10-12
I am very interested in the wine-doors project and what it promisses.

Have anyone tried it? 
Will it be a revolution in windows emulation?

---

### Post by nikoPSK on 2007-09-22
Yes you can just run your programs. That's one of the benefits of wine. (if you have a window composter running I suggest you disable it before executing any windowz apps). Wine-doors I know nothing about (I can't use it!!!:() so I can't help there.

---

