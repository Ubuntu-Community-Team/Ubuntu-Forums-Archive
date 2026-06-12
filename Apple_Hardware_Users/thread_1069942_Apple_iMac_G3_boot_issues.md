---
title: "Apple iMac G3 boot issues"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by kc8cpw on 2009-02-14
ok... i'm about to go bald from pulling my hair out... here's the situation...

I have a Applie iMac G3 333MHz/256MB RAM/80GB HD/24x CD-ROM...

I have tried to install the following versions of linux:

Ubuntu 6.10, and 8.10  (I did use the alternate cd for 6.10, but not 8.10)

Slackintosh 12.1

Debian 4.0_r7 I did this as a network install over the internet...

After installing with now problems, I'm told to take the cd out and reboot... I do that... then it says

Please wait, Loading Linux Kernel....:confused:

and it just stops and sits there...:(:(:(

This is my first time to ever mess with a mac and I'm clueless as to what I need to do... Any ideas or suggestions?

Thanks in advanced...

Jonathan

---

### Post by DonaldJ on 2009-02-16
Me too...  But I can't even get the G3 to register the image CD yet...
I boot with the CD in, and hold down four keys: Control/Option/p/r, but it always reboots into OS-10..?  I wonder if you're supposed to format first..?
Or Slam it on the top with a sledge hammer a couple times to wake it up..?
As you can see I know how you feel...

What did you do to get it to even start with the CD..?

---

### Post by DonaldJ on 2009-02-16
iMac-G3, 40-gig, 256 RAM...
I read that Xubuntu works on low RAM.. and that Ubuntu needs 500-megs...  But Xubuntu will try to update itself to Ubuntu 804, and might become unstable in an iMac...

Try:  [http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)    Go to "Alternate CD Install"...

Tip: Me thinks you shouldn't let the install update itself to the next level, or it will lock-up your boot, and you will need to reformat and install OS-10 from scratch to get it to install Ubuntu again, given the clock factor...

I stumbled upon this data in one of the other threads... 
I tried several times, and failed, so I tried changes till it worked...

Tip: Eject CD's by rebooting while holding down the mouse...

Tip: You must have an OS on the hd to be able to set the correct time, or you get stopped right at the beginning...

1. Slip in the CD, boot the iMac...
2. Hold down the "C" key until black-screen appears...
3. Hit Return...
4. After the Xubuntu screen, load all the drivers, and the screen goes black, wait about a minute, and press CTRL, ALT, F1
5. Keep doing that until you get an ubuntu prompt...
6. type:   sudo pico /etc/X11/xorg.conf
7. scroll down and look for "dri", place a # at the beginning of that line, so it reads   #Load "dri"
8. scroll down and look for "glx", place a # at the beginning of that line, so it reads   #Load "glx" 
9. Scroll down and look for Identifier "Generic Monitor".. Change the "HorizSync" values to 58-62
10.Scroll down and look for Identifier "Generic Monitor"..  Change the "VeriRefresh" values to 75-117
11. Hit Ctrl-key with the 0-key.. then press return...
12. Hit Ctrl-key with x-key.. this got me the Ubuntu prompt...
13. type:   sudo killall -HUP gdm    
and wait.. In about 10-20 seconds you get a screen with a mouse running in a wheel, then a desktop-screen...  
Hit the Install button, and follow the instructions...
When you get to the final Install button in a window, it might not work with a mouse-click..  Hit Return...

That's how I got this antique iMac to install Xubuntu...

I found the data in this forum's Apple threads.. and pieced together bits of different threads till it finally worked...

_____________________________________________________

Go to Applications>Update Manager, and do the updates.. about 180 of them.. Takes about half an hour...  Reboot...

Do a little dance...  Sing a little song...



Caution on doing the second barrage of updates...  It might update to U-804, and Slam you right-back to square-one... And there aren't any cuss-words strong enough to deal with that mess...  Although, "flinging the Mac through the window", is a comforting option...

______________________________________________________


Just a little off the wall Linux-humor:  Maybe the boot wouldn't mess up so bad if you din't run step 13 as: "sudo killall -HUP gdm.. but changed it to:  "sudo killjustalittlebit -HUP gdm"...  but don't try it at home...

---

### Post by DonaldJ on 2009-02-17
Thing Ubuntu thing just doesn't quit.. Now the iMac is updating itself to Ubuntu 8.04 LTS.. which it seems also runs on low RAM...  And then it's probably gonna update itself to 8.10 LTS... It sure is a pleasure getting "Apple OS 10 crap" out of the Mac...  Maybe I'll be able to use this sad little computer again..?

I like this Ubuntu thing...  I have in my head 300 new technologies, the first one being plazma-engines for floating/flying cars...  If and when I gets funded, and building new technologies in a small lab, and start marketing new 1200 mph flying-cars, I will inject a couple $hundred-mil into this project, to all those who have made it work...  

Maybe for the iMac you should just get the 8.04 LTS image CD, in the first place..?  The info says it works on 256 megs of RAM...  Only five minutes more downloading into the Mac..  I almost can't wait to see what the new desktop's gonna be...  It's downloading 997 new files...

Yikes!..  It says it's gonna take an hour and twenty minutes to install...  I've got time to feed the wild rabbit, living in the woodpile, its breakfast of four peeled sweet baby carrots, and slice of fresh apple...

Ohh Lovely!.. the update locked up the boot.. so now it's back to square one...   "poop & darn"..  More time to feed the rabbit...

---

### Post by DonaldJ on 2009-02-18
The rabbit hasn't been around for a  very long time..  and it's carrots are still in its dish by the woodpile..  I wonders if some hungry humon caught her and ate her..?  hope not!..


The iMac-G3 started this Image CD install right off..

[http://cdimage.ubuntu.com/ports/rele...repid/release/](http://cdimage.ubuntu.com/ports/rele...repid/release/) Go to "Alternate CD Install"...

It started on it's own, with just a few hits to return button.. but now it wants drivers installed by floppy.. Oyie!.. I don't have the ext-floppy installed... I think it's somewhere in one of them boxes of computer junk.. someplace, where ever they might be..? 

Where do I get downloads of iMac-G3 hardware drivers..?  I checked the Net.. It's back to  being scammed and slammed by those driver's websites..  I don't like this.. it reminds me of trying to get Windows drivers, and always giving up after a couple hours fruitless searching...

This Ubuntu-810 Mac-install wants floppy installed CD-ROM Drivers before it can continue the install...

Why can't the install find the drivers that are already in the OS-10..?

Is there a sudo command to make the Ubuntu-install see the OS-10 drivers already on the hd..?  (umm?  "sudo ~/CDR/D's.Go_get'em Baby!".. I Wish!.)

This is gonna be a process and some.. Step one: Get suited-up, warm the car up, and drive a mile to the shed, push my way in, and hope I can find the right box with the iMac's floppy unit...   

"I be back!"

---

### Post by DonaldJ on 2009-02-18
Try this...

[http://ubuntuforums.org/showthread.php?t=964904&highlight=G3+drivers](http://ubuntuforums.org/showthread.php?t=964904&highlight=G3+drivers)

______________________________________________________________________________


Ubuntu installed in the iMac.. It took about an hour, maybe longer... When it came time to remove the CD and reboot, it started to boot, the chimes happened, then two command windows came up, then the computer just shut down... not fun!..

Me thinks I'm just gonna give-up on it for tonight.. It's been a Stretch.. And there's always the final last-ditch option of shooting the iMac with the 9-mil...

---

### Post by chort27 on 2009-02-19
I had a smiliar problem - 
when it got to the loading please wait screen the words would dissapear then it would just hang there for a while . I fixed it like htis:
When it got to the yaboot screen, i typed:
Linux video=ofonly
Worked like a charm.

---

### Post by DonaldJ on 2009-02-19
I tried "Linux video=ofonly" at the yboot... 

I get to a non-screen login...  At the top reads:

Loading, please wait...

Screen init failed
19+0 records in
19+0 records out
kinit: name_to_dev.....
kinit: trying to resume.....
kinit: No resume image, doing normal boot

I log in, and now it's at the command prompt, waiting for something that I don't know what to do..?

I think maybe boot and screen aren't fully installed yet..?  They probably need a few keys set..?

Now it reads: "See "nan sudo_root" for details"...

I keyed that + return..  I get "command not found"...  It's at  :~$ _

______________________________________________________________________


I did get an Ubuntu Desktop immediately after the install, then I clicked to do the 240-updates...  
It checked, but at the Install Window "Check" and "Install" seemed both to be "check".. 
If I clicked "Check" it checked...  If I clicked "Install" it checked... 
I couldn't get the updates to download, which probably means it can't find a path to download to..? 
Or it means the the path to download to, is set at zero..?  
I rebooted, and now it won't boot to a desktop..?  I can't shut down, except by pulling the power cord..?  

I had left the iMac On, at the command prompt, for about 5-minutes...  The screen just went blank..  Reboot button works to reboot, but I only ever get to a command prompt...

---

