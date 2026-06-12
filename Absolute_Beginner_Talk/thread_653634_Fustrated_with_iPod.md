---
title: "Fustrated with iPod"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by juniah on 2007-12-30
Ok.  I've been at this for a few hours now.  I've read multiple threads here and nothing is helping me out.

How do I get my iPod to see the music when I use gtkPod, amaroK, or any other program like that.

I can see my music on linux, but the iPod can't.  I have a new 8 GB iPod Nano, that I got today and I'm gonna snap.  I've heard it might have to do with firmware, I've tried funk's corner (theres a link in the forums somewhere to it) and that didn't work.  I've tried the 'great' how to and it didn't work.

All I have Gutsy and my iPod.

Somebody please help with instructions that a 2 year could follow.

It would be greatly appreciated and end much fustration.

---

### Post by juniah on 2007-12-30
Ok, I forgot to mention that earlier I did get songs on it.  I used my brother's windows box to do it (thats where I picked up my iPod today).  So apparenlty after doing some reading, my iPod should be in a FAT32.  However that doesn't make sense because the nano's don't use a hdd, they're flash.

or am I just going crazy????

---

### Post by dcj65 on 2007-12-30
I removed amarok and replaced with the new version [here ]("http://amarok.kde.org/")and now my ipod works fine. Hope this helps

---

### Post by juniah on 2007-12-30
Ok, but amarok doesn't work.  I can put music on to my iPod but still it doesn't recognize what I've just put on.

---

### Post by doorknob60 on 2007-12-30
Are you putting on ogg files or something? Because I don't think iPods can read oggs.

---

### Post by juniah on 2007-12-30
no ogg files

---

### Post by juniah on 2007-12-30
Ok something I've noticed in my version of GTKPod theres no Sync button only a 'Save Changes' button.  Anyone want to take a gander at that one?

---

### Post by slibuntu on 2007-12-30
Have you tried Rythmbox? I've been told it works well, and i second what doorknob said, make sure they're not ogg's

---

### Post by matt_risi on 2007-12-30
I don't think we have to worry about him using Ogg, all major download sites distribute in mp3. At any rate, I've been using Rhythmbox well with my iPod, except that you can't delete music off it! It adds it great, but when you delete music using Rhythmbox, it just seems to delete the entries to the iPod database, and not the actual files.

Anyone else encounter this?

---

### Post by siwilson on 2007-12-30
> **juniah said:**
> Ok, but amarok doesn't work.  I can put music on to my iPod but still it doesn't recognize what I've just put on.

Hi, try searching the other forums on here. You need to update libgpod/libgpod2 (all of the applications appear to use these libraries), for the newer iPods to work.

/Simon

---

### Post by juniah on 2007-12-31
those are upto date.  how do you use rythmbox to add songs or podcasts to your ipod?

---

### Post by juniah on 2007-12-31
Now Ubuntu won't reconize my iPod....

---

### Post by tdrusk on 2007-12-31
I recommend banshee.

it is so simple to use with the ipod

make sure you are right clicking on the ipod and ejecting it or unmounting it before you pull it out.

---

### Post by Animal Mother on 2007-12-31
[Songbird FTW]("http://www.songbirdnest.com/")

---

### Post by juniah on 2007-12-31
banshee no see iPod.

I think i just might commit suicide and not worry about this anymore.

---

### Post by juniah on 2007-12-31
songbird won't sing for me.  just crashes.

---

### Post by feistybird on 2007-12-31
first remove the gtkpod completely and reinstall it.

sudo apt-get remove --purge gtkpod
sudo apt-get install gtkpod

run gtkpod, and click "Edit" => "Edit Preferences"
In "General" tab, look for "Import" and "Ipod mount point"
Change the path to "/media/ipod"

Then go to "tools" tab

Look for "Play"
and change the "Command for Play Now" to "gmplayer %s"
and the "Command for Enqueue" to "gmplayer -e %s"

(you can use rhythmbox or whatever the audio player you like in the above command)

You will need to click "Read" button first to load the iPod's playlist , and then right click on the loaded list, and click "play now" on the context menu

If you wan to use rhythmbox, you need to install the following plugins:

sudo agt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad

---

### Post by juniah on 2007-12-31
No go feistybird....

Still wont let my iPod see the music.

---

### Post by juniah on 2007-12-31
Should I just reinstall linux and then use one of the solutions I've seen?  So this way I can start fresh again?

---

### Post by frankos44 on 2007-12-31
Me having problems here too.

One of my daughters iPod (model A1199) works absolutely fine  with Rythmbox and has done so for over a year now.

My other daughter now owns an iPod (model A1236) and this IPod refuses to work with Ubuntu.

Files can be copied on but wont play. I understand that there is a database file containing information about each mp3 and I think the problem relates to this.

I would of expected Apple to of catered for Windows, Apple and Linux users from the outset but obviously not. 

Any positive help here would be appreciated.

---

### Post by kvonb on 2007-12-31
-

---

### Post by juniah on 2007-12-31
It's a drop down menu when you go to configure it in amaroK.

Speaking of which, it says the 8Gb nano is black, but my dad got me the red one.  I don't think this should make a difference, but if it does can someone let me know?

Oh, also no progress.  Got fed up and watched Hellboy.

---

### Post by juniah on 2007-12-31
How do I correct these GTKpod errors?

Number One

> iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using SHA1 checksums. This may take a long time.

Number Two

> Transfer of 'Stop Don't Panic' failed. Error opening '/media/ipod/iPod_Control/Music/F08/gtkpod703312.mp3' for writing (Permission denied).


---

### Post by exile on 2007-12-31
Number 1 is not an error. It happens when you use gtkpod to add music and later on use itunes to access the ipod. iTunes can slightly change the file information hence changing the checksum when it does the gapless playback anaylsis. All this is saying is that gtkpod's checksums aren't what they are expecting and it has to update its definitions. Annoying yes, but it's not an error. I think you can turn this off in Edit -> Preferences -> General then uncheck "Write Extended Information". I've never tried this since it is not recommended, but that is where I would start.

Regarding the second one. I've never seen this but my hunch would be that you are using different (lesser) permissions when syncing the ipod now to what was used when creating the library previously. You might be able to chmod -R 777 the ipod's directory, I don't know if that is the best way or if that will sove the problem though. Others wiser than myself can help you better with that one.

Good luck.

---

### Post by tdrusk on 2007-12-31
Have you been unmounting it when when you disconnect it? That could be why it's not working...

---

### Post by juniah on 2007-12-31
At somepoint Ubuntu stopped loading the iPod automatically and I had to mount and unmount mannually using sudo.  So i'm not sure what happened, but at one point my system stopped responding and I had to restart my session while my ipod was mounted (that was fun!).  Not sure if that had to do anything with it.

Also on the start of my new session a get a box that says 'Could not load HAL'

Any ideas?

---

### Post by exile on 2007-12-31
There have been times when if I didn't unmount my usb disks then strange things could occur but that was easily fixed with a reboot, and in the last two releases of ubuntu I've found the USB subsystem to be very stable. Sounds like something strange is going on with your system.

---

### Post by tdrusk on 2007-12-31
> **juniah said:**
> At somepoint Ubuntu stopped loading the iPod automatically and I had to mount and unmount mannually using sudo.  So i'm not sure what happened, but at one point my system stopped responding and I had to restart my session while my ipod was mounted (that was fun!).  Not sure if that had to do anything with it.

Also on the start of my new session a get a box that says 'Could not load HAL'

Any ideas?

get a computer with itunes and reformat it.

make it so it doesn't automatically update.

then try.

I think the filesystem is corrupt on the ipod.

---

### Post by juniah on 2008-01-01
Alright, thanks.  I'll give that a go.  however it'll have to a wait a couple of days.

---

### Post by metalpancake on 2008-01-01
There is a open source firmware hack for ipods that let you use a drag and drop interface with music and will also play many new formats not supported by apple such as ogg and flac.
It's called Rockbox[http://www.rockbox.org]("http://www.rockbox.org")

It works on most ipods and some other players too.:)

Good luck and happy new year!:popcorn:

---

### Post by juniah on 2008-01-01
metalpancake - looked into that, and unfortunately only the first generation of the iPod nano is supported.  Thanks though!!

Happy New Year to you all!!!  And many thanks for patience and help!!

---

### Post by metalpancake on 2008-01-01
ok. They will probably make a version for the 2nd gen nano eventually. I run it on a ipod vidio 30gb and it runs well. It actually dual boots with the apple firmware.:)

---

### Post by juniah on 2008-01-01
Thats interesting you get it to dual boot.  I'd like to see that actually.  However I have a 3rd gen iPod, so I'll have to wait longer for those with the 2nd gen.

---

### Post by airtonix on 2008-01-11
get rid of gutsy and use fiesty instead.

gutsy is still beta not ready for general bovine consumption.

then you want to get floola ([http://www.floola.com](http://www.floola.com)) if you still want to use your appleOs on your ipod.

or rockbox. I highly recomend rockbox over using ipods appleOs & itunes.

ps: rockbox team have begun a wma decoder, a calendar and vcard reader (goodbye appleOs)

---

### Post by Amstell on 2008-01-11
Make sure that you are unmounting the ipod to prevent data loss.

---

