---
title: "Itunes disk space"
date: 2012-05-18
forum: Any Other OS
---

### Post by roelforg on 2012-05-18
My parents' XP computer has an 41GB drive.
Now diskspace is running out (i was kinda expecting this).
After some searching i determined the culprit (well, the worst one) is Itunes.
It uses 18+GB in My Music (!)
Some more searching reveals that it's used because itunes keeps a copy of every app ever installed on the phone of me,my sister, my mother and my dad.
(Note: As much as i hate apple, they DO make good phones with a lot of apps (that and the android UI just hates me, it never detects my finger)).
Now, i never hook my phone up to itunes, but my sister does and it would be a problem if it would try to erase her phone.

My question is: Can i safely delete those app-files w/o triggering itunes to erase the phones (it already wants to do that on mine, guess why i never hook it up)?

Please keep in mind that i hate itunes.
(I can build ubuntu based distro's in a snap by hand and do a lot of stuff complex on computers. But itunes just gives me a headacke when i try to do even the simplest of things w/o erasing my entire phone (and i still fail to get it done)!)

Help please!

(Stuff like this makes me glad that linux (in general) is very efficient with disk space. And i almost never have to deal with low diskspace on my (usually dated) systems.)

---

### Post by TransitMan on 2012-05-20
41GB is really small in this day and age. If it were me, I'd upgrade the drive, or install a second and move all iTunes related files there.
Otherwise, get a new larger drive and install Windows and copy over everything from the 41GB drive to the larger newer drive.

As for deleting those programs or apps from iTunes, yes it will delete them from the phones. My step-daughters friend did this and totally borked her phone.

---

### Post by VanillaMozilla on 2012-05-23
If it were your computer instead of your parents', I would direct you to RhythmBox or Banshee on Linux.

I've just been through this in the last 48 hours.  ITunes is a rude program.  It pretty much takes over your computer and gives it over to Apple.  Not only the hard drive, but the processor as well.  It took me a couple of hours to drive a wooden stake through all the extraneous iTunes processes, and then they came back.  It basically assumes that you have every Apple product they have ever made, and it tries to synchronize your data with all of them continuously.  I found 6 memory-resident processes running -- some of them fairly large, and most of them even if I had not run iTunes.  Some of them ran separate processes for each user who had logged on.  The Apple site has a list of 12 of these processes.  Use the Task Manager to look for these.

I don't have all the details here, but I can tell you in general terms.  The first thing to do is to to Add/Remove programs and uninstall everything Apple that's not directly related to the task at hand.  That will be sufficient to kill off at least some of it.  Then there's a lot of user-profile stuff on the C: drive.

I went so far as to rename some of the executables and then create empty files with the same name as the .exe or .dll file.  That was only partly successful, as some of them were recreated and some just spawned error messages.  I also went to msconfig and some other MS config utility (I don't have notes here) and turned off the extraneous services.  Both of these were pains.  Uninstalling stuff is preferable if you can find it all.

I found a couple hundred MB of profile and application information, even though I installed iTunes on another drive. You can probably get rid of all or most of that, but you have to be creative to find it.  It's under both applications (iPod?) and user profile data.  Be cautious, but also be bold and creative.

If you have Firefox, it will install a plugin.  Go to Tools > Add-Ons > Plugins and disable it.  I tried nuking it from the hard drive, but it resurrected itself, so you have to disable it from within Firefox.

Now everything works, except that it whines on startup that it doesn't have an Internet connection (I just click OK, as I don't need the store).  Also, the Help document doesn't work, so I have to go on line.  Works for me.  Both of these are possibly because I killed access to some the stuff in my firewall.

Finally, I have seen rumors that Apple has a custom installer hidden somewhere, which will install only what you want.

Good luck.  I wish I had all the details for you.

P.S.
And by the way, if you just add another hard drive and install stuff on that instead of C:, you're still partly out of luck because of all the junk it will try to put in user profiles on the old C: drive.  And transferring the system to a new drive is a good solution, although you have to do it in the Microsoft way, whatever that is (thanks, Microsoft).

Finally, and maybe most important, go through the options settings and try to put the library and the music files on another drive if you can.

---

### Post by roelforg on 2012-05-23
> **VanillaMozilla said:**
> If it were your computer instead of your parents', I would direct you to RhythmBox or Banshee on Linux.



That's not needed, if the thing was mine, i'd have put linux on the thing a long long time ago.

> **VanillaMozilla said:**
> 

I've just been through this in the last 48 hours.  ITunes is a rude program.  It pretty much takes over your computer and gives it over to Apple.  Not only the hard drive, but the processor as well.  It took me a couple of hours to drive a wooden stake through all the extraneous iTunes processes, and then they came back.  It basically assumes that you have every Apple product they have ever made, and it tries to synchronize your data with all of them continuously.  I found 6 memory-resident processes running -- some of them fairly large, and most of them even if I had not run iTunes.  Some of them ran separate processes for each user who had logged on.  The Apple site has a list of 12 of these processes.  Use the Task Manager to look for these.

I don't have all the details here, but I can tell you in general terms.  The first thing to do is to to Add/Remove programs and uninstall everything Apple that's not directly related to the task at hand.  That will be sufficient to kill off at least some of it.  Then there's a lot of user-profile stuff on the C: drive.



Already done that, itunes has 21gb of user-profile stuff stuffed in My Music (i checked it, it's in the itunes subdir).

> **VanillaMozilla said:**
> 

I went so far as to rename some of the executables and then create empty files with the same name as the .exe or .dll file.  That was only partly successful, as some of them were recreated and some just spawned error messages.  I also went to msconfig and some other MS config utility (I don't have notes here) and turned off the extraneous services.  Both of these were pains.  Uninstalling stuff is preferable if you can find it all.

I found a couple hundred MB of profile and application information, even though I installed iTunes on another drive. You can probably get rid of all or most of that, but you have to be creative to find it.  It's under both applications (iPod?) and user profile data.  Be cautious, but also be bold and creative.



I'm afraid it'll try to erase the phones again if i do that (it already tried to do that like 20 times in the last year).

> **VanillaMozilla said:**
> 

If you have Firefox, it will install a plugin.  Go to Tools > Add-Ons > Plugins and disable it.  I tried nuking it from the hard drive, but it resurrected itself, so you have to disable it from within Firefox.



I installed firefox after itunes, itunes doesn't know firefox is on the pc. ;)
There are only the flash, java, vlc and ms plugins on firefox.

> **VanillaMozilla said:**
> 

Now everything works, except that it whines on startup that it doesn't have an Internet connection (I just click OK, as I don't need the store).  Also, the Help document doesn't work, so I have to go on line.  Works for me.  Both of these are possibly because I killed access to some the stuff in my firewall.

Finally, I have seen rumors that Apple has a custom installer hidden somewhere, which will install only what you want.



If you ever find that installer, send me the file (not the link because i suspect apple'll take it down fast) and i'll own you big time.

> **VanillaMozilla said:**
> 

Good luck.  I wish I had all the details for you.

P.S.
And by the way, if you just add another hard drive and install stuff on that instead of C:, you're still partly out of luck because of all the junk it will try to put in user profiles on the old C: drive.  And transferring the system to a new drive is a good solution, although you have to do it in the Microsoft way, whatever that is (thanks, Microsoft).

Finally, and maybe most important, go through the options settings and try to put the library and the music files on another drive if you can.

I already explained that i erased all the mp3 files on the drive (saved 10gb that itunes has filled now), and that created more problems: Itunes won't sync anymore because it thinks the files are still there when they're not.

Look, this kind of stuff is exactly why itunes causes me headackes and why i hate that damn program (though i think it should be classified as a virus because if you wipe it you can't do several things as some stuff can only be done on the pc that originally activated the phone).

The HD suggestions are all fine, but they're going to get a laptop this year (i actually marked the day they're gonna get one on the calendar) and they're not gonna put any more money in the pc (it's a dell (no hw issues ever) from 2001). So the poor old thing is gonna have to last a little longer.
When they take a laptop i get the pc, i've already planned the first thing i'm going to do with it: Crack it open, remove the hd (in case there's some file they want and forgot or need itunes again (i hope not)), put in a new, fresh one, throw a copy of ubuntu on the thing and make it last a long time (cause it's perfectly capable of running ubuntu with unity (dedicated nvidia card)) but without the resource intensive strain of windows.

---

### Post by VanillaMozilla on 2012-05-23
> **roelforg said:**
> Already done that, itunes has 21gb of user-profile stuff stuffed in My Music (i checked it, it's in the itunes subdir).
There's more.  It's in user profiles.  (And not .mp3 files.)

> **roelforg said:**
> I already explained that i erased all the mp3 files on the drive (saved 10gb that itunes has filled now), and that created more problems: Itunes won't sync anymore because it thinks the files are still there when they're not.
But I hope you still have the files, because those are the music.  The basic iTunes index in two databases called something.itl and something.xml.  You can easily Google this.  If you move the music, you could delete (or rename) these files and ask iTunes to import the tunes again.  It will recreate the indexes.  iTunes may have a proper way to do it rather than deleting the index files.

Gee, a 16 GB USB flash drive would make a great place for temporary storage of the music files, and you could point iTunes toward it.

Sorry I couldn't be more specific, but I don't have my notes here.  Good luck.

---

### Post by VanillaMozilla on 2012-05-24
Ah, here it is:
[http://support.apple.com/kb/HT3960](http://support.apple.com/kb/HT3960)
I think if you uninstall the right stuff and make sure none of them is in memory (and you're not running iTunes at the moment), you can't erase your phone.  It can't erase the phone if it can't communicate, right?

---

### Post by VanillaMozilla on 2012-05-27
[http://www.zdnet.com/blog/bott/the-unofficial-guide-to-installing-itunes-10-without-bloatware/2390](http://www.zdnet.com/blog/bott/the-unofficial-guide-to-installing-itunes-10-without-bloatware/2390)
[http://www.howtogeek.com/howto/28727/how-to-install-itunes-without-extra-bloat/](http://www.howtogeek.com/howto/28727/how-to-install-itunes-without-extra-bloat/)

You owe me your first-born child, even if you don't check back here again.


EDIT:  Cancel that.  This stuff doesn't work.  iTunes.msi installs all that stuff and runs it by default.  You have to start all over with the wooden stake.  Try services.msc for a start.  If that doesn't kill it, get rid of the .exe files and replace them with dummy files with zero length.  Best solution:  do a System Restore if you can, to just before that stuff was installed.

---

