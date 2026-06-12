---
title: "HELP please Help...ipod dramas....:'(...."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by i_pod25 on 2007-03-13
i ran my ipod nano with gtkpod and after i resetted my ipod from the ipod menu itself it tells me that that it only has 600 or so MG left even though there is NO songs on my ipod.

so i try to link it back to gtkpod which gives me this

"iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'"

when i try to read the ipod or sync it :(


please help...im very lost :'(


thanx

---

### Post by ThrobbingBrain66 on 2007-03-13
> **i_pod25 said:**
> i ran my ipod nano with gtkpod and after i resetted my ipod from the ipod menu itself it tells me that that it only has 600 or so MG left even though there is NO songs on my ipod.

so i try to link it back to gtkpod which gives me this

"iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'"

when i try to read the ipod or sync it :(


please help...im very lost :'(


thanx

gtkpod sees your Ipod as a completely different piece of hardware because the database file it kept for your Ipod now doesn't match.
Within the .gtkpod folder in your home directory, delete all files except for the 'prefs' file.  Then restart gtkpod and plug in your Ipod. This should reset everything so you don't get that error message anymore.

---

### Post by i_pod25 on 2007-03-13
> **ThrobbingBrain66 said:**
> gtkpod sees your Ipod as a completely different piece of hardware because the database file it kept for your Ipod now doesn't match.
Within the .gtkpod folder in your home directory, delete all files except for the 'prefs' file.  Then restart gtkpod and plug in your Ipod. This should reset everything so you don't get that error message anymore.

would it work if i just reinstalled gtkpod? 

thanx

and will this also reset the memory count on my ipod?

---

### Post by chuckyp on 2007-03-13
No because purging or reinstalling won't delete .gtkpod from your home directory.  Just click on places > home and hit ctrl+h this will toggle the showing of hidden folders/files.  i.e. the ones that start with a period.  You can then navigate to the .gtkpod directory and delete the aforementioned files.

---

### Post by i_pod25 on 2007-03-13
> **chuckyp said:**
> No because purging or reinstalling won't delete .gtkpod from your home directory.  Just click on places > home and hit ctrl+h this will toggle the showing of hidden folders/files.  i.e. the ones that start with a period.  You can then navigate to the .gtkpod directory and delete the aforementioned files.

it still came up with this message when i tried to get gtkpod to read my ipod

"iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'"

---

### Post by i_pod25 on 2007-03-13
and when i tried to sync a song it came up with this :S

"You did not import the existing iTunesDB ('/media/ipod/iPod_Control/iTunes/iTunesDB'). This is most likely incorrect and will result in the loss of the existing database.

Press 'OK' if you want to proceed anyhow or 'Cancel' to skip storing. If you cancel, you can import the existing database before calling this function again."....

---

### Post by ThrobbingBrain66 on 2007-03-13
> **i_pod25 said:**
> and when i tried to sync a song it came up with this :S

"You did not import the existing iTunesDB ('/media/ipod/iPod_Control/iTunes/iTunesDB'). This is most likely incorrect and will result in the loss of the existing database.

Press 'OK' if you want to proceed anyhow or 'Cancel' to skip storing. If you cancel, you can import the existing database before calling this function again."....

Hmmm...just to be sure, why don't you completely delete the .gtkpod folder.  Then, if it's not too much of a hassble, you can completely purge gtkpod with synaptic or through the terminal:
```
sudo aptitude remove --purge gtkpod
```

I've only been using gtkpod myself since Christmas so I'm not an expert with it but just deleting the .gtkpod folder should work.  If you do decide to reinstall, make sure you remove the settings folder first.

---

### Post by i_pod25 on 2007-03-13
it still comes up with this error

"iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'"


:(:(:(:(:(

---

### Post by i_pod25 on 2007-03-14
:confused:

---

### Post by Famicommie on 2007-03-14
I personally haven't tried this out yet, but the Songbird Media Player has an extension which supposedly works with the iPod.

[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

---

### Post by ThrobbingBrain66 on 2007-03-15
> **i_pod25 said:**
> it still comes up with this error

"iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'"


:(:(:(:(:(

Sorry bud, I forgot about this thread.  Clearly now the issue is with your Ipod.  I would try mounting it, opening it up in nautilus (I believe mine mounts at /media/ipod) and deleting any files you find on.  make sure to enable hidden files to get rid of those too.

---

