---
title: "Burning ISOs to DVD"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-01-30
I just installed a new DVD R/W drive into my tower.  I have been able to successfully create ISOs from a DVD source, and play the ISO straight from my hard drive.  I have not, however, been able to burn ISOs image to DVD.  When I drag the ISO into the DVD icon and then attempt to write to disc, I am presented with the option to either "Create from Image" or "Create With File."  When I create With File, it produces an unplayable DVD.  When I choose Create from Image, it simply does nothing (it acts as if I selected Cancel).  Any help?  Thanks!

---

### Post by bigken on 2007-01-30
all you need to do is right click the iso and select write to disc

---

### Post by zgornel on 2007-01-30
Install Gnomebaker or K3B. In both of them , in the "Tools" menu you 'll find Burn DVD iso image. :)

---

### Post by wickstopher on 2007-01-30
Unfortunately, both those solutions produce the same results as before: an unplayable DVD on both my computer and other DVD players.  It plays, but I just get a scrambled screen.

---

### Post by bigken on 2007-01-30
could be a bad iso file ?

---

### Post by carverj on 2007-01-30
What are you trying to burn? 
It's just that ISO's are bootable files. 
Do you mean that there is a scrambled boot screen when you boot from DVD?
Forgive my ignorance if not !!

---

### Post by helliewm on 2007-01-30
Gnome Baker is better than Brasero. I had problems burning an ISO DVD with Brasero. Add/Remove programes will give you Gnome Baker.

Helen

---

### Post by jkeyes0 on 2007-01-30
> **carverj said:**
> What are you trying to burn? 
It's just that ISO's are bootable files. 
Do you mean that there is a scrambled boot screen when you boot from DVD?
Forgive my ignorance if not !!

btw, ISO files aren't necessarily bootable files. They are images of CD's or DVD's.

Also, in regards to wicks' problem: have you placed the DVD back in your computer and tried browsing the files on the disc? There should be an audio_ts and a video_ts folder, with many .vob, .ifo, etc. files in the video_ts folder. There's every possibility whatever burning software you've got burned a copy of the .iso file to the disc rather than extracting the contents of the .iso file.

---

### Post by wickstopher on 2007-01-30
Here is what I am trying to do: burn a copy of a playable movie DVD that is playable in a normal DVD player.  

The ISO image of the original DVD plays just fine in totem.  Not noticeable problems upon skimming the contents.

When I try to burn it as an ISO image disc, I am getting the folders audio_ts and image_ts on the disc.  The burned disc is the same size as the original ISO file.  But consistently, in 5 attempts with the same ISO image, I get the same results.  In my Phillips DVD player, I just get a scrambled screen, and when I try to play it on my computer DVD drive, it starts out okay with the warning screen and a few seconds of intro CG-stuff, but after about 5 seconds it goes to a scrambled screen.  The audio_ts folder is empty.  And the video_ts folder contains 14 items, totalling the total size of the DVD (which matches the size of the ISO image).  Even browsing the directory, you can see that the .vob files are scrambled from the preview.  


[IMG]http://www.christopherwicks.com/bucket/dvdprob.png[/IMG]


I'm at a complete loss, having tried everything that has thus far been suggested.

---

### Post by bigken on 2007-01-30
could be bad media or could it be something to do with copy protection ?

---

### Post by jkeyes0 on 2007-01-30
did you use any sort of decss tool to unencrypt the DVD data? I've done my fair share of dvd backups, but I've never tried it through an ISO.

---

### Post by zerhacke on 2007-01-30
You're trying to copy a copywrited DVD with copy protections on it.  You'll have to rerip the DVD this time breaking the encryption before or during the rip.

I know how to do this with Windows, but have never found a way with Linux.

---

### Post by klytu on 2007-01-30
> **zerhacke said:**
> You're trying to copy a copywrited DVD with copy protections on it.  You'll have to rerip the DVD this time breaking the encryption before or during the rip.

I know how to do this with Windows, but have never found a way with Linux.

I haven't done this with Linux either, but my brother-in-law who often rips and burns DVDs with Linux claims that libdvdcss automatically decrypts the copy protection when you rip the DVD.  If the original poster has libdvdread and libdvdcss installed, which should be the case if Totem plays the ISO on his hard drive, this probably isn't an encryption problem.

---

### Post by klytu on 2007-01-30
> **wickstopher said:**
> Here is what I am trying to do: burn a copy of a playable movie DVD that is playable in a normal DVD player.  

The ISO image of the original DVD plays just fine in totem.  Not noticeable problems upon skimming the contents.

When I try to burn it as an ISO image disc, I am getting the folders audio_ts and image_ts on the disc.  The burned disc is the same size as the original ISO file.  But consistently, in 5 attempts with the same ISO image, I get the same results.  In my Phillips DVD player, I just get a scrambled screen, and when I try to play it on my computer DVD drive, it starts out okay with the warning screen and a few seconds of intro CG-stuff, but after about 5 seconds it goes to a scrambled screen.  The audio_ts folder is empty.  And the video_ts folder contains 14 items, totalling the total size of the DVD (which matches the size of the ISO image).  Even browsing the directory, you can see that the .vob files are scrambled from the preview.  


[IMG]http://www.christopherwicks.com/bucket/dvdprob.png[/IMG]

I'm at a complete loss, having tried everything that has thus far been suggested.

Have you tried using dd to burn the ISO to a DVD?

---

### Post by %hMa@?b&lt;C on 2007-01-30
you can use k9copy to get a copy of the dvd iso image.
also i have used acidrip to get video files.

---

### Post by bruenig on 2007-01-30
xdvdshrink works or you can use dvdrip to get it to the hard drive and then make a dvd from that file. Also to burn an iso from the command line do
```
growisofs -dvd-compat -Z /dev/hd?=whatever.iso
```
hd? is the name of your dvd drive and whatever.iso is the name of the iso file. If that doesn't burn it should give you some output as to why.

---

### Post by wickstopher on 2007-01-31
growisofs generates the exact same result as everything else I've tried.  Not sure how I would use dd to do this, perhaps you could explain more?  Everything I do seems to be giving me the same results though.  Perfect .iso image, playable from my hard drive, but can't get it to burn without corruption to a dvd.  I tried to use k9copy but couldn't get it to do anything.

P.S.
Not sure what is going on now, but after installing k9copy and dvdbackup, everything seems to be screwed up.  k9copy won't let me do anything, and now I'm trying through the gnome interface to burn discs, and it tells me that I can't.  I uninstalled k9copy and rebooted.  DVDs aren't being read properly. now I'm attempting, once again, to burn an ISO image to my DVD, but for some reason it is taking 1.5 hours instead of about 10 minutes.  Losing my mind here, maybe I need to reinstall.  Or maybe my dvd drive is effed up.  Not sure.

---

### Post by kvorion on 2007-01-31
Have you tried checking the MD5sums of the files that get written to your DVD and comparing them with the original ISO?

---

### Post by wickstopher on 2007-01-31
I have not tried that.  How do I do that, and where do I go from there?

---

### Post by wickstopher on 2007-01-31
Could it be that I'm not using Dual Layer DVDs?  I thought that it didn't matter (i.e. i thought that my dvd burner was supposed to read/write all formats), but I could be wrong.  I got this message when trying to burn a dvd of files for backup:  

The following disc types are supported:
DVD+R DL

[IMG]http://www.christopherwicks.com/bucket/disctypes.png[/IMG]


i don't know much about dvd burners, but maybe it can read all types but can only burn to Dual Layer media?  Sounds strange, but like I said, I don't know much.  The drive writes audio CDs just fine.

Addendum:

Since posting this message, I have been able to burn a data DVD using gnomebaker.  I tried, once again, to get an accurate ISO image of a movie to a disc using gomebaker and it still comes up scrambled.  Blech.  Perhaps I am missing a codec somewhere?  It just doesn't make any sense that I can play the files without any problems on my computer, but can't get them to burn properly to a dvd.

---

### Post by wickstopher on 2007-02-01
I'm giving up on ISOs for the time being.  Is there any other method of extracting the information on a movie DVD and then burning a copy of it?  jkeyes0 mentioned a decss tool.  What is that?  I have both ibdvdcss2 and libdvdcss2-dev, as well as win32codecs.  Thanks for all the support so far, and my apologies for not being able to get any of it to work!  I'm trying!

---

