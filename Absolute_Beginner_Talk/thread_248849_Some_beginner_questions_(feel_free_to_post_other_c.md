---
title: "Some beginner questions (feel free to post other *current* threads as answers)"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-09-01
I really love Ubuntu.  Just installed it on my computer and my little brother's computer.  I have a couple issues that, if I can get solved this weekend, should let me switch ENTIRELY away from windows!! whoohoo!  

Anyways, I do a lot of searching, but more than a few times I have started executing steps that were out of date or just plain wrong (which I found out later after reading down the thread). I promise I will get smarter about this and read things more carefully.

As a result, I'm posting this to get info that is more up to date.  I apologize for the length of this post, I am very new and all this thread chasing is becoming intimidating :( 

In order of most critical to least:

------------------------------------------------------------------------

1.  Upgraded to 686 to take advantage of hyperthreading.  Now my keyboard is acting up by losing window focus and randomly not working.  Questions: do I need to change repositories after upgrading? Is everything suppose to "just work" when upgrading like this (technique: sudo apt-get install linux-686 or something similiar)


------------------------------------------------------------------------

2.  After upgrading the kernal, the computer would lag for 20 seconds when trying to do simple things like moving a window when not using XGL COMPIZ.. when using XGL/COMPIZ it works fine.  I had originally posted about this here:
 [http://ubuntuforums.org/showthread.php?t=244794]("http://ubuntuforums.org/showthread.php?t=244794")

Result - I'm fed up with XGL/Compiz.  I feel like it's all messed up on my computer.  I installed it the "old" way and I want to try again, this time using the new (and better) way based on sessions.
Questions: Is there an easy way to _completely_ uninstall XGL/Compiz and bring my system back to the way it was when I started?  I am praying this doesn't involve going back through the guide I used and reversing the changes.

What I want is to be able to have the computer running the normal way (when you do a fresh install) and be able to switch XGL/Compiz on and off as needed.


------------------------------------------------------------------------

3.  I got my little brother's desktop computer working (with wireless!!!) and occasionally  he loses connection.  Questions: Is there a way to disable the wireless card and re-enable it so it can look for the signal again?  I know how to bring it down and up, is that all I have to do?


------------------------------------------------------------------------

4.  MIDI files aren't playing at all on my Ubuntu box (maybe I need some sound font?)  So I still have to use windows for making MIDI's.  I currently use voyetra's MIDI Orchestrator Plus (a very old program).  I've looked around for something similiar but all the programs seem too complicated.  This picture is what I'm looking for:
[IMG]http://www.cdaccess.com/gifs/screen/midiorch1.gif[/IMG]
Something that I can just draw notes in.  Questions: Should I look into Wine or Cedega?  Is there a substitute?


------------------------------------------------------------------------

5.  This should be an easy one.  I am very used to windows.  I keep a neat and tidy file system.  I only install programs I need and use.  I monitor my system and try to keep track of all services and programs running at all times.  I am having difficulties understanding the linux equivilant of the windows areas (I understand it's not going to be the same, but I need a frame of reference).  

I find myself downloading things and not feeling comfortable that where I'm putting them is the "right" spot to keep everything in order.

For example, where should I put my music?  In my home folder? In my user folder?  Where are the system files, program files, my documents, etc??  


------------------------------------------------------------------------

If you made it this far, thank you very, very much!! I am on my way to completely switching!!! Please feel free to post other threads in response, just make sure they are up to date so I don't get all turned around.

---

### Post by bruce89 on 2006-09-01
> **k9brand said:**
> 
MIDI files aren't playing at all on my Ubuntu box (maybe I need some sound font?)
```
sudo aptitude install timidity
```
This will let you play them, but you have to use TiMidity++ to play MIDI files.  To get a gui version of TiMidity++, use this command:
```
timidity -ia
```

> **k9brand said:**
> 
5.  This should be an easy one.  I am very used to windows.  I keep a neat and tidy file system.  I only install programs I need and use.  I monitor my system and try to keep track of all services and programs running at all times.  I am having difficulties understanding the linux equivilant of the windows areas (I understand it's not going to be the same, but I need a frame of reference).  

I find myself downloading things and not feeling comfortable that where I'm putting them is the "right" spot to keep everything in order.

For example, where should I put my music?  In my home folder? In my user folder?  Where are the system files, program files, my documents, etc??
Everything you modify on a daily basis should be put in your home directory (~), as that is the only place you have full permissions over.  Most data files are kept in /user/share, programs in /usr/bin and libraries in /usr/lib.

---

### Post by k9brand on 2006-09-01
thanks!  that's good to know.  coming from windows, I have very little experience with permissions.  I'll check out tmidity tonight!!! :)

---

### Post by k9brand on 2006-09-01
Well, I went to run the GUI and I got this:

```
ALSA pcm 'default' set buffer size 60208, period size 3760 bytes
Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-adobe-helvetica-bold-r-normal--12-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

CONNECTION PROBLEM WITH XAW PROCESS: Success

```

---

### Post by Paul41 on 2006-09-01
> 1. Upgraded to 686 to take advantage of hyperthreading. Now my keyboard is acting up by losing window focus and randomly not working. Questions: do I need to change repositories after upgrading? Is everything suppose to "just work" when upgrading like this (technique: sudo apt-get install linux-686 or something similiar)
You might need to select a different keyboard, but I doubt that is the problem since it is only random.  In System->Preferences->Keyboard on the Layouts tab you can try a different keyboard to see if it helps any.

You don't need to change repositories after upgrading.

---

### Post by SoftTaco on 2006-09-01
In response to question 3

you might try [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

the easiest way to get it is to install automatix, which might fix your midi problem

get automatix:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix)

---

### Post by k9brand on 2006-09-02
Yeah.. I did the automatix stuff already.  I'm going to check around for people having the same problem installing tmidity.  Libraries and fonts confuse me a little, so I'll probably read up on those this weekend as well.

---

