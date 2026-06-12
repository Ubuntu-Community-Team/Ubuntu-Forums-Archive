---
title: "gtkpod frustration."
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-02
One of my main motivations for installing Linux was because my old, '98 machine wouldn't run iTunes (it needs 2k or higher).  No problem...I've got gtkpod instead.

So...I've opened it, added some files and clicked 'synchronize'.  First I get a message 'Ok to add directories?' (and a list of directories, under iPod_control).  So I OK it....but then I get 'Warning! iTunes database must be present!'

So...where am I going wrong?

---

### Post by Kethinov on 2006-01-03
Try downloading YamiPod and managing your iPod with that instead: [http://www.yamipod.com/main/modules/home/](http://www.yamipod.com/main/modules/home/)

---

### Post by Edward The Bonobo on 2006-01-03
Good suggestion.  Thanks.  It certainly looks good from the site.

I'm having problems getting it at the moment, but I'll report back.

---

### Post by purdy hate machine on 2006-01-03
Unfortunately you need to set up your ipods directory structure using Itunes on a Windows machine before it can be used under Gtkpod. I asked a friend who uses windows to do this for me with my ipod shuffle and everything worked fine after that.

---

### Post by Kethinov on 2006-01-03
[QUOTE=purdy hate machine]Unfortunately you need to set up your ipods directory structure using Itunes on a Windows machine before it can be used under Gtkpod. I asked a friend who uses windows to do this for me with my ipod shuffle and everything worked fine after that.[/QUOTE]

This isn't so.

It's certainly easier to start from Windows, but gtkpod does have the ability to create the directory structure. You just have to mess around with formatting the ipod as vfat yourself, which is pretty annoying.

---

### Post by livewyer on 2006-01-04
Here's a new test case for iPods and Ubuntu.  

I have an iPod Nano that was originally setup using iTunes on XP SP2.  I have since come home to my Breezy Badger.  I first installed gtkpod using apt-get and everything went fine.  

After I deleted some music and added new music, I got messages about how gtkpod couldn't open/create a folder in ./iPod_Control/Music.  I played with it a bit and was able to seemingly add the music I wanted on the iPod.  I closed gtkpod and right-clicked to unmount the iPod.  I got an error message that the disk could not be ejected.  When I removed the iPod, everything I had deleted was still there and no new music to be found.  

Since I found this thread, I installed YamiPod.  It thinks my iPod is full no matter how much music I delete from it.  However, it did let me load one mp3 on it.  There should be at least a gig free on my iPod, but YamiPod thinks there's less than 5 MB.  

Any suggestions?

Livewyer

---

