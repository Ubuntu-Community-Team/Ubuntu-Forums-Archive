---
title: "gtk based pacman frontend?"
date: 2008-02-06
forum: Arch and derivatives
---

### Post by woedend on 2008-02-06
Anyone here know of a good gtk frontend for pacman?  PAcman is easy enough to use, but I find the search feature, seeing whats installed, and installing things like all of the gstreamer0.10- codecs much faster with a frontend.... gtk pacman is coming out with a new version I think, but it was unusable as of a couple weeks ago.  Jacman worked ok too, but doesnt seem to at all anymore...that and i find java apps clunky.  Don't really want to use KDE apps.
speaking of which also, is there ANY gnome based cd recording software that will burn audio cd's truly on the fly like K3b does.  Brasero claims to but doesn't(unless i'm missing a setting), and I dont think gnomebaker ever has..
then again i may just have to go to the kde darkside when kde4 shapes up.

---

### Post by Rumor on 2008-02-06
I know you can burn CD's in Banshee, the music playing program. I don't know if it does on the fly writing as I have never tried.

---

### Post by finferflu on 2008-02-07
I know I'm not answering your question, but Yaourt is a good wrapper for Pacman, which provides colorised output and also an interactive menu for selecting the packages you want to install. 

I have never tried nor looked for any GUI fronted.

---

### Post by fwojciec on 2008-02-07
> **finferflu said:**
> I know I'm not answering your question, but Yaourt is a good wrapper for Pacman, which provides colorised output and also an interactive menu for selecting the packages you want to install. 

I have never tried nor looked for any GUI fronted.

ditto.

And while we're at recommending CLI rather than GTK based apps -- bashburn is a very full featured frontend to linux CLI burning tools and it works very well for both data and audio burning.  It does require some basic CLI skills (you have to know/learn how to link files to the burn directory, etc.) but it gives you instructions and examples for everything and once you know your way around it's very convenient.

---

### Post by kpkeerthi on 2008-02-08
You may also want to try [tupac]("http://bbs.archlinux.org/viewtopic.php?id=38560") (Turbo Pacman). It does speed things (esp. search).

---

### Post by finferflu on 2008-02-08
> **kpkeerthi said:**
> You may also want to try [tupac]("http://bbs.archlinux.org/viewtopic.php?id=38560") (Turbo Pacman). It does speed things (esp. search).
Yeah! I only mentioned Yaourt because it's the wrapper on which Tupac is based, but I actually use Tupac.

---

### Post by bwtranch on 2008-02-11
> **woedend said:**
> Anyone here know of a good gtk frontend for pacman?  PAcman is easy enough to use, but I find the search feature, seeing whats installed, and installing things like all of the gstreamer0.10- codecs much faster with a frontend.... gtk pacman is coming out with a new version I think, but it was unusable as of a couple weeks ago.  Jacman worked ok too, but doesnt seem to at all anymore...that and i find java apps clunky.  Don't really want to use KDE apps.
speaking of which also, is there ANY gnome based cd recording software that will burn audio cd's truly on the fly like K3b does.  Brasero claims to but doesn't(unless i'm missing a setting), and I dont think gnomebaker ever has..
then again i may just have to go to the kde darkside when kde4 shapes up.
You may find this interesting. I haven't tried it yet. [http://bbs.archlinux.org/viewtopic.php?pid=322903#p322903](http://bbs.archlinux.org/viewtopic.php?pid=322903#p322903)
Forgot to tell you about the K3b, that one has been "split" and you can get it from pacman. I wanted KStars too so I got the kdemod package [http://kdemod.ath.cx/](http://kdemod.ath.cx/) . You can get basic or the full boat. Make sure you follow the directions. People that haven't have had problems. I have tried this one and it works just like in Ubuntu. I really like it and that was the first thing I needed back when I "switched" to Arch. (and, yeah, I think I have switched).

---

### Post by sargate on 2009-02-07
gtkpacman is on yaourt

or shaman for kde

---

### Post by doorknob60 on 2009-02-07
Shaman's good, and I'm not sure if it has extra KDE deps (might be plain Qt). I still prefer yaourt though, by far my favorite.

---

### Post by dannytatom on 2009-02-07
Pretty sure Shaman is has only QT dependencies, and not a lot either.

---

### Post by handy on 2009-02-07
Here are details on Shaman:

*_[http://sourceforge.net/projects/shaman-arch/](http://sourceforge.net/projects/shaman-arch/)_*

& gtkpacman:

*_[http://gtkpacman.berlios.de/](http://gtkpacman.berlios.de/)_*

---

### Post by Rokurosv on 2009-02-07
Shaman is very nice if you're using KDE, I totally recommend it.
And for the CLI, I use powerpill to speed things up :D

---

### Post by handy on 2009-02-07
> **Rokurosv said:**
> Shaman is very nice if you're using KDE, I totally recommend it.
And for the CLI, I use powerpill to speed things up :D

I just checked out the [*_powerpill_*]("http://xyne.archlinux.ca/info/powerpill") site & learned that if you are getting maximum download speed when upgrading/installing packages, with pacman that powerpill (naturally) can't improve on the situation.

As my downloads very rarely aren't at max' speed, powerpill would be a waste of time for me.

I'm sure powerpill would help many people that aren't maxing out their bandwidth when using pacman though.

---

### Post by dannytatom on 2009-02-07
Handy, I couldn't find much info on gtkpacman's site but whats the difference between it and Shaman (other than one being gtk and the other qt)?

---

### Post by handy on 2009-02-07
> **dannytatom said:**
> Handy, I couldn't find much info on gtkpacman's site but whats the difference between it and Shaman (other than one being gtk and the other qt)?

I don't know, I've never used either as I'm not interested in using a GUI for the job.

I find making aliases in .bashrc is about the only simplification I need to do for the process.

---

### Post by smartboyathome on 2009-02-07
> **dannytatom said:**
> Handy, I couldn't find much info on gtkpacman's site but whats the difference between it and Shaman (other than one being gtk and the other qt)?

The main difference between the two is that gtkpacman is simpler (ie, not as many features). I found it very nice if you were trying to stick with GTK, but since I use aliases now for Pacman I don't need it.

---

### Post by Rokurosv on 2009-02-07
> **handy said:**
> I just checked out the [*_powerpill_*]("http://xyne.archlinux.ca/info/powerpill") site & learned that if you are getting maximum download speed when upgrading/installing packages, with pacman that powerpill (naturally) can't improve on the situation.

As my downloads very rarely aren't at max' speed, powerpill would be a waste of time for me.

I'm sure powerpill would help many people that aren't maxing out their bandwidth when using pacman though.

Yep powerpill is such a nice tool, I usually don't download at full speed, so I use powerpill when I'm downloading large packages or updates.

---

### Post by dannytatom on 2009-02-07
> **handy said:**
> I don't know, I've never used either as I'm not interested in using a GUI for the job.

I find making aliases in .bashrc is about the only simplification I need to do for the process.

As do I, but it's easier for me to see a list of installed applications and descriptions of 'em in Shaman than it is in the terminal.  But for installing, removing, searching, etc, I use yaourt.

---

### Post by handy on 2009-02-07
> **dannytatom said:**
> As do I, but it's easier for me to see a list of installed applications and descriptions of 'em in Shaman than it is in the terminal.  But for installing, removing, searching, etc, I use yaourt.

Over time, I have been manually going through a lot of the directories on my Arch install, & deleting unnecessary files by hand.

I don't do it out of compulsion, it is more a way to gradually keep growing my familiarity with the Arch system.  My memory isn't all that crash hot, so looking around in there from time to time helps keep the familiarity. :-)

With a history of starting with Gnome, then going to Openbox, then Xfce, now back to Openbox with parts of Xfce, & my having looked at & deleted various WM's & KDEmod, there seems to be a some stuff that just gets left behind.  

Also, I have gone through & got rid of any .pacsave .pacnew remnants as well.

I'm sure that there is still a pile of stuff that doesn't need to be on my machine that has been left after my removing a package the wrong way (before I knew better) or has found another way to exist, most likely due to my ignorance at the time I was doing whatever it was I was doing.

Because Arch is a rolling release, stuff can get to stay around for a long time, if during that time you are learning how to use Arch, you can create a pile of litter that stays until Arch or the drive gets replaced...  

Trying to be litter free, is in keeping with the Arch way I think. :-)

---

### Post by dannytatom on 2009-02-07
Hah, exactly what I'm saying.  After I uninstall anything, I make sure to locate name and delete everything I can find of it.  It's just much easier for me to open up shaman, jot down stuff I don't need/want, then close it and start cleanin' up.  

I am enjoying Arch a ton though, and have fallen in *looove* with pacman.

---

### Post by handy on 2009-02-08
Pacman is capable of a large variety of ways to handle Arch packages; I am approaching the stage where I will look into learning how to use pacman in a more sophisticated fashion than I do now.

You do need to treat pacman commands with a great deal of respect.

---

### Post by dannytatom on 2009-02-08
Fill me in when ya do, 'cause as of now I use it in a pretty basic way.  Set aliases for the commands in the wiki and a few for yaourt and that's about it. :p

---

### Post by handy on 2009-02-08
> **dannytatom said:**
> Fill me in when ya do, 'cause as of now I use it in a pretty basic way.  Set aliases for the commands in the wiki and a few for yaourt and that's about it. :p

I'll start a thread on the topic & see what tips/tricks & reference resources it will bring out.

---

