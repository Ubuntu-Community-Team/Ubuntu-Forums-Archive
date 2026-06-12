---
title: "gtkpod / ipod synching help ?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by fedira on 2007-10-08
Hi,

Okay, I've looked through past postings and I can't seem to find the solution to my problem.

I plugged in my ipod, and it mounted on the desktop without a problem. 

Here's my situation:

-- I have ~1100 songs on my ipod, and ~800 songs on my local machine, *most* of which are duplicates of those on my ipod. 
-- I want to 'sync' them so that no songs are deleted, but that all the songs on my local machine are on my ipod, and all the songs on my ipod are on my local machine. 
-- I don't want there to be duplicates, and I (ideally) don't want to delete my music collection in the process. 

In Banshee, when I hover over the "Synchronize iPod" button, it says "Synchronize music library to device." That's not what I want to do -- I have tracks on my iPod that are not in my music library, and I don't want to overwrite them.

Based on what I've read, it seems like gtkpod is best suited for this task. But I cannot find a sync button anywhere! I'm so confused. I've loaded my iPod, I've loaded my local music, but it seems like when I right-click on something, I can "Copy tracks to filesystem," but not SYNC them, so that duplicates are auto-skipped. (When I do "copy tracks to filesystem," it lets me "check for existing files when copying from ipod," but I don't understand all the naming options, and I got a million errors [from non-mp3 files, perhaps?] when I tried this.)

I'm just confused. Can someone explain to me the simplest way to do this? Thank you!

PS I'm on Feisty, and I have gtkpod version .99.8. Please let me know if you need more info.

---

### Post by skipb on 2007-10-09
If your looking for good sync functionality I would recommend Exaile or amaroK. Both work wonderfully with the ipod. I'm unable to find a sync function in gtkpod, if anyone else knows how to get this to work I welcome suggestions.

---

### Post by tgalati4 on 2007-10-09
In gtkpod, click on the read device button on the top left side.  This will read the iPod's database and give you a listing of playlists and all tracks on the iPod.  

Use your mouse to drag those files into the main library of gtkpod.  Be sure to select "Copy files to Library" in preferences.

Sync is normally reserved for updating stuff that you drag from the main library to the iPod.  Not the other way around.

If you are paranoid:

In a terminal, with the iPod mounted:

>sudo cp /media/ipod /home/fedira/ipod_backup

Then import the ipod_backup directory into Banshee.  It will give you error messages for duplicate files, but won't copy them over.  Be sure to use Banshee 0.13.1 as it has a lot more iPod functionality over the older repository version (0.10.9).

---

### Post by Incense on 2007-10-09
I believe that Amarok will check for dups when you load music on. Best music app on Linux IMO.

---

### Post by fedira on 2007-10-09
> In a terminal, with the iPod mounted:

>sudo cp /media/ipod /home/fedira/ipod_backup

Then import the ipod_backup directory into Banshee. It will give you error messages for duplicate files, but won't copy them over. Be sure to use Banshee 0.13.1 as it has a lot more iPod functionality over the older repository version (0.10.9).

Ah, thank you. This sounds like what I'm looking for. I'll have to try this when I get home. Can I update my current copy of Banshee, or do I have to uninstall & re-download?

> In gtkpod, click on the read device button on the top left side. This will read the iPod's database and give you a listing of playlists and all tracks on the iPod.

Perhaps unrelated, but one thing I remember -- in gtkpod, I don't have a "read device" button, just a "load ipod" button. Same thing?

Thanks all for the help!

---

