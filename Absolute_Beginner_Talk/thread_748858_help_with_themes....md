---
title: "help with themes..."
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by mstrchfmjolnirty on 2008-04-07
Hey I just installed Ubuntu Gutsy I believe, on my laptop about an hour ago and I used to have it but traded it for Vista when I ran into massive trouble attempting to connect to a projector...so now I'm back and I've been looking at a lot of themes, I'm very interested in the Mac OS X look and am trying to run "Mac4Lin" as seen here: 
[http://www.youtube.com/watch?v=Bm9vJ0e3tXs](http://www.youtube.com/watch?v=Bm9vJ0e3tXs)
I followed a tutorial earlier tonight that failed on every level possible to fail on, so I gave up and played some Counter Strike for a while and now I'm back...I'm attempting this tutorial:
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)
and am stuck on the very first step...it says to "Goto System > Preferences > Appearance. Click Install. Browse and choose the Mac4Lin GTK Metacity Theme .tar.gz file (wherever it is extracted)"
but when I do that I have 4 different installation folders under that theme and I install all of them and end up with a theme looking exactly like the standard "human" theme and nothing like their's but called "custom"...any help here would be very appreciated...I also prefer installing through terminal over the GUI if at all possible...

---

### Post by brownknight on 2008-04-07
Whenever I have a theme that I want to use from gnome-look.org, I just open the appearance window, go to themes tab and drag the whole .tar.gz file over. It should say, theme installed, do you want to apply, and that's it! Have you tried doing this? Works all the time for me.

---

### Post by Saya on 2008-04-07
After installing the themes you need to go to Appearance Preferences - Theme - Customize... and pick the Mac4Lin stuff in the Controls and Window Border tabs.

---

### Post by mstrchfmjolnirty on 2008-04-07
Alright...got the first step down lol...thank you all but now it says to go to system preferences and emerald theme manager...which i do not have so now i feel like a total noob but how do i go about getting this?

---

### Post by Helios1276 on 2008-04-07
you should find it in the synaptic packet manager if i remember correctly?

---

### Post by Saya on 2008-04-07
> **mstrchfmjolnirty said:**
> how do i go about getting this?
Open a terminal and issue
```
 sudo apt-get install emerald
```

---

### Post by twist2b on 2008-04-07
no offence but mac4lins theme guide is super simple. you have to go to optimize to edit which theme you are going to use. 

Emerald stinks in my opinion use nautilus.

---

### Post by mstrchfmjolnirty on 2008-04-07
well ive got it all good except for icons which werent in my extraction so ill have to work on that...

---

### Post by mstrchfmjolnirty on 2008-04-08
Alright, so I have everything looking great...correct icons, right theme and all that, but im a little stuck on the dock I got Avant installed so that I click Applications>Accessories>Avant Window Navigator....but when I do this nothing happens, so I tried the System>Preferences>Avant Preferences...and again nothing happened, I followed all the directions so I'm not too sure whats up here

---

### Post by mstrchfmjolnirty on 2008-04-08
I also followed a different guide for this step of installing Avant it is here:

[http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html)

and where it says to do the applets i run into problems it says to enter this:

bzr co [http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk) awn-extras

but i get an error saying that bazaar is already fully updated... then it says to enter this:

cd awn-extras/awn-applets/awn-extras-applets/

but i get an error saying there is no such directory...

---

### Post by mstrchfmjolnirty on 2008-04-08
Alright I'm beggining to think I may just be incompetent with this....Ive tried yet another guide here:

[http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn](http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn)

and Ive got it all in the menus and everything but when i click it it still wont come up...im really lost

---

### Post by moonbeam on 2008-04-08
> **mstrchfmjolnirty said:**
> Alright I'm beggining to think I may just be incompetent with this....Ive tried yet another guide here:

[http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn](http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn)

and Ive got it all in the menus and everything but when i click it it still wont come up...im really lost

As an awn/awn-extras dev I would like to make a couple comments:

We strongly recommend going with a binary package from either the official Hardy repositories (They do NOT include applets) or (if you want applets) then either [ Reacocard's thread ]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator") or [the awn-testing PPA]("https://launchpad.net/~awn-testing/+archive").  Please note, in any case, remove any existing awn install before installing from a new repo.

For beginners I would strongly suggest Reacocard's repository as his support thread provides an excellent Ubuntu specific environment.

btw, what you are describing is normally due to the lack of running compositor.

---

