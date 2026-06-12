---
title: "How can I import XP registry to WINE?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by lexl1604 on 2008-03-30
Hi folks,

first of all THANK YOU ALL a lot for this superb OS... Ubuntu's the best!!!!!

Now what I'm gonna ask seems perverted, but is there a possibility to copy the entire XP registry and the whole "C:\Windoze" directory into WINE? Would it increase WINE performance?

I ask because there are several games I'd like to run on UBUNTU.

[got 7.10]

Games:

[www.cabalonline.com](www.cabalonline.com) (using gameguard)
Battlefield 1942
Peggle Deluxe (there is a problem with the game activation key)

and many more...

I know WineHQ and appDB etc. but there was no help for me...

My concrete question is the following: Will WINE be able to Run 90% (almost all) of the windows programs (Which are not using directX) when it contains all the files that are in the C:\Windoze directory?

best regards
alex

(don't be angry with my english... I'm just a student from austria)

PS: by the way... is it possible then to install the LEXMARK P6350 printer on wine?
If not, is it possible to install the printer on a virtual XP machine? (linux (cups) doesn't have the drivers, but recognizes the printer) (I have the XP drivers)

---

### Post by forestpixie on 2008-03-30
I don't think it works like that - if you've checked the wine appdb and it gives bad results for the games you're trying to use - you need to play them in windows.

As far as the english - it's a whole lot better than my Austrian, just don't post in Austrian :)

---

### Post by Oldsoldier2003 on 2008-03-30
> **lexl1604 said:**
> Hi folks,

first of all THANK YOU ALL a lot for this superb OS... Ubuntu's the best!!!!!

Now what I'm gonna ask seems perverted, but is there a possibility to copy the entire XP registry and the whole "C:\Windoze" directory into WINE? Would it increase WINE performance?

I ask because there are several games I'd like to run on UBUNTU.

[got 7.10]

Games:

[www.cabalonline.com](www.cabalonline.com) (using gameguard)
Battlefield 1942
Peggle Deluxe (there is a problem with the game activation key)

and many more...

I know WineHQ and appDB etc. but there was no help for me...

My concrete question is the following: Will WINE be able to Run 90% (almost all) of the windows programs (Which are not using directX) when it contains all the files that are in the C:\Windoze directory?

best regards
alex

(don't be angry with my english... I'm just a student from austria)
no it wouldn't be helpful. in fact it would probably break your working installation of wine. some of the "windows" files in wine are not the native windows .dlls and installing the windows version would make wine not work correctly...

---

### Post by lswest on 2008-03-30
You can, however, try [crossover games]("http://www.codeweavers.com/products/cxgames/") (they have a trial) so you can try those games there first, and if it works, purchase the software (i think it's like 34€, which isn't bad), otherwise...you're probably out of luck.  And no, copying the whole registry and folder is not a good idea, as the registry was modded so that it works in linux, and the dll files also.  You can, however, copy certain parts of it over (such as the core fonts for microsoft, etc.)

---

### Post by SpongeBob SquarePants on 2008-03-30
Hi Alex,

If it's any help, at least two of those games seem to run in Linux using Cedega. It's a commercial software, but it's cheap. See the Cedega games database here......

[http://games.cedega.com/gamesdb/](http://games.cedega.com/gamesdb/)

andthe  Battlefield 1942, working in Linux screen shot here......

[http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2857](http://games.cedega.com/gamesdb/games/view.mhtml?game_id=2857)

---

