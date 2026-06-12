---
title: "Gnash on ppc (ps3) 0.8.6 - no go?"
date: 2009-12-20
forum: Apple Hardware Users
---

### Post by alpinerod on 2009-12-20
Can anyone please let me know if you got flash working on PS3 ubuntu (9.10, karmic koala) through gnash or via any other means? I specifically mean mozilla playing youtube and like sites.

I've installed the browser plugin, have gnash 0.8.6 -- even compiled my own gnash from sources just in case -- still not getting any results. Only interested in 9.10 solution specifically for PS3 h/w.

Thanks

---

### Post by rjcalifornia on 2009-12-21
yeah, no go...

---

### Post by oswaldkelso on 2009-12-21
This is on Debian. But it's a similar sort of set up on Ubuntu 

Gnash and swdec are to resource heavy and unfortunatly not quite there on my PPC machines. Here a rehash of info on viewing youtube on PPC, that my self and others posted on the ubuntu forum. It will give you a good youtube experiance if nothing else.

How to watch youtube clips without flash-gnash etc on PPC
I just notice a lot of new PPC users struggling so thought I'd chuck this in.

I only really need flash for youtube and as it doesn't exist and gnash can be a bit cpu intensive on my old PPC hardware I use clive in terminator. Then I split the screen and run mplayer -ontop name-of-clip, works a treat. (you can leave out the -ontop bit if your feeling lazy)
No need to wait for the download, and you can be adding other clips at the same time.

Depending on your connection speed you can vary how much video to cache. On my poor 1mb connection I give 5% on small clips and 10-15% on larger ones.

In reality by the time you've split the terminator screen and typed mpla (TAB to auto complete) and read and started typing the youtube clip name (clive changes all that gobby gook to a real name) your buffer has loaded.

In debian I use mplayer from debian multimedia repo,(non gui).

as root

Code: Select all
    apt-get install clive mplayer 



[http://www.youtube.com/watch?v=y-KeLxxHkEY](http://www.youtube.com/watch?v=y-KeLxxHkEY)

Or

For a nice gui try Abby it needs clive or cclive to be installed [http://code.google.com/p/abby/](http://code.google.com/p/abby/) I use clive or cclive if I just want to play a single youtube link and abby if I want to select from all the links on the page and down load them all for later in a few clicks.

Code: Select all
    Apt-get install abby cclive 



Or
Minitube a sort of youtube TV [http://freshmeat.net/projects/minitube](http://freshmeat.net/projects/minitube) [http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)
I did eventually manage to compile it. viewtopic.php?f=10&t=46571 But it failed to play on my machine. You may have better luck and it is as of today being activly developed.

Or
You could just use the customvid addon for firefox/iceweasel [https://addons.mozilla.org/en-US/firefox/addon/12027](https://addons.mozilla.org/en-US/firefox/addon/12027) (License: Mozilla Public License 1.1 (MPL 1.1)

[http://www.youtube.com/watch?v=aahiPQwb5hM](http://www.youtube.com/watch?v=aahiPQwb5hM)

Or

If you run epiphany or iceweasel use a greasemonkey script.
First you need to install greasemonkey from the repos

Code: Select all
    apt-get install epiphany-extensions 


or

Code: Select all
    apt-get install iceweasel-greasemonkey 


And then, install this script: [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

If you run epiphany the script goes in ./gnome2/epiphany/extentions/data/greasemonkey/50771.user.js
I found it worked well on my better machines but on my low end 333mhz imac clive and mplayer was a better option and much more flexible in that it didn't restrict browser choice, and was faster and seems to use less resources.

---

### Post by llamabr on 2009-12-21
I'll also add my vote for debian, not ubuntu, on the ibook.  

Also, gnash is the crap.  Here's a thread that discusses how to build a script to do what you want:


[http://ubuntuforums.org/showthread.php?t=951546&page=2](http://ubuntuforums.org/showthread.php?t=951546&page=2)

---

### Post by alpinerod on 2009-12-22
> **oswaldkelso said:**
> This is on Debian. But it's a similar sort of set up on Ubuntu 

Gnash and swdec are to resource heavy and unfortunatly not quite there on my PPC machines. Here a rehash of info on viewing youtube on PPC, that my self and others posted on the ubuntu forum. It will give you a good youtube experiance if nothing else.

How to watch youtube clips without flash-gnash etc on PPC
I just notice a lot of new PPC users struggling so thought I'd chuck this in.

I only really need flash for youtube and as it doesn't exist and gnash can be a bit cpu intensive on my old PPC hardware I use clive in terminator. Then I split the screen and run mplayer -ontop name-of-clip, works a treat. (you can leave out the -ontop bit if your feeling lazy)
No need to wait for the download, and you can be adding other clips at the same time.

Depending on your connection speed you can vary how much video to cache. On my poor 1mb connection I give 5% on small clips and 10-15% on larger ones.

In reality by the time you've split the terminator screen and typed mpla (TAB to auto complete) and read and started typing the youtube clip name (clive changes all that gobby gook to a real name) your buffer has loaded.

In debian I use mplayer from debian multimedia repo,(non gui).

as root

Code: Select all
    apt-get install clive mplayer 



[http://www.youtube.com/watch?v=y-KeLxxHkEY](http://www.youtube.com/watch?v=y-KeLxxHkEY)

Or

For a nice gui try Abby it needs clive or cclive to be installed [http://code.google.com/p/abby/](http://code.google.com/p/abby/) I use clive or cclive if I just want to play a single youtube link and abby if I want to select from all the links on the page and down load them all for later in a few clicks.

Code: Select all
    Apt-get install abby cclive 



Or
Minitube a sort of youtube TV [http://freshmeat.net/projects/minitube](http://freshmeat.net/projects/minitube) [http://flavio.tordini.org/minitube](http://flavio.tordini.org/minitube)
I did eventually manage to compile it. viewtopic.php?f=10&t=46571 But it failed to play on my machine. You may have better luck and it is as of today being activly developed.

Or
You could just use the customvid addon for firefox/iceweasel [https://addons.mozilla.org/en-US/firefox/addon/12027](https://addons.mozilla.org/en-US/firefox/addon/12027) (License: Mozilla Public License 1.1 (MPL 1.1)

[http://www.youtube.com/watch?v=aahiPQwb5hM](http://www.youtube.com/watch?v=aahiPQwb5hM)

Or

If you run epiphany or iceweasel use a greasemonkey script.
First you need to install greasemonkey from the repos

Code: Select all
    apt-get install epiphany-extensions 


or

Code: Select all
    apt-get install iceweasel-greasemonkey 


And then, install this script: [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

If you run epiphany the script goes in ./gnome2/epiphany/extentions/data/greasemonkey/50771.user.js
I found it worked well on my better machines but on my low end 333mhz imac clive and mplayer was a better option and much more flexible in that it didn't restrict browser choice, and was faster and seems to use less resources.

Wow, thanks for the extensive reply! I did go the "easy" way and got youtube working through greasemonkey, that plays vids quite decently, actually.

---

