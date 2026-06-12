---
title: "Play online video on BBC new website"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Kalibur on 2007-01-18
I use Edgy 32bit and Firefox but I have never been able to play the news on the BBC website.  Anyone one please help.](*,) 
Here is the url [http://news.bbc.co.uk/player/nol/newsid_3690000/newsid_3694000/3694028.stm](http://news.bbc.co.uk/player/nol/newsid_3690000/newsid_3694000/3694028.stm)

---

### Post by r4ik on 2007-01-18
Mplayer play's nice here try to install using this guide,

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

Good luck.

---

### Post by luvinit on 2007-01-18
Some people have problems with steaming media player not working when installed via synaptic. I had to use this:

[http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv](http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv)

---

### Post by SunnyRabbiera on 2007-01-18
I suggest you get realplayer.
you can get it with synaptic, but its under the ubuntu commerical repo's, to add it just open up "settings" then click on "repositories"
here go to the "third party' tab
then here press the add button.
here is how you can add this repo:
first line:
[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/)
second line:
edgy-commercial
third line:
main
ignore the last one and press "ok"
you should have it in your list now, just put a checkbox next to it and then refresh the list by pressing "reload"
then serach for realplayer, then when realplayer comes up just right click and select "mark for installation"
(them name is realplay in the repo's)
go to apply
press "ok"
let it install...
after it installs close synaptic
restart firefox...
and bingo you are done!
you might want to restart your puter though as sometimes this doesnt fully work.

---

### Post by GandG on 2007-01-18
Did you try the Totem plugin ? It seems to  pick up the BBC's Wmv files OK,  e.g., 

[http://jan18b.imghost.us/9VXE.png](http://jan18b.imghost.us/9VXE.png)


(file: mms://rmgeo.bbc.net.uk/news/media_acl/mps/fix/news/video/74000/bb/74483_16x9_bb.wmv)

Firefox 2.0.0.1

---

### Post by Kalibur on 2007-02-09
Thanx Guys I have tried everything and I have come to the conclusion that page only works in ms windows environment and linux is not supported, so much for whats suppose to be platform indipendent, I think web page designers should test there sites on all platforms.  Thanks for the help guys.  Keep spreading the ubuntu spirit

---

### Post by arochester on 2007-02-09
An oldie but a goodie. The BBC has an advice page "Advice for Unix/Linux users" at [http://www.bbc.co.uk/radio/audiohelp_nix.shtml](http://www.bbc.co.uk/radio/audiohelp_nix.shtml) . Yes it says it's Audio, but it's about using Realplayer10 and works for Video as well.

The trick is to make sure that the two files nphelix.so and nphelix.xpt are in the browser's plugins directory and to restart the computer.

Yes I can watch the BBC...

---

### Post by Maestro23 on 2007-02-09
Just went to that site and the vid played fine for me.  The mplayer-plugin in firefox picked it right up with no problems.  Running Edgy 6.10(32-bit) as well.

---

