---
title: "Sansa M250"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by jlb2 on 2006-09-21
Greetings group,
                  I am new(ish) to the open source world and am looking for some help with the Sandisk Sansa M250 .  I currently run Kubuntu Dapper Drake (KDE 3.5.2) on an older machine (AMD XP1800) . I am using Amarok 1.4.2.   I would like to know how to set the Sansa M250 up correctly/efficiently.  Basically, I would like to boot up the player and be able to choose between categories i.e. Podcasts/Music/ Audiobooks or something that resembles perhaps a playlist.  I just got this thing (M250) today, mind you, but have been having a devil or a time trying to get things organized.  I also have another problem.  I initially just did a plug n' play with the unit and it was recognized by my system.  The unit itself was on Settings>USB>Automatic.  I transfered a "Netlibrary" .wma file to it just to see if it would work.  I figured it wouldn't....but tried so anyway.  It didn't, as expected, due to their proprietary encrypting (if anyone knows anything about decrypting "Netlibrary" .wma files, let me know...I would sure like to be able to listen to audiobooks I check out from my public library via linux/Sansa M250).  In the Konqueror browser window...I deleted the file from the AUDIBLE folder.  When in Konqueror under media:/sdb1 I have the following folders/files:  AUDIBLE, CONFIG, RECORD and a file called SYS_CONF.DNC.  I then loaded another .mp3 that was not DRM restricted.  It worked.  Ok sweet, I said.  But the Sansa M250 still listed the track I had deleted, although it wouldn't play.  How can I get rid of these "ghost files?"  Are they taking up flash memory?  I then went through Amarok, which is great on the desktop, but seems a little finicky when trying to transfer song to a flash memory MP3 player.  Sure, I transfered some more songs but, those damn "ghost files" still appear on the player (i.e. I physically transfer 10 files, deleted 2 and the Sansa M250 still says I have 10 files on there) when I delete them via Konqueror (i.e. normally).  Maybe this is just a poorly executed player...perhaps I am too inexperienced with linux/Amarok...not sure.  Any help would be greatly apprecited.  Here are links that I have found/ read that I believed would have helped me.  They really didn't but, perhaps I don't understand the material. 

[http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Audio_Books](http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Audio_Books)

[http://www.linuxquestions.org/questions/showthread.php?p=2346005](http://www.linuxquestions.org/questions/showthread.php?p=2346005)

[http://www.ubuntuforums.org/archive/index.php/t-235700.html](http://www.ubuntuforums.org/archive/index.php/t-235700.html)

I just want to be able to drag/drop files and have a little organization with the Sansa M250.  Also get rid of the files I know I deleted.  Any help greatly apprecited. 

Sincerely,
Jeff

---

### Post by slmingol on 2006-09-28
Did you try emptying the trash with konqueror after you deleted these files from your sansa? I find I have to do this. Apparently the files are still on the sansa in a "trash" basket and aren't really deleted until you empty them. I do this with nautilus, which is gnomes default file browser/manager program.

---

### Post by haiku99 on 2006-09-29
I've been fooling around w/ an M240 and have learned a little after some struggle ](*,) ...deleted files  do indeed go to a trash folder which is hidden (using gnome at least)....from the view menu you can make it visible and then delete the contents, but not the trash folder itself. Also, whenever you add or delete content before disconnecting the player from the computer you need to eject  it by right clicking on it on the desktop and selecting eject, if you fail to do this the changes will not take and/or the files will not play properly.  Finally, if you are using it as a mass storage device, select MSC, NOT auto, auto will put the player in MTP mode which few linux programs will handle....FWIW Amarok 1.4.1 or greater supposedly will, but after waaay to much hassle trying to make it work I reset the player to MSC and now use drag and drop....from what I've read Edgy Eft will have better MTP support. There is some good info on m200 series players at
[http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200](http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200)

---

