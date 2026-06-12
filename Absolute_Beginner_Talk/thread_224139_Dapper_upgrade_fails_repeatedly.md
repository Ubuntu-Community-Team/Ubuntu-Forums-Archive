---
title: "Dapper upgrade fails repeatedly"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by johnbl on 2006-07-27
Attempting online upgrade from Breezy.
Heaps of files download then this error appears ;


Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz) Sub-process gzip returned an error code (1)

Explanation shows as being a possible network error and to try again.. Have for days!

Same error every time.

I do have the CD however that only appears to have a clean install ability not an upgrade option.

Lost!
Any ideas most appreciated.

Johnbl

---

### Post by easyease on 2006-07-27
honest mate my best policy is keep a seperate home partition and do a fresh install when a new upgrade comes out, thats from two years ubuntu experience.that way you dont lose your music and vids etc.
 theres something nice about having a fresh from cd instilation but still having your personel files tucked away elsewhere.

---

### Post by avtolle on 2006-07-27
On upgrade from CD, you need the Alternate Install iso to upgrade without a clean install. The error message you posted causes me to think your sources list may have an issue somehow. I did a dist upgrade myself back in June without any issues. I am not where I can get a good sources list to post that you could use, perhaps someone else reading this thread could post the same.

---

### Post by easyease on 2006-07-27
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

 this is a good place to get a decent source list for your personal location and preferences......

---

### Post by johnbl on 2006-07-29
> **avtolle said:**
> On upgrade from CD, you need the Alternate Install iso to upgrade without a clean install. The error message you posted causes me to think your sources list may have an issue somehow. I did a dist upgrade myself back in June without any issues. I am not where I can get a good sources list to post that you could use, perhaps someone else reading this thread could post the same.

Thanks for that suggestion, annd the others. Problem inded must have been the source list.
I followed some other suggestions comments on upgrade as well and;
* Turned off screen saver
* replaced the contents of source list with the online list form
[http://www.ubuntuforums.org/showpost.php?p=1090438](http://www.ubuntuforums.org/showpost.php?p=1090438)

then ran Upgrade Manager again - worked a treat!

However, if I could make an observation for any of the dist managers this seems way too difficult for dumbos as I!
Might a automated process that;
* backs up and replaces the dist list
* turns off screen saver
* Offers a list of all the keep or replace options on one screen so upgrade can simply proceed OR a answer in ' n' seconds or minutes or default answer is " yes " sort of approach be applied
* Asks if a CD is available and uses that as source for required files rather than downloading serveral thousand!

Ubuntu is great and the whole open source ethos is something I can only applaud and spread the word on. I'll work at the skills but dont expect me to start contributing code any time soon! However there are legions who have even less idea than I and zip tenacity or patience when it comes to things computer. ANYTHING that can assist them in moving to open source is surely worth it. Oh and one more nail in the MS bank coffin!

---

