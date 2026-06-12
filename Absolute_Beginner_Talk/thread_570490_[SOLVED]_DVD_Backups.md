---
title: "[SOLVED] DVD Backups"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by clancymf on 2007-10-08
I have almost successfully matched everything that I was able to do in windows through ubuntu.  One of the few remaining items is backing up dvds.

I used to use anydvd and then clonedvd, which work great in combination.

Since switching to ubuntu, i have tried k9copy, acidvd, and a few others but i cannot figure out a way to limit (shrink) the size down to a normal dvd (4.7 gigs).  There has to be an easy way.

Any ideas.

Thanks!

---

### Post by qpieus on 2007-10-08
I have not played with any of the linux dvd tools you mention, so I can't help you there, but I do know that dvdshrink and dvd decrypter work well using WINE. This guide is a little old, so I'm not sure it's the same setup for newer versions of ubuntu, but I know it works for dapper:

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

If you don't mind running these under WINE, then this may work well for you.

---

### Post by hyper_ch on 2007-10-08
I also use DVDShrink and DVD Decrypter :)

---

### Post by Drakkor on 2007-10-08
I think it's default in k9copy, but to check, go to Settings>Configure k9copy>DVD,
and it should read 4400mb for the DVD size. :)

---

### Post by clancymf on 2007-10-08
Thanks for all the feedback. 

I'll have to check the settings again but for some reason I think the one I tried to back up came to 7.7 gigs.  If i cant get k9 to work I'll try dvd decrypt and shrink.  

This forum is the most helpful on the web (IMHO).

:)

---

### Post by indytim on 2007-10-08
Use K9Copy but save the output as an iso file vs trying to do the direct burn through k3b.  It works.

IndyTim

---

### Post by clancymf on 2007-10-09
Well I am still having problems. I check my settings in k9copy and it is set to 4400 but the .iso that it burned was 7.4gigs and is too big to put on a DVD.  Could it be that it is reading that my burner is dual layered?

I tried using GnomeBaker and the same problem.  

Any ideas.  

Thanks.

---

### Post by wild77 on 2007-10-09
I have been able to get the following DVD programs running with Wine 0.9.30 on Ubuntu 6.10 

Ripit4Me
DVD Decrypter
DVD Shrink
ImgBurn
VOBBlanker
DVD Rebuilder

Here is a guide I put together on another site.
[http://forum.doom9.org/showthread.php?p=948220#post948220](http://forum.doom9.org/showthread.php?p=948220#post948220)

---

### Post by Drakkor on 2007-10-09
I don't think so Clancy, because my burner is also dual layer, but k9 should shrink it as ordered ! I still use the cheaper 4.7 disks , and no problems here. I just made an .iso of a DVD yesterday, and it worked fine.

---

### Post by clancymf on 2007-10-09
With everything I have read k9copy should work.

Here is what was downloaded into my tmp dir:

clancymf@clancypc:/tmp/kde-clancymf/k9copy/dvd$ ls -al
total 16
drwxr-xr-x 4 clancymf clancymf 4096 2007-10-09 18:10 .
drwx------ 3 clancymf clancymf 4096 2007-10-09 18:10 ..
drwxr-xr-x 2 clancymf clancymf 4096 2007-10-09 18:10 AUDIO_TS
drwxr-xr-x 2 clancymf clancymf 4096 2007-10-09 18:32 VIDEO_TS
clancymf@clancypc:/tmp/kde-clancymf/k9copy/dvd$ 

Attached is my settings and the .iso that was created

Any ideas what could be wrong?  Thanks.

---

### Post by Incense on 2007-10-09
Check here ([http://www.dvd-guides.com/content/view/213/59/]("http://www.dvd-guides.com/content/view/213/59/") )and see if this helps. I just hit open, Select the tracks, Copy, name the ISO and it works. Don't have to set up anything.

---

### Post by Eck on 2007-10-11
Wild77,

You know, I've used the RipIt4Me way in Wine mostly since I feel I end up with a better quality result with DVDShrink than with K9Copy (although that also works for me).

But Wine as been tricky with regressions lately regarding breaking RipIt4Me's ability to create a PSL file.  With 0.9.44 things were fine, but not the few preceding Wine's and none since.

I found it has nothing to do with the distro or setup of the drives in winecfg, well, as long as that's done correctly.

I get on 0.9.46 the failed to create a psl file and there doesn't seem to be a DVD in your selected drive.  So I set RipIt4ME.ini to autocreatepsl "0" so DVDDecrypter can just rip all the files (I need to edit-Select All) when it opens and RipIt4Me will then continue after the rip to blank the areas and do its built in FixVTS process.  I then start DVDShrink from RipIt4ME and all is fine.

This works on all the old DVDs that could be ripped by DVDDecrypter anyway, plus adds the extra after the rip features to clean up the rip.  I use the DVDShrink full analysis as well for a beautiful end product that I then use K3B to create a new DVD Video Project with and that's fine.

However without the psl file there will be DVDs that will not work.  It's been reported in the winehq,org ap database for the latest versions and there is a link to a bug report there as well.  Unfortunately the Wine developers want the user to prove the regression and I fear he may not have the skills to follow the directions they gave him in the bug report.  (Not sure if I do either.) So they may never admit to the regression and it will be dumb luck if they release a version of Wine where this works again.

Maybe you have some idea what we could change in the wine regedit that could overcome this problem?  The drives are being detected fine, RipIt4Me is ripping the temporary IFO's fine, yet is not able to then create a psl file and so the work around of the autocreate PSL set to 0 is needed to get the after the rip functions to happen.  But obviously this is not ideal.

Well, using OpenSUSE 10.3 at the moment, the Wine version on the DVD and oss repo is the last version I had working on Debian Lenny, 0.9.44.  When I upgraded that on Debian to a later version it also broke this feature so it is not distro related.  It also was broken before 0.9.44.  On OpenSUSE I installed Wine from the latest on the Build Service which is 0.9.46 (the latest).  That's why this is broken again!

Do you (or anyone) have an idea of what we might be able to adjust?

---

### Post by Eck on 2007-10-13
Ah!  I figured out what can be used to work around the problem.  I took your hint about your copying the IFOs over and examined the RipIt4Me files in the Windows\Application Data folder and the RipIt4Me Debug file.

It appears that the part that errors out is when RipIt4Me is supposed to create the OriginalIFOs folder within the target directory for the rip.  The Debug file reported an =0 for that task, and then didn't have much luck copying over the IFOs from the TempISOs folder into that OriginalIFOs folder as the folder didn't exist to have anything copied into it.

As I mentioned, I have made a change to the AutoCreatePSL entry in RipIt4Me.ini, changing the value to 0.  This affords me the opportunity to carry that operation using DVDDecrypter's menu of Import psl if that psl would exist.  As things have been going, it hasn't been created because RipIt4Me doesn't have any IFOs in an OriginalIFOs folder to work with.  Edit - We don't need to change that anymore as with RipIt4Me successfully creating the PSL file it also can now automatically import it into DVDDecrypter when it opens it.

So what I did with my last successful rip was to carry out the RipIt4Me wizard operations until the step where I'd need to click the Create PSL file button.

I then created an OriginalIFOs folder within the VIDEO_TS folder created by RipIt4Me during its initial phase, and then copied everything in the Window\Temp\TempIFOs folder with the exception of the TempIFOs file with that "Welcome to RipIt4Me" written in it to my newly created OriginalISOs folder.  I also needed to create a FinalIFOs folder and place it into the target folder for the rip as well.  Having both folders there and the files from TempIFOs copied to OriginalIFOs folder enabled RipIt4Me to successfully create the psl file.

Then I clicked the Create PSL button and amazingly the DVD started up again and RipIt4Me went ahead and successfully created the RipIt4Me.psl file.

Then after clicking Rip With DVD Decrypter, I used the menu to import the PSL file (had to browse to the VIDEO_TS folder) and DVDDecrypter successfully imported the file. Edit - No longer need to do that as we can leave RipIt4Me.ini set at the default value of "1" for AutoLoadPSL.   I then proceeded to do the rest of the rip and DVDShrink and burn with K3B operations.

I wish I could figure out why RipIt4Me can do this on its own, as designed, with some versions of Wine but not others.  But at least I have got the whole process available now.

---

### Post by ayenack on 2007-10-14
If you're ripping Films there's a great app called [XDVDSHrink]("http://dvdshrink.sourceforge.net/") that I use does the job well and is written for GNU/Linux you don't need wine in other words.

Good luck. ayenack.

---

### Post by clancymf on 2007-10-16
Thanks for everyones help.

I managed to get k9copy to work.  I dont really know how i got it fixed by i reinstalled the application and installed k3b and all the dependencies.  And magically it seems to work.

Thanks again. :)

Mick

---

### Post by wild77 on 2007-10-19
> Wild77,

You know, I've used the RipIt4Me way in Wine mostly since I feel I end up with a better quality result with DVDShrink than with K9Copy (although that also works for me).

But Wine as been tricky with regressions lately regarding breaking RipIt4Me's ability to create a PSL file. With 0.9.44 things were fine, but not the few preceding Wine's and none since.


That is why I am still using edgy and Wine 0.9.30 it has been rock solid for what I want. I plan to upgrade to Gutsy and PCLinux  soon and begin testing, Feisty was too buggy on my system.

There is also news at Doom9 that the latest DVDFab will run on Wine unless you have a Plextor drive like me.

[http://forum.doom9.org/showpost.php?p=1056458&postcount=187](http://forum.doom9.org/showpost.php?p=1056458&postcount=187)

---

### Post by ejs7597 on 2007-10-19
I can also confirm that DVDFAB will work with Wine in Gutsy.  I just downloaded and installed the trial version.  I am using an old Toshiba DVD-R 2X drive. It burns around 2x most of the time in Ubuntu, but under Wine with DVDFAB, it is only burning at 0.2x or 0.22 MB/s.   Does anyone know of any tricks in Wine to get the drive to work better?  I might try a faster drive from my other computer, to see how it performs also.

Update:  I changed the version of Windows that Wine was emulating to XP, and the burner speed is back to normal.

---

