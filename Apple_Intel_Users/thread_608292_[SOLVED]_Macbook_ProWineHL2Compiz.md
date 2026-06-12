---
title: "[SOLVED] Macbook Pro/Wine/HL2/Compiz"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by CodeSamurai on 2007-11-09
Hello All!  Here's my story:

I'm on my Macbook Pro Rev. 3 (Santa Rosa)  15.4" 2.4Ghz model.  I have been using Ubuntu on and off for about 4 years now, but I had my last bout with Windows a couple days ago.  Now I'm running a dual boot of OSX and Gutsy.  This is an awesome setup!  I have everything working well, but my main accomplishment (and actual question) stems from this.

I got wine working and also Half-Life 2, Peggle Extreme, Garry's Mod, CCS, Portal, and TF2. A problem has arisen however.  It seems that the games become unplayable when compiz is running.  I had to go back to metacity in order to run any of the games.  I have searched around and found only half answers, but my question is this:

Is there a way to write a script that will make compiz turn off when I start a game, STAY OFF (I emphasize this because most answers I've found fail to address this) and then turn back on when the game is closed.  I'm new to this type of thing, so if you do have the answer, I'd enjoy a fairly thorough walkthrough.  Thanks!

Trent out

---

### Post by cyberdork33 on 2007-11-10
> **CodeSamurai said:**
> Hello All!  Here's my story:

I'm on my Macbook Pro Rev. 3 (Santa Rosa)  15.4" 2.4Ghz model.  I have been using Ubuntu on and off for about 4 years now, but I had my last bout with Windows a couple days ago.  Now I'm running a dual boot of OSX and Gutsy.  This is an awesome setup!  I have everything working well, but my main accomplishment (and actual question) stems from this.

I got wine working and also Half-Life 2, Peggle Extreme, Garry's Mod, CCS, Portal, and TF2. A problem has arisen however.  It seems that the games become unplayable when compiz is running.  I had to go back to metacity in order to run any of the games.  I have searched around and found only half answers, but my question is this:

Is there a way to write a script that will make compiz turn off when I start a game, STAY OFF (I emphasize this because most answers I've found fail to address this) and then turn back on when the game is closed.  I'm new to this type of thing, so if you do have the answer, I'd enjoy a fairly thorough walkthrough.  Thanks!

Trent out
Not a script (well it is, really, but not what you are asking for), but an easier way to access Compiz functions:
[http://ubuntuforums.org/showpost.php?p=3378285&postcount=12](http://ubuntuforums.org/showpost.php?p=3378285&postcount=12)

after you install fusion-icon, just add it to your session, and it manages the launching of compiz / emerald (so you can remove any compiz --replace, etc lines from your session). You can easily switch to metacity with a couple of clicks.

---

### Post by CodeSamurai on 2007-11-11
Awesome.  Thanks.  That did help a lot, but in the end, I decided to simply put two scripts on my desktop.  I realized that I'd have to have them there anyway because I use AWN (which uses compiz) so in order to turn compiz back on, I would have to have a permanent launcher.  Thanks for the help.  Consider this solved. 

Trent out

---

### Post by cyberdork33 on 2007-11-11
> **CodeSamurai said:**
> Awesome.  Thanks.  That did help a lot, but in the end, I decided to simply put two scripts on my desktop.  I realized that I'd have to have them there anyway because I use AWN (which uses compiz) so in order to turn compiz back on, I would have to have a permanent launcher.  Thanks for the help.  Consider this solved. 

Trent out
Mark as solved from the thread Tools Menu at the top.

---

