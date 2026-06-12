---
title: "oh crap .. yamipod has screwed my ipod !"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2008-04-11
up until this point, yamipod has worked fine on my ipod, which is a third generation 20gb ipod with a click wheel.

was uploading some songs and everything was fine.

moved around some songs in a playlist, everything was fine.

tried to delete a song, and got an error that said something like "another program has accessed your ipod" - can't remember exactly.  Yamipod then crashed.

Fired it up again, and i got another error - it says "error: iTunes Length (song mhsd)"

but now, my ipod can't see any music !!

it's all there - the "about" option shows 18.5gb used and if i look at the folders, the music does actually exist on the ipod, it's just like yamipod has trashed the playlists.

i've tried a soft reset but that doesn't work - i'm reluctant to do anything more if there's a simple fix - any suggestions ?? cheers !


*EDIT

I've fixed it - sort of - i copied the itunesdb from the yamipod folder on the ipod to the itunes folder and it's all back but it's lost all my updates from earlier ..

---

### Post by jw5801 on 2008-04-11
I believe there's an option somewhere in yamipod to "rebuild iTunes database" that's what you need to do.

---

### Post by jasonwatkins on 2008-04-11
can't even get into yamipod now .. get the infamous "error mhlt" which i believe is a corrupted database

tried deleting the yamipod folder on the ipod but fat lot of good that did ..

*EDIT

basically nothing works ..

installed floola and hipo and all give an error ..

i really don't want to re-format if i have to but unless anyone has any bright ideas, i may have to

---

### Post by Jon Monreal on 2008-04-11
> **jasonwatkins said:**
> can't even get into yamipod now .. get the infamous "error mhlt" which i believe is a corrupted database

tried deleting the yamipod folder on the ipod but fat lot of good that did ..

*EDIT

basically nothing works ..

installed floola and hipo and all give an error ..

i really don't want to re-format if i have to but unless anyone has any bright ideas, i may have to
Doing what jw5801 said may delete all of your songs.

However, it is possible that your song database is corrupted and this may be the only option.

You could perform a restore on a computer running Windows or OS X using iTunes or by trying to find Linux-compatible software that can do it.

The best of luck to you, and I hope everything turns out alright. Make sure to explore all of your options before doing anything that might damage your iPod in any case.

---

### Post by jasonwatkins on 2008-04-11
well i ran amarok which seemed to mount the ipod ok and at least bring up the old playlists.

then i decided to try floola again and had a bit of an epiphany because i remembered it was floola - not yamipod - that i'd used on my first tour of duty on linux last year.

anyway, floola ran and mounted my ipod correctly (as an ipod shuffle ....) and i'm currently running a repair ipod option to try and rebuild the data.

bottom line is, i still have all my music stored on my PC, so if the worst comes to the worst, i can easily reformat and re-install.

i will, however, lose 6 weeks worth of podcasts to a radio show that i haven't actually listened to yet and i'm not sure i can re-download them.

i hate being awake at 4:07am :)

---

### Post by jasonwatkins on 2008-04-11
not sure .. floola has rebuilt the database but it's still tempremental

if i try and import another playlist it crashes, and there are plenty of unknown recovered files

i've managed to pull off the podcasts, so i'm just really looking for a way to restore it now, and i'll just re-up all my music

---

### Post by jasonwatkins on 2008-04-12
this is getting ridiculous now - been trying to work with the ipod without restoring but floola and yamipod now won't recognise it at all.

i un-installed amarok by mistake because i wanted to install gtkpod, with the libgkpod1 dependecy, but now i can't install amarok because that uses libgkpod2 and libgkpod1 won't un-install.

if that made sense .. doing my bloody head in ..

---

### Post by BandD on 2008-04-12
The only (easy) way to reformat an Ipod is with itunes.  So if you want to get the original Apple firmware working again, you'll have to boot into Windows or OS X.

To remove libgkpod1 you'll have to uninstall gtkpod as well.  Synaptic doesn't like you to uninstall things that other programs depend on.  So try that and see if you can unistall libgtkpod1. 

Alternatively you can install Rockbox on your ipod.  I use it on my 2nd gen mini.  It's awesome!!!!  You can find details here:  [http://www.rockbox.org/]("http://www.rockbox.org/")

It doesn't change the Apple firmware at all, rather it offers a 'dual boot' feature.  And you don't need the ridiculous itunes database structure either.  You can add files in a standard file structure.  It should find all the music you have on your ipod (that you can't access through the Apple firmware) just fine.  

It's easy to install (and uninstall).  Might be worth a shot.

One thing to consider though, because I can't quite tell from your posts.  Your ipod will MOUNT, correct?

---

### Post by jasonwatkins on 2008-04-12
the ipod actually does mount .. but the itunes database is completely f'ed because when i disconnect it, it doesn't show up any songs at all.

if i use floola to rebuild it, it shows up everything on it fine - i even managed to pull off all the podcasts i wanted to save.

i'm totally focused on reformatting the ipod now - even if it means setting up a dual-boot from scratch.

after i've sorted that i think i'm going to re-format the whole PC ..

i can't uninstall gtkpod either - whenever i try and do anything like that i get this error
```

You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  amarok: Depends: libgpod2 but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
```

if i try apt-get -f install, get the same error - same with autoremove and any combination of amarok, gtkpod, libgpod1 or 2.

---

### Post by jasonwatkins on 2008-04-12
ok so normal service is (sort of) resumed.

i partitioned off my hard drive, but ballsed up editing menu.lst in the grub folder and the operating system list wouldn't load - thank god for supergrub :D

itunes refused to restore the ipod due to the legendary 1418 error, so i manually reformatted it through windows explorer.

it formatted ok and seems to have been restored to factory settings, but when i fired up itunes again i select "restore" to just make absolutely certain and got the "1418" error again.

i booted over to linux and uploaded all my stuff ok with no issues though, but i'm still slightly concerned the 1418 error is still sort of there.

i'm going to try another trick tomorrow about the itunes restore, but if that doesn't work then i'll just have to stick with what i've got and hope for the best.

---

### Post by jasonwatkins on 2008-04-13
ok normal service does appear to be back properly.

i tried the old restore-pull-the-cable-out-first-and-plug-it-straight-back-in trick and it did properly restore the ipod to factory settings.

i put all my stuff back on it, created my playlists and everything and while i was doing some random editing of song title, floola decided to hang :D

i had no choice but to reboot and prayed that the database had been written to the ipod and thankfully it had.  i'm listening to it now as I type and it really does appear to be absolutely fine, so i can only keep my fingers crossed.

---

### Post by BandD on 2008-04-13
Glad things seem to be working.  I find ipods to be exteremly difficult to work with when something goes wrong with the Apple firmware or itunes database.  

But I would recommend trying out Rockbox.  If you wanted, you could jsut drop your Music folder onto your ipod like a mass storage device and Rockbox would handle it in basically the same way as any music player.  It's pretty convient.  But it's not for everyone.  Just thought I'd give it one last plug ;)

Hopefully things continue to work for you and things don't get corrupted again.

---

### Post by jw5801 on 2008-04-13
I think he has a shuffle so Rockbox may not even be an option.

---

### Post by BandD on 2008-04-13
From the very first post:

> up until this point, yamipod has worked fine on my ipod, which is a third generation 20gb ipod with a click wheel.

It's a 3rd Gen so rockbox will work.  

> anyway, floola ran and mounted my ipod correctly (as an ipod shuffle ....) and i'm currently running a repair ipod option to try and rebuild the data.

floola was identifying his ipod as a shuffle, though.

---

### Post by jw5801 on 2008-04-13
Ah, sorry. My bad.

Use [Rockbox](http://www.rockbox.org/) it's excellent!

---

